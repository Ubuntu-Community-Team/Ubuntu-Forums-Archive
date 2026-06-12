---
title: "Nvidia drivers + 7600GT = failed to start x server"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by BrownieMan on 2007-02-01
I havn't been able to get any drivers except vesa to work with my Nvidia 7600 graphics card. I've tried nv and nvidia. I've tried isntalling nvidia manually, with a script, and automatix2. Each tiem it seems to be succesful but when i start up I get teh infamous "failed to start x server".

I've included a couple of logs when I tried to use the nvidia driver:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux premo 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb  1 15:27:20 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
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
(II) PCI: 00:00:0: chip 10de,02f5 card 1849,02f5 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1849,02fa rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1849,02fe rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1849,02f8 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1849,02f9 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1849,02ff rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1849,027f rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1849,027e rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1849,0270 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0261 card 1849,0261 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1849,0264 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1849,026d rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1849,026e rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1849,0265 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1849,0266 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:2: chip 10de,026b card 1849,0850 rev a2 class 04,01,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1849,0269 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 10de,0391 card 19f1,201f rev a1 class 03,00,00 hdr 00
(II) PCI: 04:0a:0: chip 1745,2010 card 10de,2010 rev 00 class 04,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfa900000 - 0xfe9fffff (0x4100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xbdf00000 - 0xddefffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xddf00000 - 0xdfefffff (0x2000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation unknown chipset (0x0391) rev 161, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfc000000/24, I/O @ 0xbc00/7, BIOS @ 0xfe9e0000/17
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
	[0] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[1] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[2] -1	0	0xfebbb000 - 0xfebbbfff (0x1000) MX[B]
	[3] -1	0	0xfebbc000 - 0xfebbcfff (0x1000) MX[B]
	[4] -1	0	0xfebbd000 - 0xfebbdfff (0x1000) MX[B]
	[5] -1	0	0xfebbfc00 - 0xfebbfcff (0x100) MX[B]
	[6] -1	0	0xfebbe000 - 0xfebbefff (0x1000) MX[B]
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[8] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x00000e00 - 0x00000e03 (0x4) IX[B]
	[17] -1	0	0x00000e80 - 0x00000e87 (0x8) IX[B]
	[18] -1	0	0x00000f00 - 0x00000f03 (0x4) IX[B]
	[19] -1	0	0x00000f80 - 0x00000f87 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[22] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[1] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[2] -1	0	0xfebbb000 - 0xfebbbfff (0x1000) MX[B]
	[3] -1	0	0xfebbc000 - 0xfebbcfff (0x1000) MX[B]
	[4] -1	0	0xfebbd000 - 0xfebbdfff (0x1000) MX[B]
	[5] -1	0	0xfebbfc00 - 0xfebbfcff (0x100) MX[B]
	[6] -1	0	0xfebbe000 - 0xfebbefff (0x1000) MX[B]
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[8] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x00000e00 - 0x00000e03 (0x4) IX[B]
	[17] -1	0	0x00000e80 - 0x00000e87 (0x8) IX[B]
	[18] -1	0	0x00000f00 - 0x00000f03 (0x4) IX[B]
	[19] -1	0	0x00000f80 - 0x00000f87 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[22] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
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
	[4] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[6] -1	0	0xfebbb000 - 0xfebbbfff (0x1000) MX[B]
	[7] -1	0	0xfebbc000 - 0xfebbcfff (0x1000) MX[B]
	[8] -1	0	0xfebbd000 - 0xfebbdfff (0x1000) MX[B]
	[9] -1	0	0xfebbfc00 - 0xfebbfcff (0x100) MX[B]
	[10] -1	0	0xfebbe000 - 0xfebbefff (0x1000) MX[B]
	[11] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[22] -1	0	0x00000e00 - 0x00000e03 (0x4) IX[B]
	[23] -1	0	0x00000e80 - 0x00000e87 (0x8) IX[B]
	[24] -1	0	0x00000f00 - 0x00000f03 (0x4) IX[B]
	[25] -1	0	0x00000f80 - 0x00000f87 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[28] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
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
	compiled for 4.0.2, module version = 1.0.8776
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
	compiled for 4.0.2, module version = 1.0.8776
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
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Assigning device section with no busID to primary device
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
	[4] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[6] -1	0	0xfebbb000 - 0xfebbbfff (0x1000) MX[B]
	[7] -1	0	0xfebbc000 - 0xfebbcfff (0x1000) MX[B]
	[8] -1	0	0xfebbd000 - 0xfebbdfff (0x1000) MX[B]
	[9] -1	0	0xfebbfc00 - 0xfebbfcff (0x100) MX[B]
	[10] -1	0	0xfebbe000 - 0xfebbefff (0x1000) MX[B]
	[11] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[22] -1	0	0x00000e00 - 0x00000e03 (0x4) IX[B]
	[23] -1	0	0x00000e80 - 0x00000e87 (0x8) IX[B]
	[24] -1	0	0x00000f00 - 0x00000f03 (0x4) IX[B]
	[25] -1	0	0x00000f80 - 0x00000f87 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[28] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[6] -1	0	0xfebbb000 - 0xfebbbfff (0x1000) MX[B]
	[7] -1	0	0xfebbc000 - 0xfebbcfff (0x1000) MX[B]
	[8] -1	0	0xfebbd000 - 0xfebbdfff (0x1000) MX[B]
	[9] -1	0	0xfebbfc00 - 0xfebbfcff (0x100) MX[B]
	[10] -1	0	0xfebbe000 - 0xfebbefff (0x1000) MX[B]
	[11] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[25] -1	0	0x00000e00 - 0x00000e03 (0x4) IX[B]
	[26] -1	0	0x00000e80 - 0x00000e87 (0x8) IX[B]
	[27] -1	0	0x00000f00 - 0x00000f03 (0x4) IX[B]
	[28] -1	0	0x00000f80 - 0x00000f87 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[31] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(EE) NVIDIA(0): Given color depth (4) is not supported
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    4
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by glabouni on 2007-02-01
the reason why x server is failing to start seems to be:
```
(EE) NVIDIA(0): Given color depth (4) is not supported
```

it is caused by 
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
**    DefaultDepth    4**
```

edit your /etc/X11/xorg.conf and replace 4 by 16 or 24
then try startx again

---

