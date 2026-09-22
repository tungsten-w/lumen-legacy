<div align="center">

# ✦ lumen-v1 ✦

**The bash scripts that became [lumen](https://github.com/tungsten-w/lumen).**


![status](https://img.shields.io/badge/status-legacy-C36EFF?style=flat-square) ![Bash](https://img.shields.io/badge/built_with-Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white) ![Hyprland](https://img.shields.io/badge/Wayland-Hyprland-9ED53C?style=flat-square&logo=hyprland&logoColor=white)

</div>

---

Before lumen was a Rust daemon, it was a handful of shell scripts glued to a rofi
menu: pick a wallpaper, and pywal + Noctalia repaint the desktop around it, light
or dark.

> [!NOTE]
> Kept for history. The maintained version is **[lumen](https://github.com/tungsten-w/lumen)**.

## Scripts

| Script | What it does |
| --- | --- |
| `wallpaper_light-dark.sh` | Main entry point. A rofi menu with four modes: pick a **dark** or **light** wallpaper from a thumbnail grid, or get a random one for the **time of day** or the **season**. |
| `wallpaper_time.sh` | The time-of-day mode without the menu, handy for a timer. Also switches the Obsidian theme. |
| `wallpaper_recognition.sh` | Tags images by dominant color by renaming them (`beach.jpg` → `beach-#orange.jpg`). |
| `wallpaperchoise.sh` | The older menu, which called one separate script per mode. |
| `wallpaperimage0.sh` | Pops up a small feh preview of the current wallpaper. |

Applying a wallpaper sets it with an `awww` transition, generates the palette with
pywal, switches Noctalia Shell to light or dark, and keeps a
`current_wallpaper.jpg` symlink up to date.

## Setup

Needs `rofi`, `imagemagick`, `awww`, `pywal`, Noctalia Shell (`qs`), `jq`, `feh`
and a Nerd Font for the menu icons.

The scripts expect to live in `~/.config/.scripts/`, with the rofi themes
`wallpaper.rasi` and `wallpaperchoise.rasi` in `~/.config/rofi/` (not included),
and wallpapers sorted like this:

```
~/Pictures/Wallpapers/
├── dark/
├── light/
└── season-time/
    ├── day/        # 07h–18h
    ├── sunset/     # 18h–22h
    ├── night/      # 22h–07h
    ├── hiver/
    ├── printemps/
    ├── ete/
    └── automne/
```

Then bind the main script in your Hyprland config:

```ini
bind = SUPER, W, exec, ~/.config/.scripts/wallpaper_light-dark.sh


```

thanks you ! 
