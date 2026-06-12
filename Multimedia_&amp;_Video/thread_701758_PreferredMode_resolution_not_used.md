---
title: "PreferredMode resolution not used"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by xyblor on 2008-02-19
How do I get X to start with the native resolution of my 1440x900@59.9 LCD? It always starts at 1024x768 instead.

I'm using "extended desktop" mode with two LCD's connected to my Radeon 8500: a 1440x900 through the DVI port, and a 1024x768 through the VGA port.

It's no problem for X to use the native resolution (1440x900) on my DVI monitor since that is detected and reported as the "preferred mode" by XRandR. Even just "xrandr --auto" sets it to the right mode.

Is X having trouble because I'm trying to use a non VESA-mode, or is it getting confused by the native mode reported by the primary display on VGA? Would installing the proprietary driver help this problem? I'm using "ati" now.

Incidentally, ctrl+alt+keypad_plus/minus doesn't do anything for me. Also, Gnome System->Preferences->Screen Resolution doesn't have any options higher than 1024x768.

Here's the log (Xorg.0.log) where you can see X detects the native mode, then chooses 1024x768 as the "initial mode" instead:

(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[etc...]
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Output VGA-0 using initial mode 1024x768
(II) RADEON(0): Output DVI-0 using initial mode 1024x768
after xf86InitialConfiguration


Here's the relevant part of my xorg.conf::

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"Monitor-VGA-0" "Monitor-VGA-0"
	Option		"Monitor-DVI-0" "Monitor-DVI-0"
EndSection

Section "Monitor"
	Identifier	"Monitor-VGA-0"
EndSection

Section "Monitor"
        Identifier	"Monitor-DVI-0"
	Option		"LeftOf" "Monitor-VGA-0"
# This commented stuff didn't help:
#	Option		"PreferredMode" "1440x900"
#	Modeline 	"1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
#	Option 		"PreferredMode" "1440x900_59.90"
#	Modeline 	"1440x900@59.90"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
#	Option 		"PreferredMode" "1440x900@59.90"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	DefaultDepth	24
	SubSection "Display"
	   Virtual 2464 900
	EndSubSection
EndSection

Thanks for any tips!

---

### Post by xyblor on 2008-03-02
According to someone on #xorg, there is a bug in the version of xserver that comes with Gutsy, whereby X tries to use the same resolution on both monitors if possible, regardless of preferred mode. This bug may have been fixed in Hardy's xserver, but I haven't tried it out of fear and laziness.

---

