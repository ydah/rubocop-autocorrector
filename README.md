# rubocop-autocorrector

[Custom action](https://docs.github.com/en//actions/creating-actions/about-custom-actions) to autocorrect rubocop offenses.

## Usage

An example workflow to run rubocop-autocorrector via adding labels to pull requests.

```yaml
# .github/workflows/rubocop-autocorrector.yml
name: rubocop-autocorrector
on:
  pull_request:
    types: [labeled]
jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - uses: ydah/rubocop-autocorrector@main
        with:
          github_token: ${{ secrets.WRITABLE_GITHUB_TOKEN }}
```

## Inputs

### `github_token`

- GitHub access token to run another workflows from new pull request.
  - Don't forget to add `workflow` scope to this token
- optional

### `triggered_label_autocorrect_all`

- Specify the label to be triggered (rubocop --autocorrect-all).
- default: `rubocop-autocorrect-all`
- optional

### `triggered_label_autocorrect`

- Specify the label to be triggered (rubocop --autocorrect).
- default: `rubocop-autocorrect`
- optional

### `preparation_command`

- Specify the label to be triggered.
- default: `""` (empty string means no op)
- optional
