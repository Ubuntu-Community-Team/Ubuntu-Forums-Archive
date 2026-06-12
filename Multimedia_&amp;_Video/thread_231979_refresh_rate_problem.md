---
title: "refresh rate problem"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by cairn on 2006-08-08
I have searched and searched and I haven't found any previous posts with this same problem but I hope I'm not duplicating a thread.

I can not get Ubuntu to let me use any refresh rate other than 75Hz. I have run "dpkg-reconfigure xserver-xorg" several times and manually edited the xorg.conf following many other suggestions I've read - all with no luck. Here's the relevant info:

Monitor: Samsung SyncMaster 740B LCD

Video: nVidia GeForce 6200 using nvidia drivers

All I want to do is have my display set at 1280 x 1024 @ 60Hz but I can not change it from 75hz (which flickers terribly). Changing the resolution has no effect, it will still only let me choose 75Hz. I tried custom modelines but it was still stuck at 75Hz. I have made sure to enter the exact HorizSync (30-81) and VertRefresh (56-75) in xorg.conf and still I can only choose 75Hz. 1280 x 1024 @ 60Hz is the optimal setting suggested by Samsung and it is how I had previously had it set up in windows so I know the hardware is capable of this setting.

I am attaching the most recent xorg.conf and xorg log files to this post. Any help would be greatly appreciated!

Oops, it won't let me attach the xorg log so here it is:


```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux caimaver-ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  7 23:42:33 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "NVIDIA Corporation NV40? [Unknown nVidia Card]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 0000,0000 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0080 card 10de,0c11 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0084 card 10de,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0087 card 10de,0c11 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0087 card 10de,0c11 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0088 card 10de,0c11 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,008a card 270f,f446 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,008b card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0085 card 10de,0c11 rev a3 class 01,01,8a hdr 00
(II) PCI: 00:0b:0: chip 10de,008e card 10de,05b3 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 01:07:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
(II) PCI: 01:09:0: chip 1412,1724 card 1412,1724 rev 01 class 04,01,00 hdr 00
(II) PCI: 01:0b:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0221 card 1682,2152 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe5000000 - 0xe50fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe5100000 - 0xe51fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe2000000 - 0xe4ffffff (0x3000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI: (1:7:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe5100000/12
(--) PCI:*(2:0:0) nVidia Corporation GeForce 6200 rev 161, Mem @ 0xe2000000/24, 0xd0000000/28, 0xe3000000/24
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe1ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe5010000 - 0xe50100ff (0x100) MX[B]
	[1] -1	0	0xe5101000 - 0xe5101fff (0x1000) MX[B]
	[2] -1	0	0xe5200000 - 0xe5200fff (0x1000) MX[B]
	[3] -1	0	0xe5204000 - 0xe52040ff (0x100) MX[B]
	[4] -1	0	0xe5203000 - 0xe5203fff (0x1000) MX[B]
	[5] -1	0	0xe5202000 - 0xe5202fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe5100000 - 0xe5100fff (0x1000) MX[B](B)
	[11] -1	0	0x0000d200 - 0x0000d2ff (0x100) IX[B]
	[12] -1	0	0x0000d100 - 0x0000d17f (0x80) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[14] -1	0	0x0000eb00 - 0x0000eb7f (0x80) IX[B]
	[15] -1	0	0x0000ea00 - 0x0000ea0f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000e200 - 0x0000e27f (0x80) IX[B]
	[22] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe5010000 - 0xe50100ff (0x100) MX[B]
	[1] -1	0	0xe5101000 - 0xe5101fff (0x1000) MX[B]
	[2] -1	0	0xe5200000 - 0xe5200fff (0x1000) MX[B]
	[3] -1	0	0xe5204000 - 0xe52040ff (0x100) MX[B]
	[4] -1	0	0xe5203000 - 0xe5203fff (0x1000) MX[B]
	[5] -1	0	0xe5202000 - 0xe5202fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe5100000 - 0xe5100fff (0x1000) MX[B](B)
	[11] -1	0	0x0000d200 - 0x0000d2ff (0x100) IX[B]
	[12] -1	0	0x0000d100 - 0x0000d17f (0x80) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[14] -1	0	0x0000eb00 - 0x0000eb7f (0x80) IX[B]
	[15] -1	0	0x0000ea00 - 0x0000ea0f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000e200 - 0x0000e27f (0x80) IX[B]
	[22] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
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
	[4] -1	0	0xe5010000 - 0xe50100ff (0x100) MX[B]
	[5] -1	0	0xe5101000 - 0xe5101fff (0x1000) MX[B]
	[6] -1	0	0xe5200000 - 0xe5200fff (0x1000) MX[B]
	[7] -1	0	0xe5204000 - 0xe52040ff (0x100) MX[B]
	[8] -1	0	0xe5203000 - 0xe5203fff (0x1000) MX[B]
	[9] -1	0	0xe5202000 - 0xe5202fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe5100000 - 0xe5100fff (0x1000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d200 - 0x0000d2ff (0x100) IX[B]
	[18] -1	0	0x0000d100 - 0x0000d17f (0x80) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[20] -1	0	0x0000eb00 - 0x0000eb7f (0x80) IX[B]
	[21] -1	0	0x0000ea00 - 0x0000ea0f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000e200 - 0x0000e27f (0x80) IX[B]
	[28] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[29] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
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
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe5010000 - 0xe50100ff (0x100) MX[B]
	[5] -1	0	0xe5101000 - 0xe5101fff (0x1000) MX[B]
	[6] -1	0	0xe5200000 - 0xe5200fff (0x1000) MX[B]
	[7] -1	0	0xe5204000 - 0xe52040ff (0x100) MX[B]
	[8] -1	0	0xe5203000 - 0xe5203fff (0x1000) MX[B]
	[9] -1	0	0xe5202000 - 0xe5202fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe5100000 - 0xe5100fff (0x1000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d200 - 0x0000d2ff (0x100) IX[B]
	[18] -1	0	0x0000d100 - 0x0000d17f (0x80) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[20] -1	0	0x0000eb00 - 0x0000eb7f (0x80) IX[B]
	[21] -1	0	0x0000ea00 - 0x0000ea0f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000e200 - 0x0000e27f (0x80) IX[B]
	[28] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[29] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe5010000 - 0xe50100ff (0x100) MX[B]
	[5] -1	0	0xe5101000 - 0xe5101fff (0x1000) MX[B]
	[6] -1	0	0xe5200000 - 0xe5200fff (0x1000) MX[B]
	[7] -1	0	0xe5204000 - 0xe52040ff (0x100) MX[B]
	[8] -1	0	0xe5203000 - 0xe5203fff (0x1000) MX[B]
	[9] -1	0	0xe5202000 - 0xe5202fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe5100000 - 0xe5100fff (0x1000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d200 - 0x0000d2ff (0x100) IX[B]
	[21] -1	0	0x0000d100 - 0x0000d17f (0x80) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000eb00 - 0x0000eb7f (0x80) IX[B]
	[24] -1	0	0x0000ea00 - 0x0000ea0f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000e200 - 0x0000e27f (0x80) IX[B]
	[31] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[32] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[33] 0	0	0xe40003b0 - 0xe40003bb (0xc) IS[B]
	[34] 0	0	0xe40003c0 - 0xe40003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:2:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.07.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:2:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe5010000 - 0xe50100ff (0x100) MX[B]
	[8] -1	0	0xe5101000 - 0xe5101fff (0x1000) MX[B]
	[9] -1	0	0xe5200000 - 0xe5200fff (0x1000) MX[B]
	[10] -1	0	0xe5204000 - 0xe52040ff (0x100) MX[B]
	[11] -1	0	0xe5203000 - 0xe5203fff (0x1000) MX[B]
	[12] -1	0	0xe5202000 - 0xe5202fff (0x1000) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe5100000 - 0xe5100fff (0x1000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000d200 - 0x0000d2ff (0x100) IX[B]
	[24] -1	0	0x0000d100 - 0x0000d17f (0x80) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[26] -1	0	0x0000eb00 - 0x0000eb7f (0x80) IX[B]
	[27] -1	0	0x0000ea00 - 0x0000ea0f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x0000e200 - 0x0000e27f (0x80) IX[B]
	[34] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[35] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[36] 0	0	0xe40003b0 - 0xe40003bb (0xc) IS[B]
	[37] 0	0	0xe40003c0 - 0xe40003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
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
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Mon Aug  7 23:42:35 2006: 5774 X: client 2 rejected from local host
AUDIT: Mon Aug  7 23:42:35 2006: 5774 X: client 4 rejected from local host
AUDIT: Mon Aug  7 23:42:35 2006: 5774 X: client 3 rejected from local host
AUDIT: Mon Aug  7 23:42:35 2006: 5774 X: client 5 rejected from local host
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): Setting mode "1280x1024"

```

---

### Post by tseliot on 2006-08-08
Try point 10 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by cairn on 2006-08-08
Brilliant! It worked; I used point 10 in your guide and now I have 60Hz refresh. Thanks for your help!

---

