---
title: "Amarok : problem with sqlite"
date: 2008-08-25
forum: Multimedia Software
---

### Post by 1stepkloser on 2008-08-25
when building a collection with Sqlite the amarok terminates suddenly.
(when using Postgresql this doesnt happen && Amarok works well with Sqlite on ROOT)

(using amarok 1.4.10)

can anyone pls help me to work this out on Sqlite ...



heres the output.

thilina@debian:~$ amarokapp 
kbuildsycoca running...
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
Amarok is crashing...
Running: gdb --nw -n --batch -x /home/thilina/.kde/tmp-debian/amarokGLHgMa.tmp amarokapp 3675
Running: file `which amarokapp`
1.4.10 [___stripped][validity: 0.33][frames: 129][xine]

Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! Perhaps an upgrade is already available which fixes the problem. Please check your distribution's software repository.
thilina@debian:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x280009e

thilina@debian:~$

---

