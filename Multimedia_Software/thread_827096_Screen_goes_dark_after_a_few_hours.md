---
title: "Screen goes dark after a few hours"
date: 2008-06-12
forum: Multimedia Software
---

### Post by ionFreeman on 2008-06-12
O...K. Every so often, my screen goes dark. I don't even know how to go about starting to troubleshoot this. Firefox 3 has been running every time this happened, and the first few times I was in the middle of a form submission. But, this last time (the only time after the last video driver upgrade) I was off in an rdesktop window. The rdesktop session was lost, by the way. Actually, this time was a little different -- yesterday the update manager fetched for me some updates. Before this, keystrokes did nothing after a screen darkening. This time, ctrl+alt+backspace successfully restarted Gnome.

It's been happening since I started messing with my Xorg.conf file to try to get my Samsung Syncmaster 204b to work. I've failed at that so far.

[This post]("http://ubuntuforums.org/showpost.php?p=4861680&postcount=2") suggests maybe somethis helpful's in /var/log/Xorg.0.log.old, so here it is.

This compaq nc4010 laptop has been through a number of Ubuntu versions.

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
Current Operating System: Linux kidege 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 11 12:35:52 2008
(==) Using config file: "/etc/X11/xorg.conf"
(++) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Ati Technologies Inc Radeon IGP 330M/340M/350M"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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
(II) PCI: 00:00:0: chip 1002,cbb2 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,7010 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10b9,5451 card 0e11,005a rev 02 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 0e11,005a rev 00 class 06,01,00 hdr 00
(II) PCI: 00:08:0: chip 10b9,5457 card 0e11,005a rev 00 class 07,03,00 hdr 00
(II) PCI: 00:09:0: chip 8086,4220 card 103c,12f5 rev 05 class 02,80,00 hdr 00
(II) PCI: 00:0b:0: chip 1217,7114 card 1801,0000 rev 20 class 06,07,00 hdr 82
(II) PCI: 00:0b:1: chip 1217,7114 card 3c01,0000 rev 20 class 06,07,00 hdr 82
(II) PCI: 00:0b:2: chip 1217,7110 card 0e11,005a rev 00 class 08,80,00 hdr 00
(II) PCI: 00:10:0: chip 10b9,5229 card 0e11,005a rev c4 class 01,01,ea hdr 00
(II) PCI: 00:11:0: chip 10b9,7101 card 0e11,005a rev 00 class 06,80,00 hdr 00
(II) PCI: 00:12:0: chip 1033,0035 card 0e11,005a rev 43 class 0c,03,10 hdr 80
(II) PCI: 00:12:1: chip 1033,0035 card 0e11,005a rev 43 class 0c,03,10 hdr 00
(II) PCI: 00:12:2: chip 1033,00e0 card 0e11,005a rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:13:0: chip 14e4,165d card 0e11,005a rev 03 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 1002,4337 card 0e11,005a rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x90000000 - 0x900fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[1] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x43ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (0:11:1), (0,6,9), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
	[1] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x4c000000 - 0x4fffffff (0x4000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x48000000 - 0x4bffffff (0x4000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon IGP 330M/340M/350M rev 0, Mem @ 0x98000000/27, 0x90000000/16, I/O @ 0x2000/8
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
(II) PCI Memory resource overlap reduced 0xa4000000 from 0xa7ffffff to 0xa3ffffff
(II) PCI Memory resource overlap reduced 0xa0500000 from 0xa0500fff to 0xa04fffff
(II) Active PCI resource ranges:
	[0] -1	0	0xa0000000 - 0xa000ffff (0x10000) MX[B]
	[1] -1	0	0xa0480000 - 0xa04800ff (0x100) MX[B]
	[2] -1	0	0xa0400000 - 0xa0400fff (0x1000) MX[B]
	[3] -1	0	0xa0380000 - 0xa0380fff (0x1000) MX[B]
	[4] -1	0	0xa0300000 - 0xa0300fff (0x1000) MX[B]
	[5] -1	0	0xa0180000 - 0xa0180fff (0x1000) MX[B]
	[6] -1	0	0xa0100000 - 0xa0100fff (0x1000) MX[B]
	[7] -1	0	0xa0080000 - 0xa0080fff (0x1000) MX[B]
	[8] -1	0	0xa0500000 - 0xa04fffff (0x0) MX[B]O
	[9] -1	0	0xa4000000 - 0xa3ffffff (0x0) MX[B]O
	[10] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[11] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[12] -1	0	0x00003800 - 0x0000380f (0x10) IX[B]
	[13] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xa0000000 - 0xa000ffff (0x10000) MX[B]
	[1] -1	0	0xa0480000 - 0xa04800ff (0x100) MX[B]
	[2] -1	0	0xa0400000 - 0xa0400fff (0x1000) MX[B]
	[3] -1	0	0xa0380000 - 0xa0380fff (0x1000) MX[B]
	[4] -1	0	0xa0300000 - 0xa0300fff (0x1000) MX[B]
	[5] -1	0	0xa0180000 - 0xa0180fff (0x1000) MX[B]
	[6] -1	0	0xa0100000 - 0xa0100fff (0x1000) MX[B]
	[7] -1	0	0xa0080000 - 0xa0080fff (0x1000) MX[B]
	[8] -1	0	0xa0500000 - 0xa04fffff (0x0) MX[B]O
	[9] -1	0	0xa4000000 - 0xa3ffffff (0x0) MX[B]O
	[10] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[11] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[12] -1	0	0x00003800 - 0x0000380f (0x10) IX[B]
	[13] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
	[4] -1	0	0xa0000000 - 0xa000ffff (0x10000) MX[B]
	[5] -1	0	0xa0480000 - 0xa04800ff (0x100) MX[B]
	[6] -1	0	0xa0400000 - 0xa0400fff (0x1000) MX[B]
	[7] -1	0	0xa0380000 - 0xa0380fff (0x1000) MX[B]
	[8] -1	0	0xa0300000 - 0xa0300fff (0x1000) MX[B]
	[9] -1	0	0xa0180000 - 0xa0180fff (0x1000) MX[B]
	[10] -1	0	0xa0100000 - 0xa0100fff (0x1000) MX[B]
	[11] -1	0	0xa0080000 - 0xa0080fff (0x1000) MX[B]
	[12] -1	0	0xa0500000 - 0xa04fffff (0x0) MX[B]O
	[13] -1	0	0xa4000000 - 0xa3ffffff (0x0) MX[B]O
	[14] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[15] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003800 - 0x0000380f (0x10) IX[B]
	[19] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.7.9-8 $
(II) v4l driver for Video4Linux
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:05:0
(--) Chipset ATI Radeon IGP330M/340M/350M (U2) 4337 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xa0000000 - 0xa000ffff (0x10000) MX[B]
	[5] -1	0	0xa0480000 - 0xa04800ff (0x100) MX[B]
	[6] -1	0	0xa0400000 - 0xa0400fff (0x1000) MX[B]
	[7] -1	0	0xa0380000 - 0xa0380fff (0x1000) MX[B]
	[8] -1	0	0xa0300000 - 0xa0300fff (0x1000) MX[B]
	[9] -1	0	0xa0180000 - 0xa0180fff (0x1000) MX[B]
	[10] -1	0	0xa0100000 - 0xa0100fff (0x1000) MX[B]
	[11] -1	0	0xa0080000 - 0xa0080fff (0x1000) MX[B]
	[12] -1	0	0xa0500000 - 0xa04fffff (0x0) MX[B]O
	[13] -1	0	0xa4000000 - 0xa3ffffff (0x0) MX[B]O
	[14] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[15] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003800 - 0x0000380f (0x10) IX[B]
	[19] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xa0000000 - 0xa000ffff (0x10000) MX[B]
	[5] -1	0	0xa0480000 - 0xa04800ff (0x100) MX[B]
	[6] -1	0	0xa0400000 - 0xa0400fff (0x1000) MX[B]
	[7] -1	0	0xa0380000 - 0xa0380fff (0x1000) MX[B]
	[8] -1	0	0xa0300000 - 0xa0300fff (0x1000) MX[B]
	[9] -1	0	0xa0180000 - 0xa0180fff (0x1000) MX[B]
	[10] -1	0	0xa0100000 - 0xa0100fff (0x1000) MX[B]
	[11] -1	0	0xa0080000 - 0xa0080fff (0x1000) MX[B]
	[12] -1	0	0xa0500000 - 0xa04fffff (0x0) MX[B]O
	[13] -1	0	0xa4000000 - 0xa3ffffff (0x0) MX[B]O
	[14] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[15] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00003800 - 0x0000380f (0x10) IX[B]
	[22] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x0000000090000000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPMode" "4"
(**) RADEON(0): Option "AGPFastWrite" "true"
(**) RADEON(0): Option "EnablePageFlip" "true"
(**) RADEON(0): Option "ColorTiling" "false"
(**) RADEON(0): Option "SubPixelOrder" "NONE"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon IGP330M/340M/350M (U2) 4337" (ChipID = 0x4337)
(--) RADEON(0): Linear framebuffer at 0x0000000098000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(**) RADEON(0): Page Flipping enabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 12000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 13300, sclk: 133.000000, mclk: 183.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=60 min=12000 max=35000; xclk=13300
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-2, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x0, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: 1024x768                
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 16, HSyncWidth: 136
VBlank: 38, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL PAL-M NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
finished output detect: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1600x1200
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (410, 310) mm
(**) RADEON(0): DPI set to (99, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x90000000 - 0x9000ffff (0x10000) MX[B]
	[1] 0	0	0x98000000 - 0x9fffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xa0000000 - 0xa000ffff (0x10000) MX[B]
	[7] -1	0	0xa0480000 - 0xa04800ff (0x100) MX[B]
	[8] -1	0	0xa0400000 - 0xa0400fff (0x1000) MX[B]
	[9] -1	0	0xa0380000 - 0xa0380fff (0x1000) MX[B]
	[10] -1	0	0xa0300000 - 0xa0300fff (0x1000) MX[B]
	[11] -1	0	0xa0180000 - 0xa0180fff (0x1000) MX[B]
	[12] -1	0	0xa0100000 - 0xa0100fff (0x1000) MX[B]
	[13] -1	0	0xa0080000 - 0xa0080fff (0x1000) MX[B]
	[14] -1	0	0xa0500000 - 0xa04fffff (0x0) MX[B]O
	[15] -1	0	0xa4000000 - 0xa3ffffff (0x0) MX[B]O
	[16] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[17] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00003800 - 0x0000380f (0x10) IX[B]
	[25] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[26] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit 98000000 0 0
(==) RADEON(0): Write-combining range (0x98000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 2
disable montype: 1
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1600,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1600,1202)
(II) RADEON(0): Largest offscreen area available: 1600 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0xf5a000
(II) RADEON(0): Will use depth buffer at offset 0x16ad000
(II) RADEON(0): Will use 34816 kb for textures at offset 0x1e00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0x98000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(**) RADEON(0): Using AGP 4x
(WW) RADEON(0): WARNING: Using the AGPFastWrite option is not recommended.
	This option does not provide much of a noticable speed boost, while it
	will probably hard lock your machine. All bets are off!
(**) RADEON(0): Enabling AGP Fast Writes.
(II) RADEON(0): [agp] Mode 0x0f000217 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xa4000000
(II) RADEON(0): [agp] Ring mapped at 0xb7918000
(II) RADEON(0): [agp] ring read ptr handle = 0xa4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7eec000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xa4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3653000
(II) RADEON(0): [agp] GART texture map handle = 0xa4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb3173000
(II) RADEON(0): [drm] register handle = 0x90000000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 162000000
best_freq: 162000000
best_feedback_div: 360
best_ref_div: 60
best_post_div: 1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 2
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 10
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x3fff3c00 is: 0x3fff3c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xa47fa400
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xa47fa400
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1204)
(II) RADEON(0): Largest offscreen area available: 1600 x 6983
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "DCCMode" is not used
(WW) RADEON(0): Option "LVDSBiosNativeMode" is not used
(--) RandR disabled
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
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 408 x 306
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 2
enable montype: 1
(II) RADEON(0): Damage tracking initialized for page flipping
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
disable montype: 1
disable montype: 5
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 65000000
best_freq: 65000000
best_feedback_div: 455
best_ref_div: 63
best_post_div: 3
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xa47fa400
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 5
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 1ad  Serial#: 1112683056
(II) RADEON(0): Year: 2005  Week: 50
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 162.0 MHz   Image Size:  408 x 306 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCHYC02141
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2dad0130325242
(II) RADEON(0): 	320f01030e291f782aee95a3544c9926
(II) RADEON(0): 	0f5054bfef80a94081808140714f0101
(II) RADEON(0): 	010101010101483f403062b0324040c0
(II) RADEON(0): 	130098321100001e000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484348594330323134310a20200083
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 429
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
enable montype: 2
enable montype: 1
disable montype: 2
disable montype: 1
disable montype: 1
disable montype: 2
enable montype: 2
enable montype: 1
enable montype: 1
enable montype: 2
SetGrabKeysState - enabled
disable montype: 2
disable montype: 1
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
finished PLL2
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf8b6e000 at 0xb7ac4000
(II) RADEON(0): [drm] Closed DRM master.
```
Here's /etc/X11/Xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
	Identifier	"Ati Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"true"
	Option		"EnablePageFlip"	"true"
	Option		"DCCMode"
	Option		"ColorTiling"		"false
	Option		"SubPixelOrder"		"NONE"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	Option		"LVDSBiosNativeMode"	"false"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Configured Monitor"
	DefaultDepth	24
EndSection

Section "Monitor"
  identifier "Samsung SyncMaster 204B"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
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
  # modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Desktop Screen"
  Device "Ati Technologies Inc Radeon IGP 330M/340M/350M"
  Monitor "Samsung SyncMaster 204B"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1600x1200@60" "1400x1050@60" "1280x1024@60" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "ServerFlags"
EndSection
```
And /etc/gdm/gdm.conf
```
# GDM System Defaults Configuration file.
#
# This file should not be updated by hand.  Since GDM 2.13.0.4, configuration
# choices in the GDM System Configuration file (/etc/gdm/gdm.conf) will
# override the default values specified in this file.
#
# If you were using an older version of GDM, your system may have the the older
# gdm.conf configuration file on the system.  If so, then this file is used
# instead of the GDM Custom Configuration file for backwards support.  If you
# make changes to the GDM Custom Configuration file and they seem to not be
# taking effect, this is likely the problem.  Consider migrating your
# configuration to the new configuration file and removing the gdm.conf file.
#
# You can use the gdmsetup program to graphically edit the gdm.conf-custom
# file.  Note that gdmsetup does not support every option in this file, just
# the most common ones that users want to change.  If you feel that gdmsetup
# should support additional configuration options, please file a bug report at
# http://bugzilla.gnome.org/.
#
# If you hand-edit the GDM configuration, you should run the following command
# to get the GDM daemon to recognize the change.  Any running GDM GUI programs
# will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run invoke-rc.d gdm reload or invoke-rc.d gdm restart
# to cause GDM to restart and re-read the new configuration settings. 
# You can also restart GDM by sending a HUP or USR1 signal to the
# daemon.  HUP behaves like restart and causes any user session
# started by GDM to exit immediately while USR1 behaves like
# reload and will wait until all users log out before
# restarting GDM.
#
# For full reference documentation see the GNOME help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Some values are commented out, but show their default values.  Lines
# that begin with "#" are considered comments.
#
# Have fun!

[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The GDM configuration program that is run from the login screen, you should
# probably leave this alone.
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you



# should leave this alone.
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for attached (non-xdmcp) logins.  Change gdmlogin to gdmgreeter
# to get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon separated GTK+ modules.
# This is useful for enabling additional feature support e.g. GNOME
# accessibility framework. Only "trusted" modules should be allowed to minimize
# security holes
#AddGtkModules=false
# By default, these are the accessibility modules.
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this value.
DefaultPath=/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this value.
RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
#AlwaysRestartServer=

# User and group used for running GDM GUI applications.  By default this is set
# to user "gdm" and group "gdm".  This user/group should have very limited
# permissions and access to only the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# does not always work, only if those clients have a window of their own.
#KillInitClients=true
LogDir=/var/log/gdm

# Note that a post login script is run before a PreSession script.  It is run
# after the login is successful and before any setup is run on behalf of the
# user.
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say VGA
# mode, allowing a login, could you please send it to me?
FailsafeXServer=/etc/gdm/failsafeXServer
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can run an X
# configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing

# System command support.
#
# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon.  GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted via gdm."
HaltCommand=/sbin/shutdown -h now "Shut Down via gdm."
SuspendCommand=/usr/sbin/pm-suspend
HibernateCommand=/usr/sbin/pm-hibernate

# The following options specify how GDM system commands are supported.
#
# Specify which actions are displayed in the greeter.  Valid values are HALT,
# REBOOT, HIBERNATE, SUSPEND, and CUSTOM_CMD separated by semicolons.
SystemCommandsInMenu=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD

# Specify which actions are supported by QUERY_LOGOUT_ACTION, SET_LOGOUT_ACTION
# and SET_SAFE_LOGOUT_ACTION.  Valid values are HALT, REBOOT, HIBERNATE, SUSPEND, and
# CUSTOM_CMD separated by semicolons.
AllowLogoutActions=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD

# This feature is only functional if GDM is compiled with RBAC (Role Based
# Access Control) support.
# Specify the RBAC key used to determine if the user has permission to use
# the action via QUERY_LOGOUT_ACTION, SET_LOGOUT_ACTION and
# SET_SAFE_LOGOUT_ACTION.  The GDM GUI will only display the action if the
# "gdm" user has RBAC permissions to use the action.  RBAC keys for multiple
# actions can be specified by separating them by semicolons.  The format for
# each is "Action:RBAC key".  If an action is not specified, it is assumed
# all users have permission for this action.  For example:
# HALT:key.for.halt,REBOOT:key.for.reboot,[...]  
RBACSystemCommandKeys=

# Probably should not touch the below this is the standard setup.
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal X
# session, but it shares a lot of stuff with that.  See the provided default
# for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live.  It is
# really a PATH style variable since 2.4.4.2 to allow actual interoperability
# with KDM.
SessionDesktopDir=/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/:/var/lib/menu-xdg/xsessions/:/etc/dm/Sessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this
# behavior.
UserAuthDir=
# Fallback directory for writing authorization file if user's home directory
# is not writable.
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is no
# activity and no one logged on.  Set to 0 to turn off the reaping.  Does not
# affect nested flexiservers.
#FlexiReapDelayMinutes=5

# The X nest command.
# Examples of valid commands (assuming installed to /usr/X11/bin:
# Xorg Xnest: /usr/X11/bin/Xnest -audit 0 -name Xnest
# Xsun Xnest: /usr/openwin/bin/Xnest -audit 0 -name Xnest -pn
# Xephyr:     /usr/X11/bin/Xephyr -audit 0
Xnest=/usr/share/gdm/gdmXnestWrapper -br -audit 0
# Xsun Xnest does not support font paths (passed into Xnest -fp argument)
# that include the ":unscaled" suffix after a path name.  Setting this to
# false will strip any ":unscaled" suffix from the font path.  If not 
# using this Xnest, the value should be true.
XnestUnscaledFontPath=true

# Automatic VT allocation.  Right now only works on Linux.  This way we force
# X to use specific vts.  Turn VTAllocation to false if this is causing
# problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change VT's
# on Linux and FreeBSD systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and switch VT's on
# Linux and FreeBSD systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before being
# prompted for password.  While this gives away some info on what users are on
# a system, it on the other hand should give the user an idea of when they
# logged in and if it doesn't seem kosher to them, they can just abort the
# login and contact the sysadmin (avoids running malicious startup scripts).
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used when there
# are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether GDM will honor requests DYNAMIC requests from the
# gdmdynamic command.
#DynamicXServers=false

# This determines whether GDM will send notifications to the console.
#ConsoleNotify=true

# How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=10

[security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
# Allow login as root via XDMCP.  This value will be overridden and set to
# false if the /etc/default/login file exists and contains
# "CONSOLE=/dev/login", and set to true if the /etc/default/login file exists
# and contains any other value or no value for CONSOLE.
AllowRemoteRoot=false
# This will allow remote timed login.
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions.
RelaxPermissions=1
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# If your HOME is managed by automounter, set to true
SupportAutomount=false
# Number of seconds to wait after a failed login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line, a
# good default to have (why is this a "negative" setting? because if it is
# false, you could still not allow it by setting command line of any particular
# server).  It's probably better to ship with this on since most users will not
# need this and it's more of a security risk then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do not add
# a "-nolisten tcp", as then the query just wouldn't work, so this setting only
# affects truly attached sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS by
# detecting "root-squashing".  It seems bad practice to place cookies on things
# that go over the network by default and thus we do not do it by default.
# Sometimes you can however use safe remote filesystems where this is OK and
# you may want to have the cookie in your home directory.
#NeverPlaceCookiesOnNFS=true
# Will cause PAM_DISALLOW_NULL_AUTHTOK to be passed as a flag to
# pam_authenticate and pam_acct_mgmt, disallowing NULL password.  This setting
# will only take effect if PAM is being used by GDM.  This value will be
# overridden with the value from /etc/default/login if it contains
# "PASSREQ=[YES|NO]"
#PasswordRequired=false
# Specifies the PAM Stack to use, "gdm" by default.
PamStack=gdm
# GDM allows configuration of how ut_line is set when it does utmp/wtmp and
# audit processing.  If VT is being used, then ut_line will be set to the
# device associated with the VT.  If the console is attached and has a device
# name specified in the [servers] section, then this value will be used.
# Otherwise the value is defaulted to the value specified in UtmpLineAttached
# for attached displays and UtmpLineRemote for remote displays.  The value
# can be left empty which means that ut_line will be set to an empty value
# (if not VT and no value specified in the [servers] section.  The values
# can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.  The values for both keys  must begin with
# "/dev/".
UtmpLineAttached=/dev/console
UtmpLineRemote=
# If true and the specified UtmpLineAttached or UtmpLineRemote does not exist,
# then create a pseudo-device filename that will be touched when the utmp
# record is updated.  Creating such a psuedo-device ensures that programs
# that stat the utmp device associated with ut_line such as finger, last,
# etc. work in a reasonable way.  
UtmpPseudoDevice=false

# XDMCP is the protocol that allows remote login.  If you want to log into GDM
# remotely (I'd never turn this on on open network, use ssh for such remote
# usage).  You can then run X with -query <thishost> to log in, or
# -indirect <thishost> to run a chooser.  Look for the 'Terminal' server type
# at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc that
# we need.  Unless you need a specific gtkrc that doesn't correspond to a
# specific theme, then just use the GtkTheme key.
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the GUI.
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does not yet
# have this ability.
#AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can also
# specify 'all' to allow all installed themes.  These should be just the
# basenames of the themes such as 'Thinice' or 'LowContrast'.
#GtkThemesToAllow=all

# Maximum size of an icon, larger icons are scaled down.
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# The following options for setting titlebar and setting window position are
# only useful for the standard login (gdmlogin) and are not used by the
# themed login (gdmgreeter).
#
# The standard login has a title bar that the user can move.
#TitleBar=true
# Don't allow user to move the standard login window.  Only makes sense if
# TitleBar is on.
#LockPosition=false
# Set a position for the standard login window rather then just centering the
# window.  If you enter negative values for the position it is taken as an
# offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

# Enable the Face browser.  Note that the Browser key is only used by the
# standard login (gdmlogin) program.  The Face Browser is enabled in
# the Graphical greeter by selecting a theme that includes the Face
# Browser, such as happygnome-list.  The other configuration values that
# affect the Face Browser (MinimalUID, DefaultFace, Include, Exclude,
# IncludeAll, GlobalFaceDir) are used by both the Standard and Themed
# greeter.
Browser=true
# The default picture in the browser.
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the face
# browser or in the gdmselection list for Automatic/Timed login.  They will not
# be displayed regardless of the settings for Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in the
# gdmsetup selection list for Automatic/Timed login.  Users should be separated
# by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from the
# gdmsetup selection list for Automatic/Timed login.  Excluded users will still
# be able to log in, but will have to type their username.  Users should be
# separated by commas.  
Exclude=nobody
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users will be
# displayed except users excluded via the Exclude setting and user ID's less
# than MinimalUID.  Scanning the password file can be slow on systems with
# large numbers of users and this feature should not be used in such
# environments.  The setting of IncludeAll does nothing if Include is set to a
# non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture.
#GlobalFaceDir=/usr/share/pixmaps/faces/

# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with GDM and edit it.  It is not a standard locale.alias
# file, although GDM will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter.
Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# Logo shown on file chooser button in gdmsetup (do not modify this value).
#ChooserButtonLogo=/usr/share/pixmaps/gdm-foot-logo.png
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true

# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however.
#SystemMenu=true
# Configuration is available from the system menu of the greeter.
ConfigAvailable=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user to
# connect to some remote host.  Local XDMCP does not need to be enabled,
# however.
#ChooserButton=true

# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome to
# "Welcome" and for DefaultWelcome to "Welcome to %n", and properly translate
# the message to the appropriate language.  Note that %n gets translated to the
# hostname of the machine.  These default values can be overridden by setting
# DefaultWelcome and/or DefaultRemoteWelcome to false, and setting the Welcome
# and DefaultWelcome values as desired.  Just make sure the strings are in
# utf-8 Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n

# Xinerama screen we use to display the greeter on.  Not for true multihead,
# currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
# The Standard greeter (gdmlogin) uses BackgroundColor as the background
# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor
# as the background color.
BackgroundColor=#dab082
GraphicalThemedColor=#dab082
# XDMCP session should only get a color, this is the sanest setting since you
# don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true

# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# If this is true then the background program is run always, otherwise it is
# only run when the BackgroundType is 0 (None).
#RunBackgroundProgramAlways=false
# Delay before starting background program
#BackgroundProgramInitialDelay=30
# Should the background program be restarted if it is exited.
#RestartBackgroundProgram=true
# Delay before restarting background program
#BackgroundProgramRestartDelay=30

# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode
# where the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
# Do not show any visible feedback in the password field. This is standard for
# instance in console, xdm and ssh.
#UseInvisibleInEntry=false

# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
#SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
# user successfully logs in.
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
# user fails to log in.
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# Specifies a program to be called by the greeter/login program when the
# initial screen is displayed.  The purpose is to provide a hook where files
# used after login can be preloaded to speed performance for the user. The
# program will only be called once only, the first time a greeter is displayed.
# The gdmprefetch command may be used.  This utility will load any libraries
# passed in on the command line, or if the argument starts with a "@"
# character, it will process the file assuming it is an ASCII file containing a
# list of libraries, one per line, and load each library in the file.
PreFetchProgram=/usr/lib/gdm/gdmprefetch @/etc/gdm/gdmprefetchlist

# The chooser is what's displayed when a user wants an indirect XDMCP session,
# or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts.
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png.
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are scanning
# actually, we continue to listen even after this has expired).
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to a
# query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer.
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced
# when officially registered xdmcp multicast address of TBD will be available.
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names.
#AllowAdd=true

[debug]
# This will cause GDM to send debugging information to the system log, which 
# will create a LOT of output.  It is not recommended to turn this on for
# normal use, but it can be useful to determine the cause when GDM is not
# working properly.
Enable=false
# This will enable debug messages for accessibilty gesture listeners into the
# syslog.  This includes output about key events, mouse button events, and
# pointer motion events.  This is useful for figuring out the cause of why the
# gesture listeners may not be working, but is too verbose for general debug.
Gestures=false

# Attached DISPLAY Configuration
#
[servers]
# This section defines which attached DISPLAYS should be started by GDM by
# default.  You can add as many DISPLAYS as desired and they will always be
# started.  The key for each entry must be a unique number that cooresponds to
# the DISPLAY number to start the X server.  For a typical single-display
# machine, there will only be one entry "0" for DISPLAY ":0".  The first word
# in the value corresponds to an X server definition in the "X Server
# Definitions" section of the configuration file.  For example, the entry:
#
# 0=Standard
#
# Means that DISPLAY ":0" will start an X server as defined in the 
# [server-Standard] section.
#
# The optional device argument is used to specify the device that is associated
# with the DISPLAY.  When using Virtual Terminals (VT), this value is ignored
# and GDM will use the correct device name associated with the VT.  If not
# using VT, then GDM will use the value specified by this optional argument.
# If the device argument is not defined, then GDM will use the default setting
# for attached displays defined in the UtmpLineAttached configuration option.
# For the main display (typically DISPLAY ":0"), "/dev/console" is a reasonable
# value.  For other displays it is probably best to not include this argument
# unless you know the specific device associated with the DISPLAY.  The device
# value can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.
#
0=Standard device=/dev/console

# Example of how to set up DISPLAY :1 to also use Standard.
#1=Standard

# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

# X Server Definitions
#
# Note: Is your X server not listening to TCP requests?  Refer to the 
# security/DisallowTCP setting!

[server-Standard] 
name=Standard server
command=/usr/bin/X -br -audit 0 -layout DefaultLayout
flexible=true

[server-Separate]
name=Separate Heads
command=/usr/bin/X -br -audit 0 -layout SeparateHeads
flexible=true

[server-Clone]
name=Clone Heads
command=/usr/bin/X -br -audit 0 -layout CloneHeads
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params anyway,
# and terminate would be bad for xdmcp choosing).  You can make a terminal
# server flexible, but not with an indirect query.  If you need flexible
# indirect query server, then you must get rid of the -terminate and the only
# way to kill the flexible server will then be by Ctrl-Alt-Backspace.
flexible=false
# Do not handle this X server for attached displays.
handled=false

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Chooser]
name=Chooser server
command=/usr/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you wish to
# allow a chooser server then make this true.  This is the only way to make a
# flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a machine they
# will get this same server but run with "-terminate -query hostname".
chooser=true

[customcommand]
# This section allows you specify up to 10 custom commands. Each of the
# commands can be defined by the seven parameters listed below. In each of the
# descriptions of the parameters N can take on any values between 0 and 9,
# i.e. CustomCommand0=,CustomCommand1=,...,CustomCommand9=.  The  numbers
# can have gaps as long as they fit within predefined set of 10, and their
# placement order within this section and with respect to each other is
# not important.
#
# CustomCommandN, CustomCommandTextN, CustomCommandLabelN, 
# CustomCommandLRLabelN, CustomCommandTooltipN, CustomCommandIsPersistentN
# and CustomCommandNoRestartN should all be defined for a given integer N, 
# where N can be a number from 0-9 (if not the default values will be 
# assigned except CustomCommandN for which no default exists).

# Custom command to run.  Multiple commands may be specified separated by 
# semicolons.  GDM will use the first valid command.  Examples:
# /sbin/bootwindoze;/usr/bin/bootwindoze, or
# /sbin/runupdate;/usr/local/sbin/runupdate
#
#CustomCommandN=

# Custom command dialog message that will appear on all warning dialogs.
# This will vary depending on what you want to do. Examples:
# Are you sure you want to restart system into Windoze?, or
# Are you sure you want do do this?
#CustomCommandTextN=

# Custom command label that will appear as stock label on buttons/menu items.
# This option can't contain any semicolon characters (i.e. ";").
# Examples:
# _Windoze, or
# _Update Me
#CustomCommandLabelN=

# Custom command label that will appear as stock label on radio buttons/list
# items.  The underscore indicates the mnemonic used with this item.  Examples:
#   Restart into _Windoze
#   Perform system _Update
#CustomCommandLRLabelN=

# Custom command tooltip. Examples
# Restarts the computer into Windoze
# Updates the computer software to the most recent version(s)
#CustomCommandTooltipN=

# Custom command persistence option. Setting it to true will allow this
# command to appear outside the login manager, e.g. on the desktop through 
# Log Out/Shut Down dialogs. The default value is false.
#CustomCommandIsPersistentN=

# Custom command gdm/system restart option. Setting it to true will not
# restart gdm after command execution.  The default commands (reboot, shut
# down) all reboot the system by default which is why the default setting
# is true.
# In addition when corresponding CustomCommandIsPersistentN option is set to
# true, setting CustomCommandNoRestartN to false will place CustomCommandN
# in the Shut Down dialog set of actions, setting it to true will place
# CustomCommandN in the Log Out dialog set of actions.
#CustomCommandNoRestartN=
#
# Example layout for more than one command:
#CustomCommand0=
#CustomCommandText0=
#CustomCommandLabel0=
#CustomCommandLRLabel0=
#CustomCommandTooltip0=
#CustomCommandIsPersistent0=
#CustomCommandNoRestart0=
#
#CustomCommand1=
#CustomCommandText1=
#CustomCommandLabel1=
#CustomCommandLRLabel1=
#CustomCommandTooltip1=
#CustomCommandIsPersistent1=
#CustomCommandNoRestart1=
#
# and so on
```
And, finally, the output of lspci```

00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 USB Controller: NEC Corporation USB (rev 43)
00:12.1 USB Controller: NEC Corporation USB (rev 43)
00:12.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:13.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 03)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
```

---

### Post by Yondergod22 on 2008-06-12
that happens to me all the time, its when its loading or something...

---

### Post by ionFreeman on 2008-06-12
> **Yondergod22 said:**
> that happens to me all the time, its when its loading or something...

I suspect it's not by design. Anyway, I suspect yesterday's update (following hard on the heels of the previous day's kernel update, which may have started the problem) fixed it, and I just panicked today when the screen had a totally normal blackening in response to a lack of user input, which is why I could restart X from the keyboard.

I'm waiting for recurrence, but we could try to fix your problem....

---

### Post by ionFreeman on 2008-06-12
yay! I got recurrence! I'm the luckiest boy in the world!
This is definitely pathological. Ctrl+Alt+Backspace does restart X, but nothing else gets me my display back. I've switched to Opera for the time being. Still nothing particularly suspicious in Xorg.0.log.old. What can I check?

---

### Post by Yondergod22 on 2008-06-12
it doesn't really bother me. but maybe it worse for you, for me it just gets a little bit dark for a few seconds.

---

### Post by ionFreeman on 2008-06-12
Ah. Yeah. With me, it stays dark.

---

