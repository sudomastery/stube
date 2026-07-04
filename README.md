# STube

**Paste a link. Pick a quality. Done.**

STube is a dark-mode GTK4 / libadwaita downloader for YouTube and the
~1800 other sites [yt-dlp](https://github.com/yt-dlp/yt-dlp) supports.
Built for Fedora, works on GNOME and KDE.

![STube main window](screenshots/main.png)

## Features

- **One-box workflow** — paste a link and hit Download. MP4 video up to
  4K (or 1440p / 1080p / 720p / 480p), or audio-only MP3 / WAV
- **Star your favorite quality** in the dropdown to make it the
  permanent default
- **My Downloads** — full history of everything you've fetched; click an
  item to play it, hover for open-folder and remove buttons
- **Bulk Download** — point it at a `.txt` file with one link per line
  and it queues everything, three at a time
- **Cookies Setup** — borrows YouTube cookies from Brave, Chrome,
  Chromium, Edge or Firefox so YouTube treats downloads like normal
  viewing. Live status icon: green when configured, red when not.
  Cookies never leave your machine
- **Self-healing downloads** — automatic retries with plain-English
  error messages, and if cookies go stale it finds a working browser by
  itself
- **Desktop notifications** for finished and failed downloads, with a
  single summary notification for bulk batches
- **Playlists and embedding** — full-playlist downloads plus subtitle,
  thumbnail and metadata embedding under More options

## Download & Install

### Flatpak (recommended)

Grab the bundle from the
[latest release](https://github.com/sudomastery/stube/releases/latest)
and install it:

```bash
flatpak install --user ./STube-1.0.0-x86_64.flatpak
```

That's it — the required GNOME runtime is fetched from Flathub
automatically, and ffmpeg, yt-dlp and everything else is bundled.
Launch **STube** from the app grid, or:

```bash
flatpak run io.github.sudomastery.STube
```

To update, download the new bundle from Releases and run the same
install command. To uninstall:

```bash
flatpak uninstall --user io.github.sudomastery.STube
```

### From source (Fedora)

```bash
git clone https://github.com/sudomastery/stube.git
cd stube
./install.sh
```

The script installs the few Fedora system packages it needs
(`python3-gobject`, `gtk4`, `libadwaita`, `yt-dlp`, `ffmpeg-free`) if
they're missing, then puts STube in your app grid and on your `$PATH`.
Launch it from the app grid, or:

```bash
stube
```

Or run it straight from the repo without installing:

```bash
/usr/bin/python3 stube.py
```

> Note: it deliberately uses `/usr/bin/python3` (not pyenv/conda
> pythons) so it can see the system GTK bindings.

Uninstall the source install with:

```bash
rm -rf ~/.local/share/stube ~/.local/bin/stube \
       ~/.local/share/applications/io.github.sudomastery.STube.desktop \
       ~/.local/share/icons/hicolor/*/apps/io.github.sudomastery.STube.png
```

### RPM

`stube.spec` builds a native RPM:

```bash
rpmbuild -ba stube.spec
```

## License

MIT — see [LICENSE](LICENSE).
