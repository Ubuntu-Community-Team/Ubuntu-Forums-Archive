---
title: "Amarok breaks after Envy install??"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by jorwex on 2008-01-10
So I installed Envy for kicks to see if it would make things run any better and installed the latest nvidia driver for my AGP 6600 and either upon rebooting, or during the driver install itself (i cant remember), i got a few error messages that popped up about amarok and kde stuff (i use gnome).

i normally have amarok as a startup program in 'sessions' but its icon isnt showing up. so i killed all the amarok related processes and ran it from the terminal to see if anything blew up:

```
jorwex@jorwex-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098eb8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098eb8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
```

if i run amarokapp, i get the same thing, except it starts from the 3rd line where it says kdecore (KAction....) etc..

any one know of a solution? i do feel like things are a bit quicker with envy, but it may be my imagination. if possible i'd still like to stick with it.

oh ya and one more possible important piece of info. When i set up amarok about 2 weeks ago I opted for MySQL instead of SQLite. And when I installed envy i opted for it to  change/optimize xorg.conf automatically.

THANKS!

---

