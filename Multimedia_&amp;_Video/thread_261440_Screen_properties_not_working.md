---
title: "Screen properties not working"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by lord_crow on 2006-09-20
Hi all, i've this problem, when i want to access the screen properties in kcontrol, the module just dies... when i launch it from konsole, i can see this error:

```
Pythonize constructor -- pid = 6682
Python interpreter initialized!



Pythonize constructor -- pid = 6682
open /dev/mem: Permission denied
VESA BIOS Extensions not detected.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 1677, in create_displayconfig
    return DisplayApp(parent, name)
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 443, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 368, in __init__
    self._finalizeInit()
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 373, in _finalizeInit
    gfxcard._finalizeInit()
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 1082, in _finalizeInit
    screen._finalizeInit()
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 1599, in _finalizeInit
    (self.redgamma, self.greengamma, self.bluegamma) = self.x_live_screen.getGamma()
  File "/usr/lib/python2.4/site-packages/xf86misc.py", line 50, in getGamma
    return ixf86misc.GetGamma(self.display,self.screenid)
SystemError: error return without exception set
error: *** runFunction failure

```

when i do xdpyinfo | grep VidModeExtension i get nothing, but if i look at my xorg.conf file i see the Load "extmod" line... and xorg.log says:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Lara64 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Wed Sep 20 08:51:40 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 1106,0282 card 1043,80a3 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,812a rev 60 class 04,01,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
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
	[0] -1	0	0xfaf00000 - 0xfbffffff (0x1100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf9ffffff (0x1a000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xfb000000/24, 0xe0000000/28, BIOS @ 0xfaf00000/17
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
(II) PCI Memory resource overlap reduced 0xdc000000 from 0xdfffffff to 0xdbffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfae00000 - 0xfae000ff (0x100) MX[B]
	[1] -1	0	0xfac00000 - 0xfac03fff (0x4000) MX[B]
	[2] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[3] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfae00000 - 0xfae000ff (0x100) MX[B]
	[1] -1	0	0xfac00000 - 0xfac03fff (0x4000) MX[B]
	[2] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[3] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
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
	[4] -1	0	0xfae00000 - 0xfae000ff (0x100) MX[B]
	[5] -1	0	0xfac00000 - 0xfac03fff (0x4000) MX[B]
	[6] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[7] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
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
	[4] -1	0	0xfae00000 - 0xfae000ff (0x100) MX[B]
	[5] -1	0	0xfac00000 - 0xfac03fff (0x4000) MX[B]
	[6] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[7] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfae00000 - 0xfae000ff (0x100) MX[B]
	[5] -1	0	0xfac00000 - 0xfac03fff (0x4000) MX[B]
	[6] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[7] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): CRT-1: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (92, 100); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[1] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfae00000 - 0xfae000ff (0x100) MX[B]
	[7] -1	0	0xfac00000 - 0xfac03fff (0x4000) MX[B]
	[8] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[9] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
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
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

as you can see, extmod is actually loading... maybe i'm missing something, maybe i'm looking at the wrong place, the problem is that i just can't set up the screen to go stand by after a period of time.

anyway, any ideas?

i'm using kubuntu dapper 32bits, with xgl+compiz on an nvidia GeForce FX 5500 and using the propietary drivers ... i think i didn't miss any data.

cheers and thanks for your help.

---

