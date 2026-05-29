# Project remarks — sylllp.github.io

Living checklist for this Jekyll blog on GitHub Pages. Template origin: [karpathy/karpathy.github.io](https://github.com/karpathy/karpathy.github.io) (optional one-line credit in `Readme.md` only).

---

## Current assessment

**Solid foundation**

- Standard Jekyll layout: `_config.yml`, `_layouts`, `_includes`, `_posts`, `index.html`, `feed.xml`, `css/main.css`.
- Repo name matches GitHub Pages **user site** URL: `https://sylllp.github.io` with `baseurl: ""`.
- Upstream branding and third-party IDs are largely gone from the live templates.
- Disqus is centralized in `_includes/disqus.html` and driven by `site.disqus_shortname`.
- MathJax uses a current CDN (`jsDelivr`, MathJax 4) and loads only when `mathjax: true` on a page.
- Google Analytics block removed from `_includes/head.html`.
- RSS icon present (`assets/Generic_Feed-icon.svg`), linked from `_includes/header.html`.
- `.gitignore` covers `_site/`, Jekyll caches, `.DS_Store`, and Bundler paths.
- Footer shows GitHub + LinkedIn (Twitter removed from config and footer).

**Still to do before the site feels “finished”**

- Write `description` in `_config.yml` (footer and RSS feed description are empty today).
- Add real body content to the first post, or hide it until ready.
- Add `Gemfile` + local `bundle exec jekyll serve` workflow.
- Initialize git, push to `sylllp/sylllp.github.io`, confirm Pages build.
- Confirm Disqus forum `sylllp-blog` exists on [disqus.com](https://disqus.com) if you keep `comments: true`.

---

## Done — upstream cleanup

| Item | Status |
|------|--------|
| `_config.yml`: title, `url` (https), `github_username` | Done |
| `_config.yml`: removed `twitter_username` | Done |
| Google Analytics (Karpathy UA ID) | Removed from `head.html` |
| Disqus hardcoded `karpathyblog` in layouts | Replaced by `_includes/disqus.html` + `disqus_shortname: sylllp-blog` |
| MathJax `cdn.mathjax.org` | Updated in `_includes/mathjax.html` |
| RSS icon missing | Fixed (`Generic_Feed-icon.svg`) |
| `.gitignore` | Added |

No remaining `karpathy` / `karpathyblog` / old analytics references in site source (only this file mentions the fork for your records).

---

## Priority 1 — Config & content

### `_config.yml`

| Setting | Current | Action |
|---------|---------|--------|
| `title` | `Sylvain Le Liepvre blog` | OK; tweak wording if you prefer |
| `description` | `""` | **Add** a short tagline (shows in footer + RSS) |
| `url` | `https://sylllp.github.io` | OK |
| `github_username` | `sylllp` | OK |
| `linkedin_url` | set | OK |
| `disqus_shortname` | `sylllp-blog` | OK in config; register matching site on Disqus, or remove key + comments |
| `email` | empty | Optional: uncomment mailto in `_includes/footer.html` |

### First post — `_posts/2026-05-29-vision-for-healthcare.markdown`

- Front matter and per-post CSS are in place; **article body is still empty**.
- `comments: true` only works after Disqus site `sylllp-blog` is configured; otherwise set `comments: false` or remove the key.
- `mathjax: true` is fine once the post contains LaTeX; harmless on an empty post.

---

## Priority 2 — Publish on GitHub Pages

### Git repository

This folder is **not** a git repo yet (`git status` fails). Typical flow:

```bash
git init
git add .
git commit -m "Initial personal blog"
git branch -M main
git remote add origin git@github.com:sylllp/sylllp.github.io.git
git push -u origin main
```

Repo name must be **`sylllp.github.io`** (username + `.github.io`) for the user site URL.

### GitHub Pages settings

- **Settings → Pages** → Deploy from branch **`main`**, folder **`/` (root)**.
- Build uses GitHub’s Jekyll; no `gh-pages` branch needed.

### `Gemfile` (recommended)

Not present yet. Add for local builds that match GitHub Pages:

```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```

Then: `bundle install` and `bundle exec jekyll serve` → preview at `http://127.0.0.1:4000`.

Stick to [GitHub Pages–supported gems](https://pages.github.com/versions/) unless you add a custom Actions workflow.

---

## Priority 3 — Optional polish

| Item | Notes |
|------|--------|
| **Readme.md** | Expand: live URL, local serve, how to add a post (`_posts/YYYY-MM-DD-slug.markdown`, `layout: post`). |
| **Disqus** | If you do not want comments: remove `{% include disqus.html %}` from `_layouts/post.html` and `page.html`, drop `disqus_shortname` from config. |
| **About page** | Add e.g. `about.md` with `layout: page`, `title: About`, `includelink: true` for header nav. |
| **LICENSE** | Add if you want terms for the repo (upstream had none in your tree). |
| **Favicon** | Add under `assets/` and `<link rel="icon" …>` in `_includes/head.html`. |
| **Analytics** | Re-add only with your own GA4 / Plausible / etc. snippet in `head.html`. |
| **Fork credit** | Single line in `Readme.md` if you want to acknowledge the template; not required on the site itself. |

---

## Suggested order of work

1. Set `description` in `_config.yml`.
2. Write post content (or set `comments: false` until Disqus is live).
3. Add `Gemfile`, run `bundle exec jekyll serve`, fix any build warnings.
4. `git init` → commit → push → open `https://sylllp.github.io`.
5. Expand `Readme.md`; add `about.md` if you want nav links.

---

## File map (your site)

| File | Role |
|------|------|
| `_config.yml` | Site title, URL, social, Disqus shortname |
| `_includes/head.html` | Meta, canonical, CSS, feed link |
| `_includes/header.html` | Title, RSS, nav from `site.pages` |
| `_includes/footer.html` | GitHub, LinkedIn, description |
| `_includes/disqus.html` | Comments embed (conditional) |
| `_includes/mathjax.html` | MathJax 4 (conditional) |
| `_layouts/post.html` | Blog post shell |
| `_layouts/page.html` | Static page shell |
| `_posts/*.markdown` | Blog posts |
| `remarks.md` | This checklist (not published by Jekyll) |

---

*Last updated from codebase review. Check off items as you complete them.*
