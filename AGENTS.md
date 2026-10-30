# Scoop Bucket Agents Guide

Essential reference for AI agents working in this Scoop repository.

## Commands

- **Test manifests**: `pwsh -File .\bin\test.ps1` (or via Scoop environment)
- **Check/Lint manifests**: Automated via Pester tests (`Scoop-Bucket.Tests.ps1` and Scoop core test suite).

## Architecture & Structure

- `bucket/`: Contains JSON manifests for Scoop applications. Each file defines version, description, URL, architecture-specific binaries, hashes, checks, and updates.
- `scripts/`: Helper scripts.
- `deprecated/`: Old or unmaintained manifests.
- `.github/workflows/`: CI/CD automation including tests and `excavator.yml` for automated manifest updates.

## Manifest Conventions

- Standard Scoop JSON schema.
- Uses `checkver` and `autoupdate` blocks for automated tracking.
- Uses `persist` for keeping state across updates (e.g. databases).

## Gotchas

- Manifest hashes must be valid SHA-256 for binaries.
- Testing requires `SCOOP_HOME` pointing to a valid Scoop core installation.
- CI runs both Windows PowerShell and PowerShell Core.
