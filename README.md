# Example

```yml
name: Nuget Package
on:
  release:
    types: [published]
jobs:
  build:
    runs-on: ubuntu-latest
    name: Update NuGet package
    steps:
      - name: Checkout repository
        uses: actions/checkout@main

      - name: Setup .Net
        uses: actions/setup-dotnet@main

      - name: Nuget Package And Upload
        uses: csharp-opensource/publish-nuget@master
        with:
          releaseVersion: ${{ github.event.release.tag_name }}
          repoUrl: ${{ github.server_url }}/${{ github.repository }}
          nugetToken: ${{secrets.NUGET_AUTH_TOKEN}}
          nugetSource: https://api.nuget.org/v3/index.json
```
