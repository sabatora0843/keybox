# keybox

**keybox** is a lightweight CLI tool for managing secrets using the macOS Keychain.

It is implemented as a simple Bash script and relies on the built-in macOS `security` command, so it has minimal dependencies.

## Features

- Secure secret storage using the macOS Keychain
- Store a value and an optional comment for each key
- Multi-line comments supported
- Minimal dependencies (Bash + macOS `security`)
- Simple and portable Bash implementation

## Requirements

- macOS
- Bash
- `security` command (included with macOS)

## Installation

### Homebrew

```bash
brew tap sabatora0843/tap
brew install keybox
```

### Manual Installation

```bash
sudo curl -L https://raw.githubusercontent.com/sabatora0843/keybox/main/keybox \
  -o /usr/local/bin/keybox && sudo chmod +x /usr/local/bin/keybox
```

## Usage

```
keybox <subcommand> [options]
```

### Subcommands

- `add <key> <value> [comment]`
- `list`
- `get <key>`
- `update <key> <new-value> [comment]`
- `update <key> --comment <comment>`
- `delete <key>`

## Examples

### Add a secret

```bash
keybox add github_token ghp_xxx "personal access token"
```

### Get a secret

```bash
keybox get github_token
```

### Update value and comment

```bash
keybox update github_token ghp_new "rotated at 2026-03-08"
```

### Update comment only

```bash
keybox update github_token --comment "used for CI"
```

### Multi-line comments

`\n` will be stored as a newline.

```bash
keybox add aws_key AKIA... "prod\nread-only\nowner:platform"
```

### List stored keys

```bash
keybox list
```

### Delete a key

A confirmation prompt will be shown.

```bash
keybox delete github_token
```

## License

MIT License