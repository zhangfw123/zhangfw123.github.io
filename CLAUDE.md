# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **pure HTML static academic personal website** for Fuwei Zhang (张富威), a PhD candidate at Beihang University. The site is hosted on GitHub Pages at https://zhangfw123.github.io/.

**Important: This is NOT a modern web application** - it uses legacy HTML 4.01 with table-based layouts and embedded CSS. There is no build process, package manager, or framework.

## Development Workflow

### Editing the Site
- **No build step required** - simply edit the HTML files directly
- Main pages: `index.html` (homepage), `news.html` (full news archive)
- Changes are reflected immediately after pushing to GitHub
- GitHub Pages automatically serves the site from the master branch

### Deployment
```bash
# Add and commit changes
git add .
git commit -m "description of changes"

# Push to GitHub (automatic deployment via GitHub Pages)
git push origin master
```

### Local Preview
Since this is a static HTML site with no build process:
- Option 1: Open `index.html` directly in a browser
- Option 2: Use any simple HTTP server (e.g., `python3 -m http.server 8000`)

**Note:** The 不蒜子 (busuanzi) visitor counter script may not work on `file://` protocol - requires HTTP/HTTPS.

## Architecture

### File Structure
```
├── index.html          # Main homepage (~738 lines)
├── news.html           # Full news archive page (~301 lines)
├── sitemap.xml         # SEO sitemap
├── images/             # Static assets
│   └── zhangfuwei.jpg  # Profile photo
└── data/               # Empty directory (reserved for future use)
```

### Page Layout (index.html)
The homepage is organized into sections with a fixed 960px centered container:

1. **Intro** - Profile photo, bio, contact info, social links (Google Scholar, GitHub)
2. **News** - Recent updates (truncated, links to `news.html`)
3. **Publications** - Research papers organized by year (2022-2026)
4. **Academic Services** - PC memberships and journal reviewing
5. **Education** - Academic background
6. **Honors and Awards** - List of awards and scholarships

### Styling System
- **Embedded CSS** - All styles are in `<style>` tags within each HTML file (no external CSS)
- **Font**: Lato (Google Fonts) - loaded via `<link>` tag in head
- **Color scheme**:
  - Links: Blue (#1772d0) → Orange (#e46911) on hover
  - Headings: Orange (#e46911)
  - Paper tags: Blue (#0076DF) with shadow
- **Layout**: Table-based HTML (legacy approach, not modern flexbox/grid)
- **Custom elements**: Non-standard HTML5 elements like `<heading>`, `<subheading>`, `<papertitle>`, `<name>`

### External Dependencies
- **Google Fonts**: Lato font family
- **不蒜子 (busuanzi)**: Visitor counter (`//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js`)
- **Google Site Verification**: Meta tag for SEO (`p7SNRHPF7y83Q-nNBLkrxFhAAosW2t40unwTxByZ0vo`)

### Template Heritage
This site is based on a template by Jon Barron (2019), adapted through multiple editors:
- Original: Jon Barron (2019)
- Edited by: whyisyoung (2020), sheng-qiang (2021), Yongchun Zhu (2022)
- Current maintainer: Fuwei Zhang (2025)

Edit history is maintained in HTML comments at the top of each file.

## Common Tasks

### Adding a New Publication
1. Find the appropriate year section in `index.html` (e.g., `<td width="100%"><heading>2026</heading></td>`)
2. Add a new `<tr>` with the paper details following existing format:
   - Use `<papertitle>` for the paper title
   - Add links to arXiv, code, project pages as needed
   - Include author list and venue information
   - Add optional tags using `<span class="tag">`

### Adding News Items
1. Add to the News section in `index.html` (for recent items)
2. Also add to `news.html` (for complete archive)
3. Use consistent format: **[YYYY.MM.DD]** Description

### Updating Profile Information
- Name, bio, and contact info are in the Intro section of `index.html`
- Profile photo: `images/zhangfuwei.jpg` (update file if needed)

## Important Constraints

- **Do not modernize** the codebase unless explicitly requested - the table-based layout and embedded CSS are intentional
- **No build tools** - do not add package.json, webpack, or any modern build pipeline
- **Maintain HTML 4.01** DOCTYPE and legacy styling approach
- Keep the same visual design and structure when making changes
- Preserve the edit history in HTML comments when updating files

## Git Repository

- **Remote**: `git@github.com:zhangfw123/zhangfw123.github.io.git`
- **Branch**: `master` (main branch)
- **Deployment**: GitHub Pages automatically serves from master branch
