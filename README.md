# MkDocs Bootstrap Project

**Built with [WonderChat AI](https://wonderchat.dev).**

<a href="https://apps.apple.com/us/app/wonderchat-ai/id6752497385" target="_blank">
  <img src="https://developer.apple.com/assets/elements/badges/download-on-the-app-store.svg" alt="Download on the App Store" height="50">
</a>

## Technical Summary

This project provides a streamlined approach to setting up and deploying an MkDocs documentation site with the `mkdocs-material` theme, entirely automated through GitHub Actions.

### GitHub Actions Workflows:

1.  **`mkdocs_init.yml` (Manual Dispatch):**
    *   **Purpose:** Initializes a new MkDocs project within the repository.
    *   **Trigger:** Manually dispatched via `workflow_dispatch`.
    *   **Steps:**
        *   Checks out the repository.
        *   Sets up Python.
        *   Installs `mkdocs` and `mkdocs-material`.
        *   Runs `mkdocs new .` to create the basic project structure.
        *   Configures `mkdocs.yml` to use `theme: material`.
        *   Adds `site/` and `.DS_Store` to `.gitignore`.
        *   Commits and pushes these initial setup changes back to the repository.
    *   **Permissions:** Requires `contents: write` to commit and push changes.

2.  **`publish-pages.yml` (On Tag Push):**
    *   **Purpose:** Builds the MkDocs site and deploys it to GitHub Pages.
    *   **Trigger:** Pushes to tags matching `v*` (e.g., `v1.0.0`, `v1.1`).
    *   **Steps:**
        *   Checks out the repository.
        *   Configures GitHub Pages environment.
        *   Sets up Python.
        *   Installs `mkdocs` and `mkdocs-material`.
        *   Runs `mkdocs build` to generate the static site into the `site/` directory.
        *   Uploads the `site/` directory as a Pages artifact.
        *   Deploys the artifact to GitHub Pages.
    *   **Permissions:** Requires `contents: write`, `pages: write`, and `id-token: write` for artifact upload and deployment.

### Local Development:

To develop your documentation locally, ensure you have Python and pip installed, then run:

```bash
pip install mkdocs mkdocs-material
mkdocs serve
```

Your documentation will be accessible in your web browser, typically at `http://127.0.0.1:8000`.
