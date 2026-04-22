# Great Docs Gauntlet (GDG)

The Great Docs Gauntlet is a comprehensive test suite for [Great Docs](https://github.com/posit-dev/great-docs), a documentation generator for Python packages. It builds and publishes a hub of 250+ synthetic package documentation sites that exercise every feature and configuration option Great Docs supports.

## What This Repo Does

This repo hosts the GitHub Actions workflow that:

1. Clones the latest [great-docs](https://github.com/posit-dev/great-docs) source
2. Builds all 250+ synthetic test packages into fully rendered documentation sites
3. Assembles them into a navigable site with an index page, detail pages, build logs, and test coverage reports
4. Deploys to GitHub Pages

This runs nightly and can also be triggered manually from the Actions tab.

## Purpose

Great Docs generates documentation sites from Python packages. To ensure it handles the full range of real-world scenarios, the GDG defines synthetic packages that cover:

- docstring formats: NumPy, Google, Sphinx, and reST styles
- package layouts: flat, src, namespace, monorepo, flit, hatch, PDM, setuptools
- configuration options: reference sections, user guides, custom sections, CLI docs, changelogs, blogs
- theming: navbar colors, gradients, dark mode, hero sections, logos, announcement banners
- edge cases: empty modules, private symbols, deep nesting, large classes, unicode, math, overloads, etc.

Each package is built independently and the results are scored against expected outcomes, providing a live regression test for every Great Docs release.

## Viewing the GDG

Visit the deployed site at https://posit-dev.github.io/gdg/.

## Triggering a Build

Builds run automatically on a nightly schedule. To trigger one manually:

- **GitHub UI**: Go to **Actions -> Deploy GDG -> Run workflow**
- **CLI** (from the great-docs repo): `make hub-deploy`
- **gh CLI**: `gh workflow run deploy.yml --repo posit-dev/gdg`

You can optionally specify a `great_docs_ref` input to build against a specific branch, tag, or commit SHA.
