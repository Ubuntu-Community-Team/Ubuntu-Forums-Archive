---
title: "Segfault after loading glx"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by Squishy on 2007-04-11
I am still having problems starting xorg (getting blank screen)

Now I have a new problem. Xorg segfaults after loading glx.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux zoidberg 2.6.20-14-generic #2 SMP Mon Apr 2 20:37:49 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 11 22:13:54 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0282 card 1043,80a3 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 1102,0002 card 1102,8026 rev 07 class 04,01,00 hdr 80
(II) PCI: 00:0d:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,810d rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 78 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,02e1 card 1682,2247 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xfbffffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf8ffffff (0x19000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7600 GS rev 162, Mem @ 0xfb000000/24, 0xe0000000/28, 0xfa000000/24, BIOS @ 0xf9f00000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[1] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[4] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[5] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[8] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[9] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[1] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[4] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[5] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[8] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[9] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
	[4] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[5] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so

```

Anyone know how to possibly fix this?

Running feisty and currently nvidia-glx-new ... same problem occurs on nvidia-glx

---

