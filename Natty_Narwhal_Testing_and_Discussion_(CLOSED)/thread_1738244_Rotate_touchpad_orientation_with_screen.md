---
title: "Rotate touchpad orientation with screen"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jon4248 on 2011-04-24
soo, yeah...I've visited [http://cc.oulu.fi/~rantalai/synaptics/]("http://cc.oulu.fi/%7Erantalai/synaptics/") and unfortunately this won't seem to work with Natty (yet) or maybe I'm doing something wrong when trying to patch the driver source...I get the following error;

```
failed! (check stampdir/log/patch for details)
make: *** [stampdir/patch] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```My stampdir/log/patch file;

```
 Applying patch 01-synaptics-dont-grab-if-not-on-current-VT.patch
patching file src/synaptics.c

Applying patch 02-do-not-use-synaptics-for-keyboards.patch
patching file conf/11-x11-synaptics.fdi

Applying patch 03-man-no-hal.patch
patching file man/synaptics.man
Hunk #1 succeeded at 901 (offset 30 lines).

Applying patch 103_enable_cornertapping.patch
patching file src/synaptics.c
Hunk #1 succeeded at 551 with fuzz 1 (offset 87 lines).

Applying patch 104_always_enable_tapping.patch
patching file src/synaptics.c
Hunk #1 succeeded at 482 with fuzz 2 (offset 79 lines).

Applying patch 106_always_enable_vert_edge_scroll.patch
patching file src/synaptics.c
Hunk #1 succeeded at 493 with fuzz 2 (offset 80 lines).

Applying patch 114_jumpy_cursor_first_part.patch
patching file include/synaptics-properties.h
patching file man/synaptics.man
patching file src/properties.c
patching file src/synaptics.c
patching file src/synapticsstr.h
patching file tools/synclient.c

Applying patch 115_evdev_only.patch
patching file conf/50-synaptics.conf

Applying patch 116_xi2_1.patch
patching file configure.ac
patching file src/Makefile.am
patching file src/alpscomm.c
patching file src/eventcomm.c
patching file src/eventcomm.h
patching file src/ps2comm.c
patching file src/synaptics.c
patching file src/synapticsstr.h
patching file src/synproto.h

Applying patch 117_gestures.patch
patching file configure.ac
patching file src/Makefile.am
patching file src/eventcomm.c
patching file src/eventcomm.h
patching file src/grail.c
patching file src/synaptics.c
patching file src/synproto.h

Applying patch 118_quell_error_msg.patch
patching file tools/synclient.c
patching file tools/syndaemon.c

Applying patch 119_active_area_touches.patch
patching file src/eventcomm.c
patching file src/synaptics.c
patching file src/synproto.h

Applying patch 120_active_touches_num_fingers.patch
patching file src/eventcomm.c
Hunk #1 succeeded at 460 (offset 1 line).
Hunk #2 succeeded at 472 (offset 1 line).
Hunk #3 succeeded at 536 (offset 1 line).
patching file src/eventcomm.h

Applying patch 121_semi-mt_num_fingers.patch
patching file src/eventcomm.c
Hunk #3 succeeded at 459 (offset 1 line).
Hunk #4 succeeded at 477 (offset 1 line).
Hunk #5 succeeded at 547 (offset 1 line).
Hunk #6 succeeded at 679 (offset 1 line).
patching file src/eventcomm.h

Applying patch 122_revert_pressure_finger_default.patch
patching file src/synaptics.c
Hunk #1 succeeded at 466 (offset 3 lines).

Applying patch 123_order_ProcessTouch_for_numFingers.patch
patching file src/eventcomm.c

Applying patch 124_syndaemon_events.patch
patching file tools/syndaemon.c
Hunk #1 succeeded at 416 (offset 1 line).

Applying patch 125_enable_orientation.patch
patching file include/synaptics.h
Hunk #1 FAILED at 77.
1 out of 1 hunk FAILED -- rejects in file include/synaptics.h
patching file include/synaptics-properties.h
Hunk #1 succeeded at 158 with fuzz 2 (offset 16 lines).
patching file src/eventcomm.c
Hunk #1 FAILED at 352.
1 out of 1 hunk FAILED -- rejects in file src/eventcomm.c
patching file src/properties.c
Hunk #1 succeeded at 45 with fuzz 2 (offset 1 line).
Hunk #2 FAILED at 252.
Hunk #3 succeeded at 301 (offset 30 lines).
1 out of 3 hunks FAILED -- rejects in file src/properties.c
patching file src/synaptics.c
Hunk #1 succeeded at 505 with fuzz 1 (offset 72 lines).
patching file tools/synclient.c
Hunk #1 FAILED at 209.
1 out of 1 hunk FAILED -- rejects in file tools/synclient.c
Restoring src/properties.c
Restoring src/synaptics.c
Restoring src/eventcomm.c
Restoring include/synaptics.h
Restoring include/synaptics-properties.h
Restoring tools/synclient.c
Patch 125_enable_orientation.patch does not apply (enforce with -f)
Restoring src/properties.c
Restoring src/synaptics.c
Restoring src/eventcomm.c
Restoring include/synaptics.h
Restoring include/synaptics-properties.h
Restoring tools/synclient.c 
```Can anyone help me get my touchpad rotate with the screen please??

 Why oh why  isn't there simply an option under monitors is beyond me.


CelticBhoy even suggested it like two years ago too..sigh....[[IMG]http://brainstorm.ubuntu.com/idea/20789/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20789/)

---

