---
title: "Jaunty + FX5200Go + nouveau + Dual-Head"
date: 2009-04-28
forum: Multimedia Software
---

### Post by CHaoSlayeR on 2009-04-28
Hi there,

currently, I've got a little problem with my xrandr setup.

I have an old Dell Inspiron 8600 here which worked like a charm with the ppa-self-build-nouveau in Intrepid Ibex including error-free support for xrandr 1.2.

The display setup is as follows:

```

Screen 0: minimum 320 x 200, current 2880 x 1600, maximum 2880 x 1200                                                                                 
VGA-0 connected 1600x1200+0+400 (normal left inverted right x axis y axis) 396mm x 297mm                                                              
   1600x1200      85.0*+   75.0     70.0     65.0     60.0
...
LVDS-0 connected 1280x800+1600+400 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.1*+

```

The main problem is, that it corrupts my external monitor (VGA-0) in a way that parts of the screen get double-printed (the lower 800 pixel area is duplicated at the top).

Whenever I try to open the Display Settings in the KDE4.2 System Settings or when I try to correct the layout using xrandr, e.g.:
```

xrandr --output LVDS-0 --pos 1600x400

```

The X server gets killed and restarts into the login screen:
```

(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): Calling LVDS script 2:
(II) NOUVEAU(0): 0xDF52: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on lvds encoder (output 1)
(II) NOUVEAU(0): Calling LVDS script 5:
(II) NOUVEAU(0): 0xDE5A: Parsing digital output script table
(II) NOUVEAU(0): Output LVDS-0 is running on CRTC 1 using output A

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f24400]
3: /usr/lib/xorg/modules/drivers//nouveau_drv.so [0xb77f9f5b]
4: /usr/bin/X [0x817d1cb]
5: /usr/bin/X(BlockHandler+0x58) [0x80911c8]
6: /usr/bin/X(WaitForSomething+0x124) [0x8132974]
7: /usr/bin/X(Dispatch+0x7e) [0x808d2be]
8: /usr/bin/X(main+0x3bd) [0x80722ed]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7aef775]
10: /usr/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) PS/2 Mouse: Close

```

This "reset" only happened after I tried to force X into the right direction using the xorg.conf without success:

```

Section "ServerLayout"
	Identifier     "DualHead Layout"
	Screen      0  "primary screen" 0 0
EndSection

Section "Device"
	Identifier     "nVidia GeForce FX 5200 GO 64M"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX Go5200"
	BusID          "PCI:1:0:0"
	Driver         "nouveau"
	Option         "AccelMethod" "EXA"
	Option         "monitor-LVDS-0" "primary"
	Option         "monitor-VGA-0" "secondary"
#	Option         "Dualhead" "false"
#	Option         "MigrationHeuristic" "greedy"
#	Option         "UseEdidDpi"   "FALSE"
#	Option         "DPI"   "96 x 96"
EndSection

Section "Monitor"
	Identifier     "primary"
	VendorName     "Dell"
	ModelName      "LGP"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
	Option         "Position" "1600 400"
	Option         "PreferredMode" "1280x800"
EndSection

Section "Monitor"
	Identifier     "secondary"
	VendorName     "NEC"
	ModelName      "Multisync FE1250+"
	HorizSync       30.0 - 110.0
	VertRefresh     50.0 - 160.0
	Option         "LeftOf" "primary"
#	DisplaySize     401 303
	Option         "PreferredMode" "1600x1200"
EndSection

Section "Screen"
	Identifier     "primary screen"
	Device         "nVidia GeForce FX 5200 GO 64M"
	Monitor        "primary"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Virtual    2880 1200
#		Modes      "1280x800"# "1600x1200"
	EndSubSection
EndSection

Section "ServerFlags"
	Option         "AIGLX" "false"
	Option         "DontZap" "false"
#	Option         "Xinerama" "1"
EndSection

Section "Extensions"
	Option         "Composite" "Disable"
EndSection

Section "DRI"
	Mode           0666
EndSection

```

Thanx for any help,

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-04-29
Well, I just oversaw that the actual virtual size is not set to 2880x1200 as specified but 2880x1600 as I think RandR tries to *top-align* both monitors (which I thought I was denying using the "Position" option with 1600 400 in the xorg.conf).

Here's a screenshot of the full virtual screen:

[[IMG]http://www.chaoslayer.de/img/others/virtual_2880x1600_small.jpeg[/IMG]]("http://www.chaoslayer.de/img/others/virtual_2880x1600.jpeg")

So where get the randr settings stored? I didn't find any documentation about that.

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-04-29
OK, I am now nearly back as where I was before the upgrade:

I had to remove the **Position** option of the monitor so that randr does the wrong layout (top-align both monitors inside the virtual area). After login I can do an **xrandr --output LVDS-0 --pos 1600x400** (and this time without getting kicked out of X) to bottom-align the monitors.

But this way the settings don't get recognized and so I have to do that every time I log in. Finally here's the virtual screen directly after login:

[[IMG]http://www.chaoslayer.de/img/others/virtual_2880x1200_small.jpeg[/IMG]]("http://www.chaoslayer.de/img/others/virtual_2880x1200.jpeg")

And here is what I wanted it to be from the beginning (including login screen):

[[IMG]http://www.chaoslayer.de/img/others/virtual_2880x1200_corrected_small.jpeg[/IMG]]("http://www.chaoslayer.de/img/others/virtual_2880x1200_corrected.jpeg")

Is there any other way to force randr to use a specific position for a second monitor without extending the virtual size beyond the hard specified maximum (that seems to be what results in a lot of garbage on the screen)?

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-05-25
OK, just installed some newer driver builds from the well known [PPA for xorg crack pushers]("https://launchpad.net/~xorg-edgers/+archive/ppa").

Old version (still in Jaunty): 2.4.5-0ubuntu4
New version (PPA): 2.4.11+git20090519.f355ad89-0ubuntu0sarvatt~jaunty

Now it works like it did before in Intrepid.


Just for the record.

C]-[aoZ

---

