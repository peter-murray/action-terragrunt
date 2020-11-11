[![license](https://img.shields.io/github/license/peter-murray/terragrunt-github-action)](https://github.com/peter-murray/terragrunt-github-action/blob/master/LICENSE)
[![release](https://img.shields.io/github/release/peter-murray/terragrunt-github-action.svg)](https://github.com/peter-murray/terragrunt-github-action/releases/latest)
[![GitHub release date](https://img.shields.io/github/release-date/peter-murray/terragrunt-github-action.svg)](https://github.com/peter-murray/terragrunt-github-action/releases)


# Setup Terragrunt GitHub Action

Set up your GitHub Actions workflow with a specific version of [Terragrunt](https://terragrunt.gruntwork.io/).

This action is a hard fork of https://github.com/autero1/action-terragrunt which was required as the maintainer was not responding to the necessary updates to resolve
[CVE-2020-15228](https://github.com/advisories/GHSA-mfwh-5m23-j46w) which would result in this action no longer functioning after [November 16 2020](https://github.blog/changelog/2020-11-09-github-actions-removing-set-env-and-add-path-commands-on-november-16/).


## Usage

The next example step will install Terragrunt 0.21.13.

```yaml
name: Example workflow

on: [push]

jobs:
  example:
    name: Example Terragrunt interaction
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Setup Terragrunt
        uses: peter-murray/terragrunt-github-action@v1.0.0
        with:
          terragrunt_version: 0.21.13

      - name: Interact with Terragrunt
        run: terragrunt --version
```

### Inputs

| Parameter | Description | Required |
| --------- | ----------- | -------- |
| `terragrunt_version` | Terragrunt [version](https://github.com/gruntwork-io/terragrunt/releases) to deploy | true |

### Outputs

| Parameter | Description |
| --------- | ----------- |
| `terragrunt_path` | Cached tool path of Terragrunt |

### Supported platforms

This action has been tested on the following platforms:

* ubuntu-18.04
* windows-latest
* macos-latest


## License

The scripts and documentation in this project are released under the [MIT](./LICENSE) license.
