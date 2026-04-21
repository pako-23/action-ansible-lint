[![Latest Release](https://img.shields.io/github/v/release/pako-23/action-ansible-lint?sort=semver)](https://github.com/pako-23/action-ansible-lint/releases/latest)
[![Lint YAML](https://github.com/pako-23/action-ansible-lint/actions/workflows/lint.yaml/badge.svg)](https://github.com/pako-23/action-ansible-lint/actions/workflows/lint.yaml)

# ansible-lint GitHub Action

A GitHub Action to lint [Ansible] playbooks, roles and collections
using [ansible-lint].

## Usage

```yaml
- uses: pako-23/action-ansible-lint@v0
  with:
    files: .
    working_directory: ${{ github.workspace }}
```


## Inputs

| Input | Description | Default |
|-------|-------------|:-------:|
| `files` | Files or directories to check | `.` |
| `working_directory` | The directory where to run ansible-lint from | `${{ github.workspace }}` |

## Example Workflow

```yaml
name: Lint Ansible role

on:
  push:
    branches:
      - main
    paths:
      - '**.yaml'
      - '**.yml'
  pull_request:
    paths:
      - '**.yaml'
      - '**.yml'

jobs:
  yamllint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6

      - uses: pako-23/action-ansible-lint@v0
```

## License

[MIT](LICENSE)

[ansible]:
  https://docs.ansible.com/projects/ansible/latest/getting_started/introduction.html
[ansible-lint]:
  https://docs.ansible.com/projects/lint/
