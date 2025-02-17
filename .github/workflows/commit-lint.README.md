# Commit Lint GitHub Action

This GitHub Action ensures that all commits in a pull request follow conventional commit standards using [commitlint](https://commitlint.js.org/).

## Features

- Automatically lints commit messages in pull requests.
- Ensures adherence to the [Conventional Commits](https://www.conventionalcommits.org/) specification.
- Runs on `ubuntu-latest`.

## Usage

### Basic Setup

To use this action, add the following to your repository's workflow file (e.g., `.github/workflows/commit-lint.yml`):

```yaml
name: Enforce Commit Linting
on:
  pull_request:
  workflow_call:

jobs:
  call-commit-lint:
    uses: xfuture603/.github/.github/workflows/commit-lint.yml@main
```

## How It Works

1. The action runs whenever a pull request is opened or updated.

2. It installs the required dependencies, including commitlint.

3. The configuration for commitlint is set to extend @commitlint/ config-conventional.

4. It checks all commits in the pull request against the Conventional Commits standard.

5. If a commit message does not follow the standard, the workflow will fail.

## Commit Message Guidelines

This action enforces the following commit message format:

```md
type(scope): description
```

Note: scope is optional

### Examples of Valid Commit Messages

```md
feat(auth): add login API

fix(ui): resolve button alignment issue

chore(deps): update dependency versions

docs: update installation instructions
```

### Examples of Invalid Commit Messages

```md
updated the file

fixed a bug

new feature added
```

## Troubleshooting

If the workflow fails due to invalid commit messages:

1. Review the GitHub Actions logs for details on the failing commits.

2. Amend the commit messages using `git rebase -i` and `git push --force-with-lease`.
