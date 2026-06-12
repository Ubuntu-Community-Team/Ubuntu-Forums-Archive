---
title: "No 1080i with Nvidia 7800 GTX (Component)"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by adelodder on 2007-12-23
I have this very strange situation

I am unable to output higher resolutions than HD576i (720x576) on my secondary screen.  

No image is output on my screen when I setup xorg.conf for 1080i.  (1080i is working under Windows).  Still there is no relevant error in my xorg.0.log file.

Here is my setup:

Ubuntu 7.10 Gutsy Gibbon
NVidia 7800 GTX
Restricted drivers (100.14.19)
dongle
component cable
BenQ MP610 projector

here is my xorg.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux 4000BABA 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 23 18:18:53 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(**) RgbPath set to "/usr/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,04,85 hdr 00
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
(II) PCI: 01:00:0: chip 10de,0091 card 10de,02c2 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
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
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7800 GTX] rev 161, Mem @ 0xd0000000/24, 0xc0000000/28, 0xd1000000/24, I/O @ 0xa000/7, BIOS @ 0xd2000000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[1] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[2] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[3] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[6] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[7] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[12] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[13] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[14] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[15] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[25] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[1] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[2] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[3] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[6] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[7] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[12] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[13] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[14] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[15] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[25] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
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
	[4] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[5] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[6] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[7] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[10] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[19] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[20] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[21] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[30] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[31] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[5] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[6] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[7] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[10] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[19] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[20] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[21] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[30] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[31] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[5] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[6] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[7] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[10] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7800 GTX (G70) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.70.02.11.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GTX at PCI:1:0:0:
(--) NVIDIA(0):     FUS C19-3 (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): FUS C19-3 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[B](**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TVStandard" "HD1080i"
(**) NVIDIA(1): Option "UseEdidFreqs" "False"
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "TV: 1920x1080 +0+0"
(**) NVIDIA(1): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): TV Standard string: "HD1080i"
(**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(1):     disabled on all display devices.
(II) NVIDIA(1): NVIDIA GPU GeForce 7800 GTX (G70) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.70.02.11.01
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7800 GTX at PCI:1:0:0:
(--) NVIDIA(1):     FUS C19-3 (CRT-0)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): FUS C19-3 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Display Device found referenced in MetaMode: TV-0
(II) NVIDIA(1): Assigned Display Device: TV-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "TV:1920x1080+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.[/B]
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[8] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[9] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[10] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[13] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] 0	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[37] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[38] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[39] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[40] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Initialized GART.
(II) NVIDIA(1): Setting mode "TV:1920x1080+0+0"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
```

This is my xorg.conf file:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "FUS C19-3"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "BenQ"
    ModelName      "TV-0"
    HorizSync       31.0 - 82.0
    VertRefresh     48.0 - 85.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TVStandard" "HD1080i"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1920x1080 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option 	   "UseEdidFreqs" "False" 
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection

```
[B]
Things that didn't help me out:[/B]

installing latest drivers with envy --> same result.

adding following line to Screen1 section of xorg.conf:
   Option 	   "ModeValidation" "NoDFPNativeResolutionCheck, AllowNon60HzDFPModes, NoEdidMaxPClkCheck, NoMaxPClkCheck, NoHorizSyncCheck, NoVertRefreshCheck, NoEdidDFPMaxSizeCheck, NoEdidModes"  --> same result

---

### Post by adelodder on 2007-12-25
Eureka  :)

I reinstalled envy, I think the newest stable version is from 21 dec 2007.  It configured xorg.conf.  I changed it a bit for 720p output and for the first time I have a 1280x720 resolution.

I might try the 1080i configuration later, but for now I will stick to 720p.  It looks amazing.

Many thanks to Alberto Milone, tseliot.

---

