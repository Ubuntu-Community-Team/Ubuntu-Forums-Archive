---
title: "problem with install ati driver"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by dongmh on 2006-07-18
hi
i`m sorry my english is not very well
my problem is fglrz don't work
when i use
```
sudo aticonfig --init
```
then i can't startx
i try ati.com`s ati-driver-installer-8.26.18 but it is not work too
my error code follow :
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux outlands 2.6.15-26-amd64-generic #1 SMP PREEMPT Fri Jul 7 19:25:13 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 19 04:55:12 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Laptop LCD"
(**) |   |-->Device "ATI Technologies, Inc. ATI MOBILITY RADEON X1300 (M52 7149)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 1025,009f rev 10 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,5a36 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 1002,4379 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 1025,009f rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1025,009f rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1025,009f rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1025,009f rev 83 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1025,009f rev 80 class 01,01,82 hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 1025,009f rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 1025,009f rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,7149 card 1025,009f rev 00 class 03,00,00 hdr 00
(II) PCI: 06:00:0: chip 1106,3044 card 1025,009f rev c0 class 0c,00,10 hdr 00
(II) PCI: 06:01:0: chip 10ec,8169 card 1025,009f rev 10 class 02,00,00 hdr 00
(II) PCI: 06:04:0: chip 1524,1412 card a800,0000 rev 10 class 06,07,00 hdr 82
(II) PCI: 06:04:1: chip 1524,0530 card 1025,009f rev 01 class 05,01,00 hdr 80
(II) PCI: 06:04:2: chip 1524,0550 card 1025,009f rev 01 class 08,05,01 hdr 80
(II) PCI: 06:04:3: chip 1524,0520 card 1025,009f rev 01 class 05,01,00 hdr 80
(II) PCI: 06:04:4: chip 1524,0551 card 1025,009f rev 01 class 05,01,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:5:0), (0,4,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:20:4), (0,6,10), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x52ffffff (0x3000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:4:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[1] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x7149) rev 0, Mem @ 0xc8000000/27, 0xc0100000/16, I/O @ 0x9000/8
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
	[0] -1	0	0xc0202400 - 0xc020247f (0x80) MX[B]
	[1] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[2] -1	0	0xc0200c00 - 0xc0200c7f (0x80) MX[B]
	[3] -1	0	0xc0200800 - 0xc02008ff (0x100) MX[B]
	[4] -1	0	0xc0200000 - 0xc02007ff (0x800) MX[B]
	[5] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[6] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[7] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[10] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[11] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[14] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[15] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[16] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[23] -1	0	0x00008438 - 0x5300843f (0x53000008) IX[B]
	[24] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[25] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xc0200900 - 0xc02009ff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0202400 - 0xc020247f (0x80) MX[B]
	[1] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[2] -1	0	0xc0200c00 - 0xc0200c7f (0x80) MX[B]
	[3] -1	0	0xc0200800 - 0xc02008ff (0x100) MX[B]
	[4] -1	0	0xc0200000 - 0xc02007ff (0x800) MX[B]
	[5] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[6] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[7] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[10] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[11] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[14] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[15] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[16] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[23] -1	0	0x00008438 - 0x5300843f (0x53000008) IX[B]
	[24] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[25] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0200900 - 0xc02009ff (0x100) MX[B]
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
	[4] -1	0	0xc0202400 - 0xc020247f (0x80) MX[B]
	[5] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[6] -1	0	0xc0200c00 - 0xc0200c7f (0x80) MX[B]
	[7] -1	0	0xc0200800 - 0xc02008ff (0x100) MX[B]
	[8] -1	0	0xc0200000 - 0xc02007ff (0x800) MX[B]
	[9] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[10] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[11] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[12] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[13] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[14] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[15] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[16] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[17] -1	0	0xc0200900 - 0xc02009ff (0x100) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[22] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[30] -1	0	0x00008438 - 0x5300843f (0x53000008) IX[B]
	[31] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[32] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[33] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9000 (RV280 5962),
	RADEON 9200 SE (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), RADEON X850 XT (R480 5D52),
	RADEON X850 (R481 4B48), RADEON X850 XT (R481 4B49),
	RADEON X850 SE (R481 4B4A), RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 XT (R520 7108),
	RADEON X1800 PRO (R520 7109), RADEON X1800 SE (R520 710A),
	RADEON X1800 (R520 710B), RADEON X1800 (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 (RV505 715F), RADEON X1300 XT (RV515 7140),
	RADEON X1300 PRO (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 LE (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 SE (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 VE (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1300 (RV516 7183), RADEON X1300 (RV516 7187),
	RADEON X1900 (R580 7240), RADEON X1900 (R580 7243),
	RADEON X1900 (R580 7244), RADEON X1900 (R580 7245),
	RADEON X1900 (R580 7246), RADEON X1900 (R580 7247),
	RADEON X1900 (R580 7248), RADEON X1900 (R580 7249),
	RADEON X1900 (R580 724A), RADEON X1900 (R580 724B),
	RADEON X1900 (R580 724C), RADEON X1900 (R580 724D),
	RADEON X1900 (R580 724E), RADEON X1900 (R580 724F),
	RADEON X1600 XT (RV530 71C0), RADEON X1600 PRO (RV530 71C2),
	MOBILITY FireGL V5200 (M56 71C4), MOBILITY RADEON X1600 (M56 71C5),
	RADEON (RV530 LE 71C6), RADEON (RV530 VE 71CE),
	FireGL V3400 (RV530 71D2), FireGL V5200 (RV530 71DA),
	RADEON (RV530 SE 71DE)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1                           
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:58:41
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-x86_64-268237
(--) Chipset MOBILITY RADEON X1300 (M52 7149) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202400 - 0xc020247f (0x80) MX[B]
	[5] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[6] -1	0	0xc0200c00 - 0xc0200c7f (0x80) MX[B]
	[7] -1	0	0xc0200800 - 0xc02008ff (0x100) MX[B]
	[8] -1	0	0xc0200000 - 0xc02007ff (0x800) MX[B]
	[9] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[10] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[11] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[12] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[13] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[14] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[15] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[16] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[17] -1	0	0xc0200900 - 0xc02009ff (0x100) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[22] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[30] -1	0	0x00008438 - 0x5300843f (0x53000008) IX[B]
	[31] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[32] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[33] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x6cb7e0
(WW) ****INVALID IO ALLOCATION**** b: 0x9000 e: 0x90ff correcting
(II) window:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) resSize:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) IX[B]
(II) window fixed:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
Requesting insufficient memory window!: start: 0x9000 end: 0x90ff size 0xc0120100
Requesting insufficient memory window!: start: 0x9400 end: 0x94ff size 0xc0120100
Requesting insufficient memory window!: start: 0x9800 end: 0x98ff size 0xc0120100
Requesting insufficient memory window!: start: 0x9c00 end: 0x9cff size 0xc0120100
(EE) Cannot find a replacement memory range
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202400 - 0xc020247f (0x80) MX[B]
	[5] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[6] -1	0	0xc0200c00 - 0xc0200c7f (0x80) MX[B]
	[7] -1	0	0xc0200800 - 0xc02008ff (0x100) MX[B]
	[8] -1	0	0xc0200000 - 0xc02007ff (0x800) MX[B]
	[9] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[10] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[11] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[12] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[13] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[14] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[15] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[16] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[17] -1	0	0xc0200900 - 0xc02009ff (0x100) MX[B]
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[25] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[31] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[32] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[33] -1	0	0x00008438 - 0x5300843f (0x53000008) IX[B]
	[34] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[35] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[36] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[37] 0	0	0xc01203b0 - 0xc01203bb (0xc) IS[B]
	[38] 0	0	0xc01203c0 - 0xc01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 0 func 0
(EE) fglrx(0): RegisterResources failed
SetVBEMode failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```
and my fglrxinfo is:
```
Error: couldn't find RGB GLX visual!

```

---

### Post by dongmh on 2006-07-18
my glxgears is:
```
Error: couldn't get an RGB, Double-buffered visual
```

my xorg.conf is :
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI MOBILITY RADEON X1300 (M52 7149)"
	Driver		"fglrx"
	BusID			"PCI:1:0:0"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI MOBILITY RADEON X1300 (M52 7149)"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

please help me fix it

---

