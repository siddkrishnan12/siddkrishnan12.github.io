# Siddharth Krishnan Portfolio

This repository holds Siddharth's portfolio site. GitHub Pages builds and hosts it for free. All content lives in the `_data/` folder, so updates mean editing a short list in a text file.

## Part 1. Put the site online (one time, about 20 minutes)

### Create the account and repository

1. Sign up at **github.com**. The username becomes part of the web address, so pick a professional one, such as `siddharth-krishnan`.
2. Click **+** (top right) → **New repository**.
3. Name the repository exactly `<username>.github.io`, for example `siddharth-krishnan.github.io`.
4. Choose **Public**, leave every other box unchecked, and click **Create repository**.

### Upload the files

1. On the new repository's page, click the link **uploading an existing file**.
2. Open the `github-site` folder on the computer. Select **everything inside it** (not the folder itself) and drag the selection into the browser window. The folders `_data`, `_includes`, `_layouts`, and `assets` must upload with their contents.
3. Click **Commit changes**.

### Turn on GitHub Pages

1. In the repository, open **Settings** → **Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**, the branch to **main**, and the folder to **/ (root)**. Click **Save**.
3. Wait one or two minutes, then visit `https://<username>.github.io`.

A different repository name also works, but then the site lives at `https://<username>.github.io/<repository-name>` and `_config.yml` needs `baseurl: "/<repository-name>"`.

## Optional: preview changes on your computer first

Editing on github.com publishes each change right away. To check changes privately before they go online, run the site on your own computer.

### One-time setup (Mac, about 15 minutes)

The Ruby that ships with macOS is too old for Jekyll, so install a current one with Homebrew.

1. Open **Terminal**.
2. If `brew --version` prints an error, install Homebrew with the command shown on **brew.sh**.
3. Install Ruby and put it on the path:
   ```bash
   brew install ruby
   echo 'export PATH="$(brew --prefix ruby)/bin:$PATH"' >> ~/.zshrc
   ```
   Close Terminal and open a new window. Then `ruby -v` should print version 3 or higher.
4. Copy the site to the computer. The simplest way is **GitHub Desktop** (desktop.github.com): sign in, choose **File** → **Clone repository**, and pick `<username>.github.io`.
5. In Terminal, go to the cloned folder and install the site's tools:
   ```bash
   cd ~/Documents/GitHub/<username>.github.io
   bundle install
   ```

On Windows, install Ruby with the **Ruby+Devkit** download from rubyinstaller.org, then continue from step 4 in a new Command Prompt.

### Each time

1. In Terminal, from the site folder, run:
   ```bash
   bundle exec jekyll serve --livereload
   ```
2. Open **http://localhost:4000** in a browser.
3. Edit files in any text editor (VS Code works well). The browser refreshes on each save. A typo in a `_data` file prints an error in Terminal instead.
4. Press **Ctrl+C** in Terminal to stop the preview.
5. In GitHub Desktop, write a short summary (for example "Add Desert Winds recording"), click **Commit to main**, then **Push origin**. The live site updates in about a minute.

## Part 2. Add or change an entry (about 5 minutes)

Each page reads from one file:

| Page | File |
|---|---|
| Home (intro, highlights, email, photos) | `_data/profile.yml` |
| Academics & Awards | `_data/academics.yml` |
| Arts | `_data/arts.yml` |
| Projects & Research | `_data/projects.yml` |
| Service & Leadership | `_data/service.yml` |
| Top menu | `_data/navigation.yml` |

To edit one:

1. On github.com, open the file and click the **pencil icon** (Edit).
2. Copy an existing entry, paste it in the right place, and change the text. Newest entries go first.
3. Click **Commit changes**. The site updates in about a minute.

### An entry, field by field

```yaml
    - title: "Desert Winds"
      date: "April 2026"
      role: "Composer"
      description: "Composed for the 2025–26 Allegro!!! Violin Ensemble."
      result: "four performances"
      image: "/assets/images/desert-winds.jpg"
      youtube: "pMnzc-tCMUE"
      audio: "/assets/files/desert-winds.mp3"
      score_pdf: "/assets/files/desert-winds-score.pdf"
      links:
        - label: "Ensemble"
          url: "https://www.wsste.com/allegro"
```

Only `title` is required; delete any line he doesn't need.

- **youtube**: the code after `v=` in a YouTube link. The page shows a player plus a "Watch on YouTube" link.
- **image**, **audio**, **score_pdf**: upload the file first (see below), then enter its path.
- **results**: a list of placements, as in the Scholastic Bowl entry in `academics.yml`. Add a `url:` line under a placement's `text:` (same indentation) to link that placement to its results page:
  ```yaml
        results:
          - label: "First place"
            text: "2026 IHSA State Tournament"
            url: "https://www.ihsa.org/..."
  ```
- **description**: `*text*` shows as italics.

A new school year gets a new block at the top of the file:

```yaml
- heading: "2026–27 · Grade 11"
  entries:
    - title: "..."
```

### Rules that keep the file working

- Indent with spaces, never tabs. Match the indentation of the entry above exactly.
- Keep every text value inside double quotes.
- Inside quoted text, write a double quote as `\"`. Apostrophes are fine as they are.

If an edit breaks the site, the **Actions** tab shows a red ✗ with the error, which is almost always indentation. The old version stays online until a fixed version builds. To undo an edit, open the file, click **History**, and copy back the earlier text.

## Part 3. Add photos, recordings, and scores

1. Open the `assets/images` folder (photos) or `assets/files` folder (MP3s and PDFs) in the repository.
2. Click **Add file** → **Upload files**, drag the file in, and click **Commit changes**.
3. In the entry, add `image: "/assets/images/<file name>"` (or `audio:` / `score_pdf:` with `/assets/files/<file name>`).

Keep file names lowercase with hyphens, such as `balkan-tour.jpg`. Resize photos to about 1600 pixels wide. GitHub accepts files up to 25 MB through the browser, so long recordings belong on YouTube (as **Unlisted**).

**Arts playlist:** create a YouTube playlist (set to Unlisted or Public), copy the code after `list=` in its link, and paste it into `playlist: ""` in `arts.md`. A player for the whole playlist then appears at the top of the Arts page. Any other page can take a `playlist:` line the same way.

**Home page photos:** set `headshot`, `banner_image`, and each highlight's `image` in `_data/profile.yml`.

## Part 4. Show the hidden pages

Projects & Research and Resume stay out of the menu until they have content. To show one, change its `show: false` to `show: true` in `_data/navigation.yml`.

For the resume, upload a PDF to `assets/files`, set `resume_pdf: "/assets/files/resume.pdf"` in `_data/profile.yml`, and show the Resume page.

## Part 5. Move visitors from the old Google Site

Google Sites cannot forward visitors automatically. Instead, replace the old Home page text with one line and a button: "My portfolio has moved to https://<username>.github.io". Update the address on any applications or profiles.

## Privacy

- The repository is public, so anyone can see these files and their full edit history. Never commit a home address, phone number, or birth date, even briefly.
- Ask before posting photos or video that show other students clearly.

## Files at a glance

```
_config.yml         site settings (title, baseurl)
_data/              all content
_layouts/           page templates
_includes/card.html the card design
assets/css/         colors and styles (sage green tokens at the top)
assets/images/      photos
assets/files/       recordings, scores, resume
index.html          Home
academics.md, arts.md, projects.md, service.md, resume.html   page stubs
```
