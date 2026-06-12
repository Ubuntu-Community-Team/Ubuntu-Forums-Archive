---
title: "Video starts at 1024x768 under Nouveau, should be 1280x1024"
date: 2011-05-15
forum: Multimedia Software
---

### Post by pwabrahams on 2011-05-15
I've been having a lot of trouble getting my screen resolution to stay at 1280x1024.  I've finally managed to get that resolution consistently with Nouveau, so I don't want to ditch Nouveau for the Nvidia stuff.  Using System Settings I can get the 1280x1024 resolution just fine.  The problem is that the setting is lost whenever the X server is restarted, and the resolution drops to 1024x768.   I have some idea of why that's happening, but I don't know what to do about it.  The following excerpt from **Xorg.0.log** is revealing:
```
[   918.419] (--) NOUVEAU(0): Chipset: "NVIDIA NV4c"
[   918.419] (II) NOUVEAU(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   918.419] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   918.419] (==) NOUVEAU(0): RGB weight 888
[   918.419] (==) NOUVEAU(0): Default visual is TrueColor
[   918.419] (==) NOUVEAU(0): Using HW cursor
[   918.419] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   918.870] (II) NOUVEAU(0): Output VGA-1 using monitor section VGA-1
[   919.330] (II) NOUVEAU(0): EDID for output VGA-1
[   919.330] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[   919.330] (II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 
-hsync +vsync (63.7 kHz)
[   919.330] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsyn
c -vsync (48.4 kHz)
[   919.330] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +v
sync (37.9 kHz)
[   919.330] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +v
sync (35.2 kHz)
[   919.330] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +v
sync (31.0 kHz)
[   919.330] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vs
ync (31.5 kHz)
[   919.330] (II) NOUVEAU(0): Output VGA-1 connected
[   919.330] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[   919.330] (II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768

```
So Nouveau sees the correct resolution among the probed modes but somehow fails to match it.  

How can I correct this?

---

### Post by pwabrahams on 2011-05-15
The problem, it seems, is that Nouveau has to be forced to use the right initial resolution.  After poking around in several forums using Google,
I found a way to force the right resolution.  Here's my **/etc/X11/xorg.conf** file:
```
Section "Monitor"
        Identifier      "VGA-1"
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
UseModes "1280x1024"
EndSection
Section "Screen"
Identifier "Default Screen"
Subsection "Display"
Modes "1280x1024" "1024x768"
EndSubSection

```
The Monitor section enables Nouveau to implement the 1280x1024 resolution but doesn't force Nouveau to use that resolution initially.  To force it to be used initially, the Screen section is needed.

All this has an air of magic about it.  It shouldn't be necessary, and it's almost impossible to discover this solution by reading documentation unless you're a video expert.

---

