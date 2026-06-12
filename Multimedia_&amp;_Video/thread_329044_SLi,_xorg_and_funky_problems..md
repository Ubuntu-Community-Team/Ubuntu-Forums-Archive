---
title: "SLi, xorg and funky problems."
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by MattKemp on 2006-12-31
Hello folks, and a happy new year to anyone that's had it already!

I'm having fun with my laptop at the moment. I'm trying to get Ubuntu running on it, and have reached a bit of a deadlock.

Firstly to start off, relevant PC bits: AMD Turion64, but running Ubuntu 386, dual SLi GeForce go 7950 GTX graphics cards, 19" WXSGA monitor. If anyone's that interested (or it helps) it's an Alienware mALX laptop (So I can't really fiddle with it :/)

It started off with the installer: I had the dreaded black screen problem that seems to be hitting people at the moment. I managed to solve it by fiddling with xorg.conf and eventually got an interface - I've now installed and tried to install the binary drivers. This is where the problems begin - I can't find a xorg.conf that will work!

Using dpkg-reconfigure xserver-xorg, I managed to completely ream the xorg.conf file. If I start X, I now get a blank screen (as far as I can tell it's still receiving signal, just nothing) with nv or nvidia. If I set the driver to nvidia and set SLI to 1, it seems the screen actually switches off. Looking at my xorg log, I get one of a few errors:

- No device defined for PCI:4:0:0 (or something to that effect). If I define one, I still get it.
- No device defined for PCI:3:0:0 (this happens if I change the 3 in the xorg.conf to a 4 in the Device section)
- No devices found (this happens with SLI disabled, using the NV driver.)

Using nvidia-xconfig seems to just change the device section to a default name and the driver to nvidia. At one point, after using nvidia-xconfig, it told me I had an ATi card.

Using dpkg-reconfigure xserver-xorg I put in the details - it mentions something about dual head systems but only asks me for one PCI bus, so only one Device gets set up.

Sadly I can't post my xorg log, as this is the only PC I have at the moment and I'm having to type this in Windows. I'll try and find a way of transferring it across.

Thanks for anyone's help, and a happy new year.

---

### Post by hanover.fiste on 2006-12-31
SLI on linux is an unholy mess right now. It's barely worth jacking with. But if you must, this is what I've learned in 6 months of trying to get SLI running in something approaching a stable configuration.

If SLI is enabled, there must be only a single device defined. You will rarely need to define the PCI device ID. The nvidia driver should handle that on its own.

Start with a bare minimum xorg.conf and build from there.

Many systems needs pci=nommconf or pci=conf1 in the kernel line due to buggy bioses.

If that doesn't at least get you to X, post your xorg.conf and Xorg.0.log files.

---

### Post by MattKemp on 2006-12-31
Managed to grab the following Xorg.log:

> 
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux autopsy 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan  1 02:31:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1558,0590 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1558,0590 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1558,0590 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1558,0590 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1558,0590 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1558,0590 rev a2 class 04,01,00 hdr 80
(II) PCI: 00:04:1: chip 10de,0058 card 1558,0590 rev a2 class 07,03,00 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1558,0590 rev f2 class 01,01,8a hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1558,0590 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 11ab,4362 card 1558,0590 rev 19 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0299 card 1558,0590 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:00:0: chip 10de,0299 card 1558,0590 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:06:0: chip 104c,8023 card 0000,0000 rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:08:0: chip 168c,0013 card 185f,1012 rev 01 class 02,00,00 hdr 00
(II) PCI: 05:09:0: chip 104c,8031 card 6000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 05:09:3: chip 104c,8033 card 1558,0590 rev 00 class 01,80,00 hdr 80
(II) PCI: 05:09:4: chip 104c,8034 card 1558,0590 rev 00 class 08,05,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,9), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x8a000000 - 0x8cffffff (0x3000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x89ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x92000000 - 0x920fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x92100000 - 0x921fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:12:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:13:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x8d000000 - 0x8f7fffff (0x2800000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:14:0), (0,4,4), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[1] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[2] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[3] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x8f800000 - 0x91ffffff (0x2800000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (5:9:0), (5,6,9), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x8a000000 - 0x8bffffff (0x2000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x89ffffff (0x2000000) MX[B]
(--) PCI: (3:0:0) nVidia Corporation unknown chipset (0x0299) rev 161, Mem @ 0x8d000000/24, 0xb0000000/28, 0x8e000000/24, I/O @ 0x4000/7
(--) PCI:*(4:0:0) nVidia Corporation unknown chipset (0x0299) rev 161, Mem @ 0x90000000/24, 0xc0000000/28, 0x91000000/24, I/O @ 0x5000/7
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, (...removed for long-ness...)
(II) Primary Device is: PCI 04:00:0
(WW) NV: No matching Device section for instance (BusID PCI:4:0:0) found
(--) Chipset GeForce Go 7900 GTX found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x8c017a00 - 0x8c017aff (0x100) MX[B]
	[5] -1	0	0x8c017900 - 0x8c0179ff (0x100) MX[B]
	[6] -1	0	0x8c017800 - 0x8c0178ff (0x100) MX[B]
	[7] -1	0	0x8c014000 - 0x8c015fff (0x2000) MX[B]
	[8] -1	0	0x8c000000 - 0x8c00ffff (0x10000) MX[B]
	[9] -1	0	0x8c010000 - 0x8c013fff (0x4000) MX[B]
	[10] -1	0	0x8c017000 - 0x8c0177ff (0x800) MX[B]
	[11] -1	0	0x92000000 - 0x92003fff (0x4000) MX[B]
	[12] -1	0	0x92203000 - 0x92203fff (0x1000) MX[B]
	[13] -1	0	0x92202000 - 0x92202fff (0x1000) MX[B]
	[14] -1	0	0x92201000 - 0x92201fff (0x1000) MX[B]
	[15] -1	0	0x92204000 - 0x922040ff (0x100) MX[B]
	[16] -1	0	0x92200000 - 0x92200fff (0x1000) MX[B]
	[17] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[20] -1	0	0x8e000000 - 0x8effffff (0x1000000) MX[B](B)
	[21] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[22] -1	0	0x8d000000 - 0x8dffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[26] -1	0	0x00002430 - 0x0000243f (0x10) IX[B]
	[27] -1	0	0x00002440 - 0x00002443 (0x4) IX[B]
	[28] -1	0	0x00002448 - 0x0000244f (0x8) IX[B]
	[29] -1	0	0x00002444 - 0x00002447 (0x4) IX[B]
	[30] -1	0	0x00002450 - 0x00002457 (0x8) IX[B]
	[31] -1	0	0x00002420 - 0x0000242f (0x10) IX[B]
	[32] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[33] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[34] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[35] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[36] -1	0	0x00002080 - 0x000020bf (0x40) IX[B]
	[37] -1	0	0x000020c0 - 0x000020ff (0x40) IX[B]
	[38] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[39] -1	0	0x00005000 - 0x0000507f (0x80) IX[B](B)
	[40] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x8c017a00 - 0x8c017aff (0x100) MX[B]
	[5] -1	0	0x8c017900 - 0x8c0179ff (0x100) MX[B]
	[6] -1	0	0x8c017800 - 0x8c0178ff (0x100) MX[B]
	[7] -1	0	0x8c014000 - 0x8c015fff (0x2000) MX[B]
	[8] -1	0	0x8c000000 - 0x8c00ffff (0x10000) MX[B]
	[9] -1	0	0x8c010000 - 0x8c013fff (0x4000) MX[B]
	[10] -1	0	0x8c017000 - 0x8c0177ff (0x800) MX[B]
	[11] -1	0	0x92000000 - 0x92003fff (0x4000) MX[B]
	[12] -1	0	0x92203000 - 0x92203fff (0x1000) MX[B]
	[13] -1	0	0x92202000 - 0x92202fff (0x1000) MX[B]
	[14] -1	0	0x92201000 - 0x92201fff (0x1000) MX[B]
	[15] -1	0	0x92204000 - 0x922040ff (0x100) MX[B]
	[16] -1	0	0x92200000 - 0x92200fff (0x1000) MX[B]
	[17] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[20] -1	0	0x8e000000 - 0x8effffff (0x1000000) MX[B](B)
	[21] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[22] -1	0	0x8d000000 - 0x8dffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[29] -1	0	0x00002430 - 0x0000243f (0x10) IX[B]
	[30] -1	0	0x00002440 - 0x00002443 (0x4) IX[B]
	[31] -1	0	0x00002448 - 0x0000244f (0x8) IX[B]
	[32] -1	0	0x00002444 - 0x00002447 (0x4) IX[B]
	[33] -1	0	0x00002450 - 0x00002457 (0x8) IX[B]
	[34] -1	0	0x00002420 - 0x0000242f (0x10) IX[B]
	[35] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[36] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[37] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[38] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[39] -1	0	0x00002080 - 0x000020bf (0x40) IX[B]
	[40] -1	0	0x000020c0 - 0x000020ff (0x40) IX[B]
	[41] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[42] -1	0	0x00005000 - 0x0000507f (0x80) IX[B](B)
	[43] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
	[44] 0	0	0x8f0003b0 - 0x8f0003bb (0xc) IS[B]
	[45] 0	0	0x8f0003c0 - 0x8f0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) Truncating PCI BIOS Length to 65536
(--) NV(0): Chipset: "GeForce Go 7900 GTX"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xB0000000
(--) NV(0): MMIO registers at 0x8D000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1680 x 1050
(II) NV(0): Panel is LVDS
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 28.00-84.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1600x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1600x1200" (unknown reason)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1792x1344" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1792x1344" (unknown reason)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1792x1344" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1792x1344" (unknown reason)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1856x1392" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1856x1392" (unknown reason)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1856x1392" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1856x1392" (unknown reason)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1920x1200" (unknown reason)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1200" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1920x1200" (unknown reason)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "1920x1440" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "1920x1440" (unknown reason)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Mode "2048x1536" is larger than BIOS programmed panel size of 1680 x 1050.  Removing.
(II) NV(0): Not using default mode "2048x1536" (unknown reason)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1680x1050 (pitch 1680)
(**) NV(0): *Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "1680x1050": 146.2 MHz, 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(**) NV(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) NV(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
(**) NV(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0):  Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) NV(0): Modeline "1440x900"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
(**) NV(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) NV(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(++) NV(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x8e000000 - 0x8effffff (0x1000000) MX[B]
	[1] 0	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
	[2] 0	0	0x8d000000 - 0x8dffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x8c017a00 - 0x8c017aff (0x100) MX[B]
	[8] -1	0	0x8c017900 - 0x8c0179ff (0x100) MX[B]
	[9] -1	0	0x8c017800 - 0x8c0178ff (0x100) MX[B]
	[10] -1	0	0x8c014000 - 0x8c015fff (0x2000) MX[B]
	[11] -1	0	0x8c000000 - 0x8c00ffff (0x10000) MX[B]
	[12] -1	0	0x8c010000 - 0x8c013fff (0x4000) MX[B]
	[13] -1	0	0x8c017000 - 0x8c0177ff (0x800) MX[B]
	[14] -1	0	0x92000000 - 0x92003fff (0x4000) MX[B]
	[15] -1	0	0x92203000 - 0x92203fff (0x1000) MX[B]
	[16] -1	0	0x92202000 - 0x92202fff (0x1000) MX[B]
	[17] -1	0	0x92201000 - 0x92201fff (0x1000) MX[B]
	[18] -1	0	0x92204000 - 0x922040ff (0x100) MX[B]
	[19] -1	0	0x92200000 - 0x92200fff (0x1000) MX[B]
	[20] -1	0	0x91000000 - 0x91ffffff (0x1000000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[22] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[23] -1	0	0x8e000000 - 0x8effffff (0x1000000) MX[B](B)
	[24] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[25] -1	0	0x8d000000 - 0x8dffffff (0x1000000) MX[B](B)
	[26] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[27] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[28] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[29] 0	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[33] -1	0	0x00002430 - 0x0000243f (0x10) IX[B]
	[34] -1	0	0x00002440 - 0x00002443 (0x4) IX[B]
	[35] -1	0	0x00002448 - 0x0000244f (0x8) IX[B]
	[36] -1	0	0x00002444 - 0x00002447 (0x4) IX[B]
	[37] -1	0	0x00002450 - 0x00002457 (0x8) IX[B]
	[38] -1	0	0x00002420 - 0x0000242f (0x10) IX[B]
	[39] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[40] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[41] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[42] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[43] -1	0	0x00002080 - 0x000020bf (0x40) IX[B]
	[44] -1	0	0x000020c0 - 0x000020ff (0x40) IX[B]
	[45] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[46] -1	0	0x00005000 - 0x0000507f (0x80) IX[B](B)
	[47] -1	0	0x00004000 - 0x0000407f (0x80) IX[B](B)
	[48] 0	0	0x8f0003b0 - 0x8f0003bb (0xc) IS[B]
	[49] 0	0	0x8f0003c0 - 0x8f0003df (0x20) IS[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
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
(II) Configured Mouse: ps2EnableDataReporting: succeeded


Using the following xorg.conf:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
#	Load	"dri"
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

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection


---

### Post by MattKemp on 2006-12-31
> **hanover.fiste said:**
> 

Many systems needs pci=nommconf or pci=conf1 in the kernel line due to buggy bioses.

Cheers for the reply. What do you mean by this bit? I'm still relatively new, I haven't played with the kernel much.

---

### Post by MattKemp on 2006-12-31
**Update:** I've managed to get a GUI using the vesa driver, but it's not exactly pretty. This would suggest (to me) a problem with the nvidia drivers and my card, or something to do witht he resolution. I'll play some more.

**Update #2:**Managed to get 1680x1050 using the nv driver. I'd still like to get the nvidia one working, but I'm just hoping I don't break this. By changing the driver to nv, uncommenting the DRI bits and commenting out GLX, it works - so it may just be me being an idiot with the nvidia config.

---

### Post by MattKemp on 2007-01-01
Bit of a bump, if anyone could give me a hand. it handles actual windowing fine, but give it more than one animated gif on a page and it dies.

---

### Post by Dies on 2007-01-02
I've had no problems running SLI with any of my distros aside from having to add a couple boot options. I attached my xorg.conf for comparison, hope it helps.

You can add boot options by opening a terminal:

sudo gedit /boot/grub/grub.conf

And add the options to the end of the kernel line, pci=nommconf helps with some hardware issues and idle=poll helps with dual core processors.

like:
title Ubuntu (2.6.17)
        root (hd1,5)
        kernel /vmlinuz ro root=/dev/sdb6 quiet splash pci=nommconf idle=poll
        initrd /initrd.img

---

### Post by MattKemp on 2007-01-02
> **Dies said:**
> I've had no problems running SLI with any of my distros aside from having to add a couple boot options. I attached my xorg.conf for comparison, hope it helps.

You can add boot options by opening a terminal:

sudo gedit /boot/grub/grub.conf

And add the options to the end of the kernel line, pci=nommconf helps with some hardware issues and idle=poll helps with dual core processors.

like:
title Ubuntu (2.6.17)
        root (hd1,5)
        kernel /vmlinuz ro root=/dev/sdb6 quiet splash pci=nommconf idle=poll
        initrd /initrd.img



Dies,
just tried your suggestion, added the nocommconf line in and changed the xorg.conf - still no-go. I don't get sound or anthing, so I had to manually reboot. One thing I did notice is that when it starts up, just before the splash screen covers it, is a screen full of messages about how it's unable to allocate resources to PCI devices - it seems to happen with the nocommconf line or not, but it's to all kinds of devices and not just the buses that the graphics cards are on.

Clue?

---

### Post by Dies on 2007-01-02
It's nommconf not nocommconf, lol. I hope you used it the right way.

Anyways you can always try compiling your own newer kernel to see if it helps.
Also, not to upset anyone here but remember that not all distros are created equal, one might hate your hardware while another one absolutely loves it, so maybe checking out a few others might help you find one where most things work well out of the box or not - but still. I would suggest the usual suspects for that.

---

### Post by MattKemp on 2007-01-02
Sadly, no dice with nommconf either (d'oh!).
 The only thing that's bugging me is this flashing up every time I start up:

> [17179572.792000] PCI: Using ACPI for IRQ routing
[17179572.792000] PCI: If a device doesn't work, try "pci=routeirq".  If it help
s, post a report
[17179572.792000] PCI: Cannot allocate resource region 8 of bridge 0000:00:09.0
[17179572.792000] PCI: Cannot allocate resource region 8 of bridge 0000:00:0b.0
[17179572.792000] PCI: Cannot allocate resource region 8 of bridge 0000:00:0d.0
[17179572.792000] PCI: Cannot allocate resource region 8 of bridge 0000:00:0e.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:00:02.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:00:02.1
[17179572.792000] PCI: Cannot allocate resource region 2 of device 0000:00:04.0
[17179572.792000] PCI: Cannot allocate resource region 2 of device 0000:00:04.1
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:05:06.0
[17179572.792000] PCI: Cannot allocate resource region 1 of device 0000:05:06.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:05:08.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:05:09.3
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:05:09.4
[17179572.792000] PCI: Cannot allocate resource region 1 of device 0000:05:09.4
[17179572.792000] PCI: Cannot allocate resource region 2 of device 0000:05:09.4
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:01:00.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:04:00.0
[17179572.792000] PCI: Cannot allocate resource region 3 of device 0000:04:00.0
[17179572.792000] PCI: Cannot allocate resource region 5 of device 0000:00:08.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:05:09.0
[17179572.792000] PCI: Cannot allocate resource region 0 of device 0000:03:00.0
[17179572.792000] PCI: Cannot allocate resource region 3 of device 0000:03:00.0


Distro-wise, I like Ubuntu and I'm familiar with a lot of the more Debian-based things like the package manager and the structure of it, so I'd ideally like to keep with it - it works with the nv driver, but not the nvidia one which, to me, says it's a misconfiguration rather than an actual hardware problem.

---

### Post by MattKemp on 2007-01-02
Another mini-bump. Turns out the stuff above is a BIOS issue. Other than that, tried upgrading to 9746 drivers and it's exactly the same. Xorg log is a bit funky - it shows it setting the resolution to 640x480, then doing nothing. Also, with the nvidia driver the EDID data shows as corrupt, whereas it seems to find them fine with the nv driver. Any ideas?

---

