<!-- Copilot / AI agent instructions for `taekseuk.github.io` -->

This repository is a Jekyll-based personal/academic website built from the "Academic Pages" template.
The file below gives focused, actionable guidance so an AI coding agent becomes productive quickly in this codebase.

Quick summary
- **Tech stack**: Jekyll (Ruby), GitHub Pages, some Node tooling for JS asset builds, optional Docker dev container.
- **Primary tasks**: edit Markdown pages in `_pages`, `_posts`, collections (`_talks`, `_publications`, `_teaching`, `_portfolio`), templates in `_includes` and `_layouts`, and site config in `_config.yml`.

Key files & locations
- `/_config.yml` — global site settings; **changes require restarting `jekyll serve`**.
- `Gemfile` — Jekyll and plugin gems (also `github-pages`). Use `bundle install` to install.
- `package.json` — simple JS build scripts: `npm run build:js` and `npm run watch:js`.
- `/_layouts`, `/_includes`, `/_sass` — theme templates and styles; change here to alter site chrome and components.
- `/_posts`, `/_talks`, `/_publications`, `_pages` — content collections; front matter controls layout and metadata.
- `/assets` and `/images` — static assets and generated `assets/js/main.min.js` (produced by `npm run uglify`).
- `/files` — user-uploaded files served directly.
- `/markdown_generator`, `talkmap/`, `talkmap.ipynb` — helper scripts/notebooks used to generate or process content.

What an AI agent should know (practical rules)
- Previewing locally: prefer the `bundle exec` command to ensure gem versions match `Gemfile`:

  `bundle install`
  `bundle exec jekyll serve -l -H localhost`

- `_config.yml` is not auto-reloaded. If you change site settings, stop and restart the Jekyll server.
- JS assets: run `npm run build:js` to produce `assets/js/main.min.js`; `npm run watch:js` can auto-build when editing JS.
- Docker: `docker compose up` will run a containerized dev server (useful if local Ruby/node install is inconvenient).
- DevContainer: repository includes settings for VS Code devcontainer; reopening in container will host the site at `http://localhost:4000`.

Conventions and patterns specific to this repo
- This repo follows Academic Pages (a Minimal Mistakes variant). Avoid renaming or moving template directories unless intentionally for a forked theme.
- Content is driven by YAML front matter. Common front-matter keys:
  - `layout` (e.g., `single`, `talk`), `author_profile`, `share`, `comments`, `permalink`.
  - Collections defined in `_config.yml` include `teaching`, `publications`, `portfolio`, `talks`.
- Permalinks use `/:categories/:title/` by default — be careful when changing slugs.
- `_data` is used for structured data (e.g., `authors.yml`, `cv.json`) — prefer updating those files for site-wide author/profile changes.

Editing guidance (examples)
- Add a blog post: create a file in `_posts/` named `YYYY-MM-DD-title.md` with front matter `layout: single`.
- Update site title or social info: edit `_config.yml` (then restart the server).
- Change header / footer: edit `_includes/masthead.html` or `_includes/footer.html`.
- Add image assets: put new images in `/images/` and reference them from Markdown or templates.

Safety & scope for AI edits
- Avoid large automatic refactors of theme internals unless the user asks — small, focused changes are preferred.
- Do not alter licensing or attribution lines without explicit user instruction (template attribution must remain intact).
- When adding dependencies: prefer updating `package.json` for JS or `Gemfile` for Ruby and include exact rationale in the PR description.

Developer workflow commands (PowerShell friendly)
  - Install dependencies:
    `bundle install`
    `npm install`
  - Run locally:
    `bundle exec jekyll serve -l -H localhost`
  - Build JS assets:
    `npm run build:js`
  - Docker dev (if Docker available):
    `docker compose up`

Where to look for common changes
- Templates: `/_layouts`, `/_includes`
- Styles: `/_sass` and `assets/css`
- JS: `assets/js`, `package.json` scripts
- Content: `_posts`, `_pages`, `_talks`, `_publications`, `_teaching`, `_portfolio`

Useful hints for PRs and commits
- Keep commits focused: one change per PR (content, template, style, or build tooling).
- If changing `_config.yml`, include steps to reproduce the site locally (e.g., restart instructions) in the PR description.
- When touching assets, include `npm run build:js` output or let CI handle asset builds if configured.

If anything is unclear or you want the instructions to be more detailed (examples of common edits, automated checks, or CI setup), tell me what to expand and I'll iterate.
