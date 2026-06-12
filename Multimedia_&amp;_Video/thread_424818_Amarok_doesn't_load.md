---
title: "Amarok doesn't load"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Sohum on 2007-04-27
This morning, I booted my computer, and tried to start amarok. 
It didn't.
So I ran it in the terminal.
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097500 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097500 ): KAccel object already contains an action name "play_pause"
*** attempt to put segment in horiz list twice
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
*** attempt to put segment in horiz list twice
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

Something has gone wrong, and I'm not sure what.

Please, help. I love amarok, and don't want to be without it.

---

### Post by Sohum on 2007-04-27
Oh, and when I Ctrl-C out, I get this.
```
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x520001c
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)

```

---

### Post by dreadlord_chris on 2007-04-27
That's weird - Amarok did the same thing to me this morning. Well, actually, it would load - sorta. I'd get a taskbar entry but no systray icon - but there would be a blank spot where the systray icon *should* be, and I'd get the **busy** pointer if I hovered my mouse over it. The Amarok window *would* open, but remained grey out & unusable.

When run from a terminal I got the same errors as you.

I rebooted a few times - after the 3rd time Amarok loaded fine?!?

Have no clue what the problem was, but apparently it fixed(?) itself....

---

### Post by Sohum on 2007-04-27
Those are the exact symptoms that I had got (blank toolbar icon, busy cursor), and now, after rebooting the comp, amarok seems to work fine.

*Shrug*?

---

### Post by dreadlord_chris on 2007-04-28
LOL.... Ubuntu - The Amazing Self-Healing OS

---

