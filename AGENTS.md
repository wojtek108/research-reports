# Research Reports — site collection

Static, dependency-free HTML site collection (mostly Gemini deep-research reports turned into interactive pages), hosted on GitHub Pages.

- **Repo:** https://github.com/wojtek108/research-reports (branch `main`, public)
- **Live URL:** https://wojtek108.github.io/research-reports/
- **Deploy:** GitHub Pages builds from `main` / root. No build step — commit + push is the whole deployment.

## Structure

- `index.html` — home page. Simple categorized list of all reports.
- All other `*.html` files are standalone, self-contained pages at the repo root (no subdirectories, no external asset files).

## Adding a new site — checklist

1. Create the page as a **single self-contained HTML file** at the repo root. Inline all CSS/JS. No frameworks, no build tools, no external local assets.
2. **File name:** lowercase, Polish text transliterated (`ł→l`, `ś→s`, etc.), words joined with underscores (see existing files, e.g. `centrum_optymalizacji_neuroplastyczno_ci.html`).
3. **Add a "← Index" pill link** right after `<body>`. Match the pill to the page theme (light pages use the standard light pill; dark pages use the dark variant). Example (light):
   ```html
   <a href="index.html" style="position:fixed;top:14px;left:14px;z-index:9999;font:600 0.85rem/1 -apple-system,BlinkMacSystemFont,sans-serif;color:#2F6B4F;background:#fff;border:1px solid #E3E6E0;border-radius:999px;padding:8px 14px;text-decoration:none;box-shadow:0 2px 8px rgba(0,0,0,.08);">← Index</a>
   ```
4. **Dates:** the file creation date is treated as the report's official date. Hard-code it into the page if the page displays a date — never use `new Date()` for a report date (visitors would see "today" instead of the real date).
5. **Update `index.html`:**
   - Add the entry under the correct category heading (create a new `<h2>` category only if nothing fits).
   - Entry format: bold title + date badge (`· DD.MM.YYYY`, file creation date) + one-line muted description.
   - Current categories: **Suplementacja i długowieczność**, **Mózg i poznanie**, **Programowanie / ML**.
6. Commit and push to `main`. Pages rebuilds automatically (~1 min).

## Conventions

- Language: reports are Polish; the ML/programming page is English. Mark non-Polish entries with "(EN)" in the title on the index.
- Page title in `<title>` and `<h1>` must match the index entry.
- Design language of the index: light background `#F6F7F4`, text `#1A1D21`, accent green `#2F6B4F`, borders `#E3E6E0`, system font stack. Keep new pages visually independent but reasonably clean.

## Gotchas

- Polish filenames were mangled at creation (`neuroplastyczno_ci` = `neuroplastyczności`). Keep this transliteration style for consistency.
- All links between pages are relative and bare filenames — no leading `/`, so the site works both locally (`file://`) and under the `/research-reports/` Pages subpath.
