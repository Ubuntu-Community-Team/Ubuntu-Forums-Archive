---
title: "UbuntuStudio - Realtime kernel doesn't boot (X-Server can't load NVidia drivers)"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by chriswyatt on 2007-10-22
Processor: Intel Centrino Duo
Graphics: NVidia GeForce Go 7200

Hi, I just installed all the UbuntuStudio packages over my Ubuntu Gutsy installation but the realtime kernel will not boot up and I just get an x-server error, currently I'm writing this using my generic kernel:

Here's my X-Server log for the failed boot attempt:

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux chrisw-laptop 2.6.22-14-rt #1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 22 17:09:26 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation GeForce Go 7200"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30b2 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30b2 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30b2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30b2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30b2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30b2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30b2 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30b2 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 103c,30b2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 103c,30b2 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30b2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d6 card 103c,30b2 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:00:0: chip 8086,4222 card 103c,135c rev 02 class 02,80,00 hdr 00
(II) PCI: 08:08:0: chip 8086,1092 card 103c,30b2 rev 02 class 02,00,00 hdr 00
(II) PCI: 08:09:0: chip 1180,0832 card 103c,30b2 rev 00 class 0c,00,10 hdr 80
(II) PCI: 08:09:1: chip 1180,0822 card 103c,30b2 rev 19 class 08,05,00 hdr 80
(II) PCI: 08:09:2: chip 1180,0843 card 103c,30b2 rev 01 class 08,80,00 hdr 80
(II) PCI: 08:09:3: chip 1180,0592 card 103c,30b2 rev 0a class 08,80,00 hdr 80
(II) PCI: 08:09:4: chip 1180,0852 card 103c,30b2 rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,8), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:3), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd60fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,8), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xd6100000 - 0xd61fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce Go 7200 rev 161, Mem @ 0xd5000000/24, 0xc0000000/27, 0xd4000000/24
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
	[0] -1	0	0xd6102400 - 0xd61024ff (0x100) MX[B]
	[1] -1	0	0xd6102000 - 0xd61020ff (0x100) MX[B]
	[2] -1	0	0xd6101c00 - 0xd6101cff (0x100) MX[B]
	[3] -1	0	0xd6101800 - 0xd61018ff (0x100) MX[B]
	[4] -1	0	0xd6101000 - 0xd61017ff (0x800) MX[B]
	[5] -1	0	0xd6100000 - 0xd6100fff (0x1000) MX[B]
	[6] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[7] -1	0	0xd6404400 - 0xd64047ff (0x400) MX[B]
	[8] -1	0	0xd6404000 - 0xd64043ff (0x400) MX[B]
	[9] -1	0	0xd6400000 - 0xd6403fff (0x4000) MX[B]
	[10] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[14] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[15] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[16] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[17] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[18] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[19] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[20] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd6102400 - 0xd61024ff (0x100) MX[B]
	[1] -1	0	0xd6102000 - 0xd61020ff (0x100) MX[B]
	[2] -1	0	0xd6101c00 - 0xd6101cff (0x100) MX[B]
	[3] -1	0	0xd6101800 - 0xd61018ff (0x100) MX[B]
	[4] -1	0	0xd6101000 - 0xd61017ff (0x800) MX[B]
	[5] -1	0	0xd6100000 - 0xd6100fff (0x1000) MX[B]
	[6] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[7] -1	0	0xd6404400 - 0xd64047ff (0x400) MX[B]
	[8] -1	0	0xd6404000 - 0xd64043ff (0x400) MX[B]
	[9] -1	0	0xd6400000 - 0xd6403fff (0x4000) MX[B]
	[10] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[14] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[15] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[16] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[17] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[18] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[19] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[20] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
	[4] -1	0	0xd6102400 - 0xd61024ff (0x100) MX[B]
	[5] -1	0	0xd6102000 - 0xd61020ff (0x100) MX[B]
	[6] -1	0	0xd6101c00 - 0xd6101cff (0x100) MX[B]
	[7] -1	0	0xd6101800 - 0xd61018ff (0x100) MX[B]
	[8] -1	0	0xd6101000 - 0xd61017ff (0x800) MX[B]
	[9] -1	0	0xd6100000 - 0xd6100fff (0x1000) MX[B]
	[10] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[11] -1	0	0xd6404400 - 0xd64047ff (0x400) MX[B]
	[12] -1	0	0xd6404000 - 0xd64043ff (0x400) MX[B]
	[13] -1	0	0xd6400000 - 0xd6403fff (0x4000) MX[B]
	[14] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[23] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[24] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[25] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[26] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
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
	[4] -1	0	0xd6102400 - 0xd61024ff (0x100) MX[B]
	[5] -1	0	0xd6102000 - 0xd61020ff (0x100) MX[B]
	[6] -1	0	0xd6101c00 - 0xd6101cff (0x100) MX[B]
	[7] -1	0	0xd6101800 - 0xd61018ff (0x100) MX[B]
	[8] -1	0	0xd6101000 - 0xd61017ff (0x800) MX[B]
	[9] -1	0	0xd6100000 - 0xd6100fff (0x1000) MX[B]
	[10] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[11] -1	0	0xd6404400 - 0xd64047ff (0x400) MX[B]
	[12] -1	0	0xd6404000 - 0xd64043ff (0x400) MX[B]
	[13] -1	0	0xd6400000 - 0xd6403fff (0x4000) MX[B]
	[14] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[23] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[24] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[25] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[26] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd6102400 - 0xd61024ff (0x100) MX[B]
	[5] -1	0	0xd6102000 - 0xd61020ff (0x100) MX[B]
	[6] -1	0	0xd6101c00 - 0xd6101cff (0x100) MX[B]
	[7] -1	0	0xd6101800 - 0xd61018ff (0x100) MX[B]
	[8] -1	0	0xd6101000 - 0xd61017ff (0x800) MX[B]
	[9] -1	0	0xd6100000 - 0xd6100fff (0x1000) MX[B]
	[10] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[11] -1	0	0xd6404400 - 0xd64047ff (0x400) MX[B]
	[12] -1	0	0xd6404000 - 0xd64043ff (0x400) MX[B]
	[13] -1	0	0xd6400000 - 0xd6403fff (0x4000) MX[B]
	[14] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[24] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[25] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[26] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[27] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[28] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[29] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by chriswyatt on 2007-10-22
BUMP!

So, I'm guessing this is perhaps an incompatibility with the realtime kernel and my graphics card driver / processor combination.  X-Server fails on so many occasions :( .

---

### Post by chriswyatt on 2007-10-25
Bump

---

### Post by wolfen69 on 2007-10-25
i had to do
```
sudo apt-get remove nvidia-glx-new
```
reboot
then
```
sudo apt-get install nvidia-glx
```
reboot

---

### Post by chriswyatt on 2007-10-26
Ah, thankyou.  Hopefully this compatibility issue will get resolved soon.

---

### Post by garyedwardjohnston on 2008-01-25
my computer totally crashes and won't start...so my question is how do i do this using the live cd?

---

### Post by metrorat on 2008-03-12
I had exactly the same problem on my acer 5652 (Intel core duo 1.66, Nvidia G-Force Go 7600) and got round it by editing  the xorg.conf (from my generic kernel) using:

sudo dpkg-reconfigure -p hich xserver-xorg

I selected the nv driver instead of the nvidia driver which allowed me to boot into the rt kernel without the annoying xserver failure.  Once in the rt kernel I just ran Envy and all was rosy. But this didn't work until all the restricted modules for rt kernel were installed from synaptic (not mentioned in the Ubuntu Studio install guide).

Hope this helps other newbs like myself who might be looking for an easy solution (like I did for a couple of hours).

Now to get my Emu 1616m working...

Peas

---

