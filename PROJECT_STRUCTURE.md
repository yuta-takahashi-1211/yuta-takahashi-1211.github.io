# Project Structure Documentation

This document explains the folder structure and how to maintain your academic website.

## Overview

This is a **Jekyll-based website** using the [Minimal Mistakes theme](https://github.com/mmistakes/minimal-mistakes). Jekyll is a static site generator that converts markdown files into HTML pages.

---

## Main Configuration Files

### `_config.yml`
**Purpose:** Main configuration file for the entire website

**Key settings:**
- Site title, name, description
- Author information (name, bio, avatar, location)
- Email and contact information
- Theme settings and plugins
- URL and baseurl settings

**When to edit:**
- Changing your name, email, or bio
- Updating your profile picture URL
- Changing the site's color theme (`minimal_mistakes_skin`)
- Modifying global site settings

---

## Important Directories

### `_pages/`
**Purpose:** Contains all main pages of your website

**Files in this directory:**
- `about.md` - About/home page
- `research.md` - Research page listing publications
- `ra.md` - Research Assistant recruitment page
- `cv.md` - CV page
- `teaching.html` - Teaching page
- `talks.html` - Talks/presentations page
- `publications.html` - Publications archive page
- `portfolio.html` - Portfolio page

**How to add a new page:**
1. Create a new `.md` file in this directory
2. Add front matter at the top:
```yaml
---
layout: single
title: "Your Page Title"
permalink: /your-page-url/
author_profile: true
---
```
3. Write your content in markdown below the front matter
4. Add the page to navigation (see `_data/navigation.yml`)

**Front matter explanation:**
- `layout: single` - Uses the single page layout
- `title:` - Page title shown in browser tab and page header
- `permalink:` - URL path for the page (e.g., `/research/` becomes `yourdomain.com/research/`)
- `author_profile: true` - Shows your profile sidebar on the page

---

### `_data/`
**Purpose:** Contains data files that control site-wide settings

**Key file: `navigation.yml`**
- Controls the navigation menu at the top of your site
- Format:
```yaml
main:
  - title: "Menu Item Name"
    url: /page-url/  # For internal pages
  - title: "External Link"
    url: https://full-url.com  # For external links
```

**How to add a menu item:**
1. Open `_data/navigation.yml`
2. Add a new entry under `main:`
3. Specify the title and URL
4. The order in the file determines the order in the menu

---

### `_publications/`
**Purpose:** Individual publication entries

**Format:** Each file should have:
```yaml
---
title: "Paper Title"
collection: publications
permalink: /publication/paper-name
date: 2024-01-01
venue: 'Journal Name'
paperurl: 'http://link-to-paper.com'
---
```

**Note:** The `_pages/research.md` file manually lists publications, so you can either:
- Use the collection system (files in `_publications/`)
- Manually list in `research.md` (current approach)

---

### `_posts/`
**Purpose:** Blog posts (if you want to use the blog feature)

**Format:**
- Filename: `YYYY-MM-DD-post-title.md`
- Front matter similar to pages, plus `categories` and `tags`

---

### `_teaching/` and `_talks/`
**Purpose:** Teaching and talk entries displayed in collection pages

**Similar to publications:** Each file represents one teaching position or talk

---

### `assets/`
**Purpose:** Static assets like images, CSS, and JavaScript

**Subdirectories:**
- `assets/images/` - Image files (profile pictures, figures, etc.)
- `assets/css/` - Custom CSS files
- `assets/js/` - Custom JavaScript files

**How to add images:**
1. Upload image to `assets/images/`
2. Reference in markdown: `![Alt text](/assets/images/filename.jpg)`
3. For profile picture, update `avatar` field in `_config.yml`

---

### `_includes/`, `_layouts/`, `_sass/`
**Purpose:** Theme template files

**⚠️ Warning:** These are advanced theme customization files. Only modify if you understand HTML/CSS/Jekyll templating.

- `_includes/` - Reusable HTML snippets (header, footer, sidebar, etc.)
- `_layouts/` - Page layout templates
- `_sass/` - Sass/CSS styling files

---

### `files/`
**Purpose:** Downloadable files (PDFs, documents, etc.)

**Usage:**
- Store paper PDFs, CV, or other downloadable files here
- Link to them in your pages: `[Download PDF](/files/paper.pdf)`

---

## Common Tasks

### 1. **Update your research page**
**File:** `_pages/research.md`

**Steps:**
1. Open the file
2. Add papers in markdown list format:
```markdown
- ["Paper Title"](link-to-paper) — *Journal Name* (Year), with Coauthor Names
```
3. Save the file
4. Commit and push to GitHub

---

### 2. **Change your profile information**
**File:** `_config.yml`

**What you can change:**
- `name:` - Your name
- `email:` - Contact email
- `author: bio:` - Short bio text
- `author: avatar:` - Profile picture URL
- `author: location:` - Your location
- `author: links:` - Contact links (email, website, etc.)

---

### 3. **Update navigation menu**
**File:** `_data/navigation.yml`

**To reorder menu items:**
- Change the order of entries in the file

**To add a new menu item:**
```yaml
- title: "New Page"
  url: /new-page/
```

**To remove a menu item:**
- Delete the corresponding entry

---

### 4. **Add a new page**
**Steps:**
1. Create file in `_pages/` directory (e.g., `_pages/newpage.md`)
2. Add front matter:
```yaml
---
layout: single
title: "Page Title"
permalink: /newpage/
author_profile: true
---
```
3. Write content in markdown
4. Add to `_data/navigation.yml` if you want it in the menu
5. Commit and push

---

### 5. **Change website theme/colors**
**File:** `_config.yml`

**Line to modify:**
```yaml
minimal_mistakes_skin: "air"
```

**Available skins:**
- `air` (current - light and clean)
- `aqua` - Blue/teal theme
- `contrast` - High contrast dark theme
- `dark` - Dark theme
- `dirt` - Brown/earthy theme
- `mint` - Green/mint theme
- `neon` - Bright neon accents
- `plum` - Purple theme
- `sunrise` - Orange/warm theme

---

## Git Workflow

### Basic workflow for making changes:

1. **Make your edits** to the necessary files
2. **Check status:**
   ```bash
   git status
   ```
3. **Stage changes:**
   ```bash
   git add .
   ```
4. **Commit with message:**
   ```bash
   git commit -m "Description of changes"
   ```
5. **Push to GitHub:**
   ```bash
   git push -u origin branch-name
   ```

GitHub Pages will automatically rebuild your site after each push (takes 1-2 minutes).

---

## Jekyll Basics

### What is Jekyll?
Jekyll converts your markdown files and templates into a complete HTML website.

### How it works:
1. You write content in **markdown** (`.md` files)
2. Jekyll processes the files using **layouts** and **includes**
3. It generates static **HTML files**
4. GitHub Pages hosts these HTML files

### Front Matter
Every page/post needs front matter (YAML between `---` lines):
```yaml
---
layout: single
title: "Page Title"
permalink: /url-path/
---
```

### Markdown syntax quick reference:
```markdown
# Heading 1
## Heading 2
### Heading 3

**bold text**
*italic text*

[Link text](https://url.com)
![Image alt text](/path/to/image.jpg)

- Bullet point
- Another point

1. Numbered list
2. Second item
```

---

## Troubleshooting

### Site not updating after push?
- Wait 2-3 minutes for GitHub Pages to rebuild
- Check GitHub Actions tab for build errors
- Clear your browser cache

### Navigation menu not showing new page?
- Make sure you added it to `_data/navigation.yml`
- Check that the `url:` matches the page's `permalink:`

### Profile picture not showing?
- Check the image URL in `_config.yml` under `author: avatar:`
- Make sure the image file is in `assets/images/`
- Use the full path: `/assets/images/filename.jpg`

### Page showing 404 error?
- Check that `permalink:` in front matter matches the URL you're visiting
- Make sure the file is in `_pages/` directory
- Check that `_pages` is included in `_config.yml` (should already be set)

---

## File Structure Summary

```
yuta-takahashi-1211.github.io/
│
├── _config.yml              # Main configuration file ⚙️
├── index.md                 # Homepage content
│
├── _data/
│   └── navigation.yml       # Navigation menu configuration 📍
│
├── _pages/                  # Main pages of your site 📄
│   ├── about.md
│   ├── research.md         # Research publications page
│   ├── ra.md               # Research Assistant page
│   ├── cv.md
│   ├── teaching.html
│   ├── talks.html
│   └── publications.html
│
├── _publications/           # Publication entries 📚
│   └── *.md
│
├── _posts/                  # Blog posts 📝
│   └── YYYY-MM-DD-*.md
│
├── _teaching/               # Teaching entries 🎓
│   └── *.md
│
├── _talks/                  # Talk entries 🎤
│   └── *.md
│
├── assets/                  # Static files 🖼️
│   ├── images/             # Image files
│   ├── css/                # Custom styles
│   └── js/                 # Custom scripts
│
├── files/                   # Downloadable files 📎
│   └── *.pdf
│
├── _includes/               # Reusable HTML snippets ⚠️
├── _layouts/                # Page templates ⚠️
└── _sass/                   # Style files ⚠️
```

**Legend:**
- ⚙️ = Core configuration
- 📍 = Navigation control
- 📄 = Content you'll edit often
- 📚📝🎓🎤 = Collection content
- 🖼️📎 = Media and downloads
- ⚠️ = Advanced files (edit with caution)

---

## Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Minimal Mistakes Theme Docs](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

---

## Quick Start Checklist

When you want to make changes to your website:

- [ ] **Update research:** Edit `_pages/research.md`
- [ ] **Update profile:** Edit `_config.yml`
- [ ] **Add new page:** Create file in `_pages/`, add to `_data/navigation.yml`
- [ ] **Change menu:** Edit `_data/navigation.yml`
- [ ] **Add image:** Upload to `assets/images/`
- [ ] **Test locally:** (Optional) Run `bundle exec jekyll serve`
- [ ] **Commit and push:** Git commit and push to GitHub
- [ ] **Wait 2-3 minutes:** GitHub Pages rebuilds your site

---

*Last updated: November 2025*
