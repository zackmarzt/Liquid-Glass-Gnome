# Liquid Glass GNOME Theme

Liquid Glass is a modern, full-dark desktop theme for GNOME and XFCE, characterized by its glassy ("Aqua") aesthetic and vibrant blue accent color. It is primarily built as a set of overrides and refinements for the Ubuntu **Yaru** theme.

## Project Structure

- **`gnome-shell/`**: Contains `gnome-shell.css` which overrides the default shell styling to introduce glassy menus and custom panel appearance.
- **`gtk-2.0/`, `gtk-3.0/`, `gtk-4.0/`**: Implementation of the GTK theme across different versions.
  - GTK 3 and 4 utilize `@import` to load base Yaru styles and apply custom CSS overrides.
  - GTK 2 uses traditional `.rc` files and a large set of PNG assets.
- **`metacity-1/`**: Defines window decorations (titlebars, buttons) for GNOME's Metacity/Marco window managers using XML and SVG assets.
- **`xfwm4/`**: Theme assets and configuration for the XFCE window manager.
- **`index.theme`**: The master metadata file used by desktop environments to identify and load the theme.

## Key Technologies

- **CSS/SCSS**: Core styling for GNOME Shell and GTK 3/4.
- **GTK (GIMP Toolkit)**: The underlying UI toolkit supported (versions 2, 3, and 4).
- **SVG & PNG Assets**: Used for window controls, icons, and legacy GTK 2 widgets.
- **XML**: Used for Metacity theme definitions.

## Installation and Usage

To install the theme for the current user:

1.  Create the themes directory if it doesn't exist:
    ```bash
    mkdir -p ~/.themes
    ```
2.  Copy the project directory into `~/.themes/`:
    ```bash
    cp -r . ~/.themes/Liquid-Glass-Gnome
    ```
3.  Apply the theme using **GNOME Tweaks** or via CLI:
    ```bash
    gsettings set org.gnome.desktop.interface gtk-theme "Liquid-Glass-Gnome"
    gsettings set org.gnome.shell.extensions.user-theme name "Liquid-Glass-Gnome"
    ```

## Development Conventions

- **Override Pattern**: For GTK 3/4 and GNOME Shell, maintain the pattern of importing base themes and keeping custom overrides in a dedicated section at the top of the CSS files.
- **Asset Management**: New assets should be placed in the respective `assets/` subdirectories (e.g., `gtk-2.0/assets/`). SVG is preferred for new window controls to ensure high-DPI compatibility.
- **Consistency**: Ensure that the `@define-color` variables in `gtk-3.0/gtk.css` and `gtk-4.0/gtk.css` are kept in sync to provide a unified experience across applications.
