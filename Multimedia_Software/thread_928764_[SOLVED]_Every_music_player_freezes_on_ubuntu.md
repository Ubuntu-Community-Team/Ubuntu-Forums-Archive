---
title: "[SOLVED] Every music player freezes on ubuntu"
date: 2008-09-24
forum: Multimedia Software
---

### Post by Jo.T. on 2008-09-24
I'm having a nasty problem that is still without an answer despite my several attempts to solve it.

For some unknown reason I can't run any music player on ubuntu. At first I used Amarok frequently, but suddenly it got stuck so I wasn't able to run it in any way. I tried as root and restarted the system many times without an effect. 
 
I just got this:

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Error: "/tmp/ksocket-johanna" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-johanna" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-johanna" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-johanna" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-johanna" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-johanna" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-johanna" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-johanna" is owned by uid 1000 instead of uid 0.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097fa8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097fa8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
(23:27:57) Napster: QObject::connect: Incompatible sender/receiver arguments
StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Error: "/tmp/kde-johanna" is owned by uid 1000 instead of uid 0.
QPainter::begin: Cannot paint null pixmap
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

I removed and reinstalled it many times, but everytime it got stuck with that blue starting screen and did nothing. Sometimes it froze also Firefox. Only one time it mysteriously worked perfectly untill I had to reboot the system and the problem returned.

I also tried other music players such as Banshee, Rhythmbox, Kaffeine etc. but every single one of them froze at some point. Rhythmbox for example froze with mp3-files and Banshee froze when it tried moving to another song on the playlist. It seems that the bug is somewhere in the system (Ubuntu 7.10 gutsy).

I read about one similar case with Amarok (the same error message) but the problem vanished by itself unlike in my case.

So...

If you have any ideas, please let me know :)

EDIT: Found out that the problem is actually with Gnome. Anyone knows how to fix it?

---

### Post by Jo.T. on 2008-09-28
If someone is interested in the solution I shall explain.

I reinstalled PulseAudio and just poked some preferences and now everything works as dream. ;)

---

