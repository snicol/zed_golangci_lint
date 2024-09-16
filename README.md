# `zed_golangci_lint`

This project is a fork of [j4ng5y/zed_golangci_lint](https://github.com/j4ng5y/zed_golangci_lint)
with some fixes required to run (see issues of the upstream project). As they are not merged yet,
I decided to create a fork of all of the community fixes combined.

To install this extension, you can clone this repository and in Zed's extension panel, click
on `Install Dev Extension` and select the folder where you cloned this repository.

## Installation

This extension will attempt to install [golangci-lint-langserver](https://github.com/nametake/golangci-lint-langserver)
for you, but you will need to install [golangci-lint](https://github.com/golangci/golangci-lint) also. It's recommended
that you install and manage both of these tools using the following methods:

### MacOS

```bash
brew install golangci-lint golangci-lint-langserver
```

### Source (Linux, Windows, MacOS)

```bash
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
go install github.com/nametake/golangci-lint-langserver@latest
```

## Configuration

To change the command options run by the extension, open `~/.config/zed/settings.json` and add the
following `lsp` configuration. `"lsp"` itself is a root level object in the settings file.

```jsonc
{
  // ...
  "lsp": {
    "golangci-lint": {
      "initialization_options": {
        "command": [
          "golangci-lint",
          "run",
          "--out-format",
          "json",
          "--issues-exit-code=1",
          "--fix" // e.g. Add "--fix" if you'd like golangci-lint to attempt to fix issues.
        ]
      }
    }
  }
  // ...
}
```
