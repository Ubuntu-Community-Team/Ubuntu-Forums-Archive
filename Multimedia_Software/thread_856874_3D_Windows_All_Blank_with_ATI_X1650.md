---
title: "3D Windows All Blank with ATI X1650"
date: 2008-07-11
forum: Multimedia Software
---

### Post by MusicallyInspired on 2008-07-11
After much toil and trouble I finally managed to get the fglrx driver working after figuring out how to up my AGP aperture size in my BIOS. I've got an ATI X1650 Pro AGP card running on a Pentium 4 2.5 GHz with 768 MB RAM. Right now I'm using the fglrx driver installed through envyng. Fglxinfo gives me all the correct information (ATI not mesagl or whatever). I'm using Ubuntu Hardy (love it!). Everything's updated and I've followed all the instructions I could find on customizing xorg.conf. I've searched the forums and Google and can't find a remedy for my problem.

Whenever I run glxgears, fgl_glxgears, and OpenGL screensaver, or anything 3D related I get a black window and nothing more. They all work, though. I just can't see them. Glxgears and fgl_glxgears still spit out framerates above 1000 and I can quit the programs without incident. Also enhanced compiz desktop effects aren't visible either. However, before when I used to get just a white screen after enabling it, now after I have the driver working properly everything disappears but my background image. The screen doesn't turn white.

Any help would be greatly appreciated. I'm very close to not having to use WinXP for games anymore and I'd hate to quit after coming this far.

My config and log files if they're needed:

xorg.conf:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "UseFastTLS" "1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "enable"
EndSection


```

xorg.0.log:
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux ariana 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 11 20:29:19 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
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
(II) PCI: 00:00:0: chip 1039,0650 card 1039,0650 rev 80 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0962 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1458,5002 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1458,a002 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1458,5004 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1458,5004 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1458,5004 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1458,e000 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 105a,6269 card 105a,4d68 rev 02 class 01,04,85 hdr 00
(II) PCI: 00:0d:0: chip 1102,0004 card 1102,2002 rev 04 class 04,01,00 hdr 80
(II) PCI: 00:0d:1: chip 1102,7003 card 1102,0040 rev 04 class 09,80,00 hdr 80
(II) PCI: 00:0d:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 01:00:0: chip 1002,71c1 card 1002,235a rev 9e class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e1 card 1002,235b rev 9e class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x71c1) rev 158, Mem @ 0xd0000000/28, 0xe1000000/16, I/O @ 0x9000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x71e1) rev 158, Mem @ 0xe1010000/16
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[1] -1	0	0xe3017000 - 0xe30177ff (0x800) MX[B]
	[2] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[3] -1	0	0xe3014000 - 0xe3014fff (0x1000) MX[B]
	[4] -1	0	0xe3018000 - 0xe3018fff (0x1000) MX[B]
	[5] -1	0	0xe3016000 - 0xe3016fff (0x1000) MX[B]
	[6] -1	0	0xe3015000 - 0xe3015fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[8] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[9] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[1] -1	0	0xe3017000 - 0xe30177ff (0x800) MX[B]
	[2] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[3] -1	0	0xe3014000 - 0xe3014fff (0x1000) MX[B]
	[4] -1	0	0xe3018000 - 0xe3018fff (0x1000) MX[B]
	[5] -1	0	0xe3016000 - 0xe3016fff (0x1000) MX[B]
	[6] -1	0	0xe3015000 - 0xe3015fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[8] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[9] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[4] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[5] -1	0	0xe3017000 - 0xe30177ff (0x800) MX[B]
	[6] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[7] -1	0	0xe3014000 - 0xe3014fff (0x1000) MX[B]
	[8] -1	0	0xe3018000 - 0xe3018fff (0x1000) MX[B]
	[9] -1	0	0xe3016000 - 0xe3016fff (0x1000) MX[B]
	[10] -1	0	0xe3015000 - 0xe3015fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[12] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[13] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[25] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.476                    
(II) ATI Proprietary Linux Driver Build Date: Mar 29 2008 00:05:22
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[5] -1	0	0xe3017000 - 0xe30177ff (0x800) MX[B]
	[6] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[7] -1	0	0xe3014000 - 0xe3014fff (0x1000) MX[B]
	[8] -1	0	0xe3018000 - 0xe3018fff (0x1000) MX[B]
	[9] -1	0	0xe3016000 - 0xe3016fff (0x1000) MX[B]
	[10] -1	0	0xe3015000 - 0xe3015fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[12] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[13] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[25] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c660
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[5] -1	0	0xe3017000 - 0xe30177ff (0x800) MX[B]
	[6] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[7] -1	0	0xe3014000 - 0xe3014fff (0x1000) MX[B]
	[8] -1	0	0xe3018000 - 0xe3018fff (0x1000) MX[B]
	[9] -1	0	0xe3016000 - 0xe3016fff (0x1000) MX[B]
	[10] -1	0	0xe3015000 - 0xe3015fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[12] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[13] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[29] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "on"
(**) fglrx(0): Option "VideoOverlay" "off"
(**) fglrx(0): Option "UseFastTLS" "1"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "Radeon X1650 Series" (Chipset = 0x71c1)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x235a)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV535
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SYL  Model: 123  Serial#: 16843009
(II) fglrx(0): Year: 1999  Week: 44
(II) fglrx(0): EDID Version: 1.1
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 35  vert.: 27
(II) fglrx(0): Gamma: 2.80
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.630 redY: 0.340   greenX: 0.280 greenY: 0.601
(II) fglrx(0): blueX: 0.145 blueY: 0.061   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #5: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): Monitor name: Sylvania F89
(II) fglrx(0): Monitor name: 
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 95 kHz, PixClock max 200 MHz
(II) fglrx(0): Serial No: KNAY4414653
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004f2c230101010101
(II) fglrx(0): 	2c0901010c231bb4e84f29a157479925
(II) fglrx(0): 	0f484ca46300714fa94f315945596159
(II) fglrx(0): 	819901010101000000fc0053796c7661
(II) fglrx(0): 	6e6961204638390a000000fc000a2020
(II) fglrx(0): 	20202020202020202020000000fd0032
(II) fglrx(0): 	a01e5f14000a202020202020000000ff
(II) fglrx(0): 	004b4e4159343431343635330a2000d4
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 594/395MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): OpenGL Overlay enabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 56 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 (93.8 kHz)
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 (91.1 kHz)
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync (43.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 +hsync (91.5 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"x100.0  113.30  1024 1096 1208 1392  768 769 772 814 +hsync (81.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"x90.0  100.18  1024 1088 1200 1376  768 769 772 809 +hsync (72.8 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"x120.0   83.94  800 856 944 1088  600 601 604 643 +hsync (77.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"x160.0   72.85  640 680 752 864  480 481 484 527 +hsync (84.3 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (350, 270) mm
(--) fglrx(0): DPI set to (116, 112)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 (93.8 kHz)
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 (91.1 kHz)
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync (43.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 +hsync (91.5 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)


(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"x100.0  113.30  1024 1096 1208 1392  768 769 772 814 +hsync (81.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"x90.0  100.18  1024 1088 1200 1376  768 769 772 809 +hsync (72.8 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"x120.0   83.94  800 856 944 1088  600 601 604 643 +hsync (77.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"x160.0   72.85  640 680 752 864  480 481 484 527 +hsync (84.3 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x1039/0x0650
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000, MCAGPSize = 0x10000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [pcie] 262144 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=1
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe1000000 - 0xe100ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[7] -1	0	0xe3017000 - 0xe30177ff (0x800) MX[B]
	[8] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[9] -1	0	0xe3014000 - 0xe3014fff (0x1000) MX[B]
	[10] -1	0	0xe3018000 - 0xe3018fff (0x1000) MX[B]
	[11] -1	0	0xe3016000 - 0xe3016fff (0x1000) MX[B]
	[12] -1	0	0xe3015000 - 0xe3015fff (0x1000) MX[B]
	[13] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[14] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[15] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[31] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[35] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x6c000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [drm] installed DRM signal handler
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.47.3
(II) fglrx(0):     Date: Mar 29 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x0006e000
(II) fglrx(0): Interrupt handler installed at IRQ 21.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc1100000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,2624)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 1424
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		9 256x256 slots
		4 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 10000000
...dwIRQEnableId: 00000008
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(WW) AIGLX: 3D driver claims to not support visual 0x73
(WW) AIGLX: 3D driver claims to not support visual 0x74
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
Receive 3D performance mode message with status: 00000001
Receive 3D performance mode message with status: 00000000
Receive 3D performance mode message with status: 00000001
Receive 3D performance mode message with status: 00000000
Receive 3D performance mode message with status: 00000001
Receive 3D performance mode message with status: 00000000
(II) 3rd Button detected: disabling emulate3Button

```

glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7415 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x47 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x73 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x74 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x87 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon


```

---

### Post by Melcar on 2008-07-12
What's the "UseFastTLS" option?  Did you add that or did the driver configure xorg.conf like that?  Try turning it off (or just delete it) and see if anything changes.

---

### Post by Sidzone on 2008-07-12
I'm a newbie who's been forcing myself to learn this thing called Linux for the past couple of years, but hopefully what I just discovered will be valuable to you and some of the others who don't speak geek yet.

My custom built notebook doesn't have the right graphics card imbedded on the mother board, and much like you, I got stuck with an all white desktop and 'bout went bannanas.  I finally resulted in turning the thing (power button) and after it rebooted selected to login in the Gnome Failsafe mode.  Whatever that move must've done must've been the trick, because at first I got a small white box in the upper left corner of my desktop and then the rest of the desktop came onboard.  After doing this, I opened Synaptic to get any updates that may have been important and restarted the computer properly.  After reaching the login page, I took a chance and logged in via the Gnome setting and voila! It opened.  The first few times I did this (after the afore mentioned experiment) I saw that same white box on the desktop which turned out to be the Terminal.  

My next lucky find was in trying to set my desktop settings to be more enhanced (like the 3-D cube desktop thing and trailing curser) because I know it all worked prior to my upgrade from Ubuntu 8 (Feisty) to Ubuntu Studio.  I discovered that there's a chance some graphic cards can't handle the load of processing the premium graphic toys while supporting the Studio suite.  I'm still hacking away at it, but I noticed that compiz (that 3-D desktop gadget) was available to flip the desktop around but each side was plain white on the desktop.

So, try doing a restart and login under the failsafe mode to Gnome (if you're Terminal saavy use the Terminal Failsafe), then complete the login and do your updates from there; you should be good. I hope that this helps; it's my first time ever being able to contribute to a Linux forum.  

Rock-on dude,

Sidzone

---

### Post by MusicallyInspired on 2008-07-12
> **Melcar said:**
> What's the "UseFastTLS" option?  Did you add that or did the driver configure xorg.conf like that?  Try turning it off (or just delete it) and see if anything changes.

I read online somewhere that one should add that. Anyway, I've removed it and still no change.

And Sidzone, I appreciate your enthusiasm to help but none of what you said is the same problem that I have. Actually I said I don't get the white desktop with compiz anymore. I just see my background instead. I'll try it anyway, though.

---

### Post by Melcar on 2008-07-12
> **MusicallyInspired said:**
> I read online somewhere that one should add that. Anyway, I've removed it and still no change.

...


When it comes to the fglrx driver, the end user needs to do very little configuration to it.  All the supported options (like VideoOverlay, TexturedVideo) are either on or off by default, depending on your card.  If someone tells you to add something in order to enable or disable an option, chances are those configurations are beta and still in testing, therefore you should use those with care.
Anyway, your problem sounds like a rendering issue.  Try playing around with the Compiz options, like turning off mipmaps (those do not render correctly on some cards with fglrx).

---

### Post by MusicallyInspired on 2008-07-12
Ok I'll try that. But how do I solve my problem for other 3D applications like games and glxgears?

---

### Post by Melcar on 2008-07-12
Try running them without Compiz on.

---

### Post by MusicallyInspired on 2008-07-12
I can't have Compiz on anyway or else I can't see any icons, windows, or anything but my background. I'm already running them without Compiz on.

---

### Post by MusicallyInspired on 2008-07-14
Nobody has any other ideas? Nobody else has the same problem?

---

### Post by markbuntu on 2008-07-14
try this line in a terminal:

compiz --replace

It will reload compiz and might get it to work properly. If you get an error like command not found or something try:

sudo compiz --replace


Also, there are a number of tweaks that may help you. They are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

If you want to install the latest 8.6 driver from ati, follow the directions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use Method 2. Read the directions all the way through before doing anything and follow them exactly.

good luck. and let us know if that works out for you and mark this thread as solved if it does using the thread tools.

---

### Post by MusicallyInspired on 2008-07-14
Compiz -replace just gave me a blank desktop again with just my background and cursour visible. Basically the same thing as enabling it in the Appearance application. I've already tried method 2 on that website and it does the same thing.

I should reiterate that my problem is not a compiz problem. I don't really care if compiz works or not. I'm trying to get my 3D applications (glxgears and 3D games) to work. I only said what happens with compiz because it uses 3D.

---

### Post by MusicallyInspired on 2008-07-16
Still desperate without a solution...are there other places I could maybe go to get some help regarding the fglrx driver?

---

### Post by markbuntu on 2008-07-16
Have you tried logging in in gnome safe mode?

---

### Post by MusicallyInspired on 2008-07-16
Yes. No change.

---

### Post by markbuntu on 2008-07-16
Try some of the suggestions here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

It may be a VideoOverlay issue or and OpenGl problem.

Also, you may want to get the latest ATI driver which is 8.6. There are directions here for installing it:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use method 2 and follow the directions very carefully.

Others have mentioned that the Radeon driver works better for them with this card. I am not familiar with that but you could try a google search and see if it meets your needs.

---

### Post by MusicallyInspired on 2008-07-17
I've done everything on that first site and I must have installed that 8.6 driver using method 2 fifty times now. It's what I'm currently running on actually. But I shall try agsin. I've done tons of research before I posted my problem and I've yet to find somebody with the same problem as I have that isn't using openSuse.

I do appreciate this help,  though. This must be the single most annoying graphics bug I've ever seen. Next time I get a nVidia card! lol

---

### Post by markbuntu on 2008-07-17
I have seen on some other threads that people are having more luck with the Radeon driver with that particular card family. Perahaps you should do a search for some of those threads and see what they did.

---

### Post by MusicallyInspired on 2009-01-22
I should point out that this problem seems to have solved itself after upgrading to Ubuntu Intrepid. Suddenly it worked perfectly without any flaws. I really don't know why it suddenly works in Intrepid and just WOULD NOT work in Hardy. I'm glad it does, though. Hopefully upgrading will solve the same problems for everybody else with this problem.

---

