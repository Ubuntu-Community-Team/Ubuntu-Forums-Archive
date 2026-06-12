---
title: "Amarok and Movie Player fail to start"
date: 2008-07-02
forum: Multimedia Software
---

### Post by mik9dt on 2008-07-02
I am suddenly experiencing problems running Amarok.

When I run from the terminal this is what I get... any ideas?

user1@comp1:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d600 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d600 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
Could not find 'kmail' executable.
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
user1@comp1:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x520009a


Can anyone offer any help.
I recently installed Songbird but they had been co-existing  with no problems.
At the same time I can no longer use movie player...

---

