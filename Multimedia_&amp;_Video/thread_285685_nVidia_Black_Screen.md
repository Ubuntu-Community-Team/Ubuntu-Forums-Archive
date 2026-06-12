---
title: "nVidia Black Screen"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by coatesj on 2006-10-27
Hello everyone,

I have trawled over this forum for a fix to my gfx problem.  It seems that i have done everything that people have been advised off to do to no avail.

My problem is that when i use the nVidia xorg.conf file when i restart x my screen goes black then turns off.  i have to power off the computer into safe mode and replace the config for me to get back in to ubuntu login screen.

my output from Xorg.0.log (when the nVidia config is running)

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux jamie-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 27 07:42:29 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "StudioWorks"
(**) |   |-->Device "nVidia Corporation GeForce 6200 (rev a1)"
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
(II) PCI: 00:00:0: chip 1039,0650 card 0000,0000 rev 01 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0961 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:2: chip 1039,7001 card 1631,7001 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:3: chip 1039,7001 card 1631,7001 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1631,5513 rev d0 class 01,01,80 hdr 80
(II) PCI: 00:02:7: chip 1039,7012 card 1631,2007 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:0b:0: chip 1033,0035 card 1799,0001 rev 43 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 1033,0035 card 1799,0001 rev 43 class 0c,03,10 hdr 00
(II) PCI: 00:0b:2: chip 1033,00e0 card 1799,0002 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:0d:0: chip 1102,0004 card 1102,0053 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:0d:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:0d:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:10:0: chip 10ec,8139 card 1631,7003 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,00f3 card 0000,0000 rev a2 class 03,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdbe00000 - 0xdfefffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbbc00000 - 0xdbcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6200] rev 162, Mem @ 0xde000000/24, 0xc0000000/28, 0xdd000000/24, BIOS @ 0xdfee0000/17
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfffbe00 - 0xdfffbeff (0x100) MX[B]
	[1] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[2] -1	0	0xdfffb000 - 0xdfffb7ff (0x800) MX[B]
	[3] -1	0	0xdfffbf00 - 0xdfffbfff (0x100) MX[B]
	[4] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[5] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[6] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[7] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffbe00 - 0xdfffbeff (0x100) MX[B]
	[1] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[2] -1	0	0xdfffb000 - 0xdfffb7ff (0x800) MX[B]
	[3] -1	0	0xdfffbf00 - 0xdfffbfff (0x100) MX[B]
	[4] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[5] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[6] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[7] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
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
	[4] -1	0	0xdfffbe00 - 0xdfffbeff (0x100) MX[B]
	[5] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[6] -1	0	0xdfffb000 - 0xdfffb7ff (0x800) MX[B]
	[7] -1	0	0xdfffbf00 - 0xdfffbfff (0x100) MX[B]
	[8] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[11] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
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
(II) Primary Device is: PCI 01:00:0
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
	[4] -1	0	0xdfffbe00 - 0xdfffbeff (0x100) MX[B]
	[5] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[6] -1	0	0xdfffb000 - 0xdfffb7ff (0x800) MX[B]
	[7] -1	0	0xdfffbf00 - 0xdfffbfff (0x100) MX[B]
	[8] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[11] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffbe00 - 0xdfffbeff (0x100) MX[B]
	[5] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[6] -1	0	0xdfffb000 - 0xdfffb7ff (0x800) MX[B]
	[7] -1	0	0xdfffbf00 - 0xdfffbfff (0x100) MX[B]
	[8] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[11] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[28] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "0"
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "NoRenderExtension" "Off"
(**) NVIDIA(0): Option "IgnoreDisplayDevices" "DFP,TV"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "Off"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of AGP disabled per request
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.61.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     LG StudioWorks 995E (CRT-0)
(--) NVIDIA(0): LG StudioWorks 995E (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfffbe00 - 0xdfffbeff (0x100) MX[B]
	[8] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[9] -1	0	0xdfffb000 - 0xdfffb7ff (0x800) MX[B]
	[10] -1	0	0xdfffbf00 - 0xdfffbfff (0x100) MX[B]
	[11] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[12] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[13] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[14] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[31] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000508, 0)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000508, 0)
(II) NVIDIA(0): Setting mode "1280x1024"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000005a8, 0)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000005a8, 0)
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): WAIT (2, 3, 0x8000, 0x00000000, 0x00000aec, 0)

```

It looks like from that log that my gfx drivers are being loaded, then i don't understand why my screen is turning black :\

any assistance would be greatly appreciated,

---

### Post by coatesj on 2006-10-27
here is my xorg.conf

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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"nVidia Corporation GeForce 6200 (rev a1)"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "NvAGP" "0" 
	Option "RenderAccel" "True" 
	Option "IgnoreDisplayDevices" "DFP,TV" 
	Option "NoRenderExtension" "Off" 
	Option "AllowGLXWithComposite" "Off"
EndSection

Section "Monitor"
	Identifier	"StudioWorks"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 6200 (rev a1)"
	Monitor		"StudioWorks"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by gerowen on 2006-10-27
Make sure the PCI address of your card is correct.  If you have a Windows installation, boot it, go to Control Panel, System, Hardware, Device Manager, right click your graphics card and go to properties, it will give you the PCI information there.  I spent an entire day stuck at an X crash screen, only to find out I was specifying the incorrect PCI location of my graphics card.  Also make sure that the HorizSync and VertRefresh values are correct for your monitor.

---

### Post by tseliot on 2006-10-27
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by coatesj on 2006-10-27
Marcusdeans,

Hi thanks for replying.  

I have checked both of these things out through my windows install and they seem to be fine,

my refresh rate in windows is at 85hz.  

My card is on PCIB:1:0:0

so that should be fine....

---

### Post by mbluethgen on 2006-10-30
Hi,

i have exact the same problem under Ubuntu 6.10. The driver installs fine. After reboot i get a black screen and i have to restart the computer. 

The funny thing is, i have tried to start the computer in recovery mode. After that i start startx and all is fine. But if i try to start the computer in normal mode i get a black screen. Don't know what that is.

Maybe someone can help me.

Bye 
Marco

---

