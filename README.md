# Helm Chart Practice

## Pre-commit Hook (Local)

This project uses pre-commit hooks to ensure the quality and consistency of Helm charts. Before each commit, the system automatically performs Helm lint checks.

### Installing pre-commit

#### 1. Install pre-commit tool

**Using pip:**
```bash
pip install pre-commit
```

**Using Homebrew (macOS):**
```bash
brew install pre-commit
```

#### 2. Install Git hooks

Run in the project root directory:
```bash
pre-commit install
```

This will install the necessary hook scripts in the `.git/hooks/` directory.

### Configuration

The `.pre-commit-config.yaml` file in the project configures the following hooks:

```yaml
repos:
  - repo: https://github.com/gruntwork-io/pre-commit
    rev: v0.1.30 # pre-commit version to be used
    hooks:
      - id: helmlint
```

- **helmlint**: Executes `helm lint` checks on all Helm charts

### Usage

#### Automatic Execution
Pre-commit hooks run automatically every time you execute `git commit`:
```bash
git add .
git commit -m "Your commit message"
```

#### Manual Execution
You can also run all hooks manually:
```bash
pre-commit run --all-files
```

Run a specific hook:
```bash
pre-commit run helmlint --all-files
```

#### Skip Hooks (Not Recommended)
In emergency situations, you can skip hooks using `--no-verify`:
```bash
git commit -m "Emergency fix" --no-verify
```

### Troubleshooting

#### Update Hooks
If hooks are outdated, you can update them:
```bash
pre-commit autoupdate
```

#### Clear Cache
If you encounter issues, you can clear the pre-commit cache:
```bash
pre-commit clean
```

#### Check Installation Status
Verify that hooks are properly installed:
```bash
pre-commit run --all-files
```

