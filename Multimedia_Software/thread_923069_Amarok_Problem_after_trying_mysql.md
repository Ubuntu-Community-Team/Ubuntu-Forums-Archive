---
title: "Amarok Problem after trying mysql"
date: 2008-09-18
forum: Multimedia Software
---

### Post by Aryding on 2008-09-18
I read Mike's Ubuntu blog on how to setup mysql for amarok and it won't work

When I start amarok in the terminal I get this:

aryding@aryding-desktop:~$ sudo amarok
[sudo] password for aryding: 
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Error: "/tmp/kde-aryding" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-aryding" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-aryding" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-aryding" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-aryding" is owned by uid 1000 instead of uid 0.
DCOP Cleaning up dead connections.
Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x76db20 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x76db20 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Error: "/tmp/kde-aryding" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-aryding" is owned by uid 1000 instead of uid 0.
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
aryding@aryding-desktop:~$ Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-aryding" is owned by uid 1000 instead of uid 0.
QWidget::setMinimumSize: The smallest allowed size is (0,0)






Any help is greatly appreciated.  Thanks!

---

### Post by cimness on 2008-10-08
Having the same problem, same error message, but I didn't try to install msql - I've no idea why it's doing this. I hadn't installed any new packages immediately beforehand.

edit: Was able to fix the problem by removing Amarok, running autoremove, then reinstalling from the command line, then running it from the terminal using the command "amarokapp". No idea WHY this works, though...

---

