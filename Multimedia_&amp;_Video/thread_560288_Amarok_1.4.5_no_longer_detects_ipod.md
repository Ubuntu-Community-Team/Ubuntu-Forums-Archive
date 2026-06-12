---
title: "Amarok 1.4.5 no longer detects ipod"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by haelen on 2007-09-26
Hi,

Yesterday I downloaded an app from a non-authenticated (although I am sure "safe") repository.

Now when I launch Amarok,  I get the error "KLibloader could not load plugin - Error Message: libgpod.so.i: cannot open shared object file or directory.
```

haelen@haelen-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8095eb8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8095eb8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
```

Any ideas?

TIA,
Tim

---

### Post by haelen on 2007-09-26
Now sorted. Got rid of the 'bad' repo. It had installed incompatible versions of lbgpod1.:)

---

