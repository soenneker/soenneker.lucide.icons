[![](https://img.shields.io/nuget/v/soenneker.lucide.icons.svg?style=for-the-badge)](https://www.nuget.org/packages/soenneker.lucide.icons/)
[![](https://img.shields.io/github/actions/workflow/status/soenneker/soenneker.lucide.icons/build-and-test.yml?style=for-the-badge)](https://github.com/soenneker/soenneker.lucide.icons/actions/workflows/build-and-test.yml)
[![](https://img.shields.io/github/actions/workflow/status/soenneker/soenneker.lucide.icons/publish-package.yml?style=for-the-badge)](https://github.com/soenneker/soenneker.lucide.icons/actions/workflows/publish-package.yml)
[![](https://img.shields.io/nuget/dt/soenneker.lucide.icons.svg?style=for-the-badge)](https://www.nuget.org/packages/soenneker.lucide.icons/)
[![](https://img.shields.io/github/actions/workflow/status/soenneker/soenneker.lucide.icons/codeql.yml?label=CodeQL&style=for-the-badge)](https://github.com/soenneker/soenneker.lucide.icons/actions/workflows/codeql.yml)

# Soenneker.Lucide.Icons

Lucide SVG files packaged as .NET content assets.

## Install

```bash
dotnet add package Soenneker.Lucide.Icons
```

Each SVG is copied beneath the application output directory using its upstream kebab-case name:

```text
Resources/Lucide/circle-check.svg
Resources/Lucide/search.svg
Resources/Lucide/user-round.svg
```

Read an asset without relying on the process working directory:

```csharp
string path = Path.Combine(
    AppContext.BaseDirectory,
    "Resources", "Lucide", "circle-check.svg");

string svg = await File.ReadAllTextAsync(path, cancellationToken);
```

The package does not automatically expose the files through ASP.NET Core static-file middleware or render them in Blazor. Copy or serve only the assets the application needs.

Do not turn an untrusted string directly into a file path; map allowed icon identifiers to known filenames. The SVG files are regenerated from upstream, so additions, removals, and filename changes can occur between package versions. `Soenneker.Lucide.Enums.Icons` provides generated identifiers when an enum is preferable to filenames.
