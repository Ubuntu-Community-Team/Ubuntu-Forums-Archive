---
title: "[SOLVED] Upgraded to Hardy / Compiz Broken"
date: 2008-06-02
forum: Multimedia Software
---

### Post by emid on 2008-06-02
So I upgraded from Gutsy to Hardy.  I had some problems with getting the Nvidia driver working, but I finally got that fixed.  Now my problem is that I cannot get compiz running.  On Gutsy I had all this working with no problems.

I ran compiz-check and this is the output:

```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems..../compiz-check: line 402: [: 1024: unary operator expected
./compiz-check: line 402: [: 1280: unary operator expected
           [ OK ]


```

Any ideas?

---

### Post by Forlong on 2008-06-03
What happens, if you run ```
glxinfo
``` in the terminal?

---

### Post by emid on 2008-06-03
Here is what I get from glxinfo:

```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x7b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


```

---

### Post by emid on 2008-06-04
In case it helps, here is my xorg.conf:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916V"
	Horizsync	30.0-83.0
	Vertrefresh	55.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1400x1050@75"	"832x624@75"	"1600x1200@65"	"800x600@60"	"1600x1200@60"	"800x600@75"	"1792x1344@60"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Forlong on 2008-06-04
How did you install the nvidia driver?

Please also post the content of your **/var/log/Xorg.0.log**

---

### Post by emid on 2008-06-04
> **Forlong said:**
> How did you install the nvidia driver?

Please also post the content of your **/var/log/Xorg.0.log**

I think i installed the nvidia-glx-new drivers.  To be honest I did it several different ways (including downloading the driver from Nvidia's website), and at this point I cannot remember exactly which one was last.

Here is my Xorg.0.log file (It is pretty long):

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux d-desktop 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  3 19:55:03 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card f043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0391 card 1462,0452 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd3000000 - 0xd30fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GT] rev 161, Mem @ 0xd0000000/24, 0xc0000000/28, 0xd1000000/24, I/O @ 0xa000/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[1] -1	0	0xd3004000 - 0xd30047ff (0x800) MX[B]
	[2] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[3] -1	0	0xd3101000 - 0xd3101fff (0x1000) MX[B]
	[4] -1	0	0xd3102000 - 0xd3102fff (0x1000) MX[B]
	[5] -1	0	0xd3103000 - 0xd3103fff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xd3104000 - 0xd3104fff (0x1000) MX[B]
	[8] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[12] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[13] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[14] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[15] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[16] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[18] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[19] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[20] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[21] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[25] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[26] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[1] -1	0	0xd3004000 - 0xd30047ff (0x800) MX[B]
	[2] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[3] -1	0	0xd3101000 - 0xd3101fff (0x1000) MX[B]
	[4] -1	0	0xd3102000 - 0xd3102fff (0x1000) MX[B]
	[5] -1	0	0xd3103000 - 0xd3103fff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xd3104000 - 0xd3104fff (0x1000) MX[B]
	[8] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[12] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[13] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[14] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[15] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[16] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[18] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[19] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[20] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[21] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[25] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[26] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[5] -1	0	0xd3004000 - 0xd30047ff (0x800) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd3101000 - 0xd3101fff (0x1000) MX[B]
	[8] -1	0	0xd3102000 - 0xd3102fff (0x1000) MX[B]
	[9] -1	0	0xd3103000 - 0xd3103fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd3104000 - 0xd3104fff (0x1000) MX[B]
	[12] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[19] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[20] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[21] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[22] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[31] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[32] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000040gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:53:48 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[5] -1	0	0xd3004000 - 0xd30047ff (0x800) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd3101000 - 0xd3101fff (0x1000) MX[B]
	[8] -1	0	0xd3102000 - 0xd3102fff (0x1000) MX[B]
	[9] -1	0	0xd3103000 - 0xd3103fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd3104000 - 0xd3104fff (0x1000) MX[B]
	[12] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[19] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[20] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[21] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[22] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[31] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[32] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[5] -1	0	0xd3004000 - 0xd30047ff (0x800) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd3101000 - 0xd3101fff (0x1000) MX[B]
	[8] -1	0	0xd3102000 - 0xd3102fff (0x1000) MX[B]
	[9] -1	0	0xd3103000 - 0xd3103fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd3104000 - 0xd3104fff (0x1000) MX[B]
	[12] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.18.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     Acer AL1916 (DFP-1)
(--) NVIDIA(0): Acer AL1916 (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL1916 (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): No valid modes for "1400x1050@60"; removing.
(WW) NVIDIA(0): No valid modes for "1400x1050@75"; removing.
(WW) NVIDIA(0): No valid modes for "1600x1200@65"; removing.
(WW) NVIDIA(0): No valid modes for "1600x1200@60"; removing.
(WW) NVIDIA(0): No valid modes for "1792x1344@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024@75"
(II) NVIDIA(0):     "1280x960@60"
(II) NVIDIA(0):     "1152x864@75"
(II) NVIDIA(0):     "1280x1024@60"
(II) NVIDIA(0):     "1024x768@60"
(II) NVIDIA(0):     "1280x960@75"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "1024x768@75"
(II) NVIDIA(0):     "832x624@75"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "800x600@75"
(II) NVIDIA(0):     "800x600@72"
(II) NVIDIA(0):     "800x600@56"
(II) NVIDIA(0):     "640x480@75"
(II) NVIDIA(0):     "640x480@72"
(II) NVIDIA(0):     "640x480@60"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[5] -1	0	0xd3004000 - 0xd30047ff (0x800) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd3101000 - 0xd3101fff (0x1000) MX[B]
	[8] -1	0	0xd3102000 - 0xd3102fff (0x1000) MX[B]
	[9] -1	0	0xd3103000 - 0xd3103fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd3104000 - 0xd3104fff (0x1000) MX[B]
	[12] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1280x1024@75"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9

```

Thank you for taking the time to help, I really appreciate it.

---

### Post by Forlong on 2008-06-04
Your nvidia driver is obviously not properly installed.

Remove whatever you installed before and run this command in a terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot an try installing it again via *System &#8594; Administration &#8594; Hardware Drivers*

---

### Post by emid on 2008-06-04
Is there a specific command or series of commands to make sure that everything is properly removed?


Perhaps "sudo apt-get remove --purge nvidia*" or something to that effect.

---

### Post by Forlong on 2008-06-04
I'm sorry, I don't have a nvidia card, so I don't know.
Frankly, you should always keep track of what you do to your system for such cases.

---

### Post by emid on 2008-06-04
I did what you recommended.  The problem I have is that when I go to System -> Administration -> Hardware Drivers, there is nothing to choose from.  This is similar to when I first upgraded from Gutsy to Hardy (through the update-manager), which is why I installed the other drivers. :(

---

### Post by emid on 2008-06-04
I finally got it working.

I downloaded envy and used it to make sure that everything Nvidia driver related was uninstalled.

I then rebooted.

After restarting, I went back to the Nvidia website and downloaded the newest driver for my 7600GT card (NVIDIA-Linux-x86_64-173.14.05-pkg2.run).

I pressed CTRL-ALT-F2 (to get to the terminal).  Once in the terminal, I stopped GDM with:

```
sudo /etc/init.d/gdm stop
```

I made the new driver executable by typing (make sure you are in the same directory where the driver is located):

```
chmod +x NVIDIA-Linux-x86_64-173.14.05-pkg2.run
```

I then run the installer by:

```
sudo ./NVIDIA-Linux-x86_64-173.14.05-pkg2.run
```

I then restarted GDM:

```
sudo /etc/init.d/gdm start
```

Compiz has been restored! :) (at least for me)

---

