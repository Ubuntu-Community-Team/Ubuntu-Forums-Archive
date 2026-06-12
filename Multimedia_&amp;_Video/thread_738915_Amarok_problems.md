---
title: "Amarok problems"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by SoAnIs on 2008-03-29
I am using Ubuntu 7.10, compiz enabled, amd64.

First: Amarok only works when started with gksudo, not normally. normal startup via the icon in the applications menu. Starting "amarokapp" on the terminal gives the following output, then succeeds:

```
amarokapp
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x994be0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x994be0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
STARTUP

```

Second problem: The global shortcuts for changing song ratings don't work. They only work when the amarok window has focus. I have them set to Win+KP_1 through Win+KP_5. I am using a Unicomp PS/2 Model M keyboard (P/N UB40R46). It's hardware DSK layout, it works fine. IE, it's not a keyboard issue, and I don't have "multimedia" keys or similar. Nothing in "System > Preferences > Keyboard Shortcuts" is bound to these keys. Searching through Gconf-editor for "<Super>" finds nothing bound to these keys.

I am only using amarok because it offers global shortcuts for ratings, as I'm trying to find something with a featureset similar to that of Foobar2000. Switching to an alternate player is acceptable as long as it offers global hotkeys (Need: ratings, changing tracks, changing volume, Want: removing songs from playlist) ability to handle medium (5000 + tracks) playlists, fetching lyrics from the internet.

---

### Post by lesergi on 2008-03-29
Hi,

I'd try to uninstall Amarok and installing it again, maybe this form solves some dependence problems, I don't know. Try removing .kde directory config from user home.

Shortcut problems I don't know if they must work in Gnome...

Regards.

---

### Post by SoAnIs on 2008-03-30
Installed KDE, that fixed the startup problem.

Global shortcuts still broken, in both gnome and kde. What's interesting is that the shortcuts for changing songs and volume do work, and they are only bound in amarok.

---

