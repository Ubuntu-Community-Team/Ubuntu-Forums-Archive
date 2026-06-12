---
title: "Macintel Mini + DVI to (s-video / composite adapter) = NO VIDEO"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by dimmer on 2007-04-27
Hey all, I could really use some help. I have a mac mini intel core solo with 2gb of ram.

I've wiped OS X entirely and installed ubuntu instead. I want to be able to use either svideo or composite out - so I bought the Apple DVI to Svideo / composite adapter. I tested the adapter and it works as advertised in OS X. However after I installed Ubuntu (and set everything else up), I realized in shock and horror that my video would not work through the adapter.

Video works fine through DVI or a DVI->VGA adapter.

Here's what I see through the DVI->S-video/Composite adapter from boot:
The white screen - the folder with a question mark, then immediately a black screen and then nothing else.

The machine continues to boot fine - I can remotely log in just fine and it's up and running. Just no video.

BTW, this machine is still running 6.10.  I will try feisty soon.

Any ideas? Thank you in advance!

Admin: Perhaps this post should be moved to the Apple Intel forum?  My bad.

---

### Post by dimmer on 2007-04-28
So I've upgraded to Feisty Fawn - still having the same problem.  On a side note - I was having some problems with the mac mini and the feisty boot CD (and the keyboard not responding) - this happened very often until I unplugged my wireless mouse - after which it happened seldomly.

Anyways - on with the important stuff. The upgrade to feisty went smoothly except when I rebooted the first time ubuntu did not come up.  After a power cycle ubuntu booted fine (I have had this problem before too).

Now really to the important stuff.  My video works great via DVI or analog.  But if I use the Apple s-video/composite adapter I get no video immediately after the white boot screen.

Here are the logs (may or may not be relevant)...
dmesg:
[   22.994476] PCI: Probing PCI hardware (bus 00)
[   22.995252] Boot video device is 0000:00:02.0
[   19.656000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.680000] iTCO_vendor_support: vendor-support=0
[   19.680000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.680000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0460)
[   19.680000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.704000] agpgart: Detected an Intel 945GM Chipset.
[   19.704000] agpgart: Detected 16124K stolen memory.
[   19.720000] agpgart: AGP aperture is 256M @ 0x80000000
[   19.720000] intel_rng: FWH not detected

syslog:
Apr 28 00:14:14 loki gdm[4928]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Apr 28 00:14:19 loki gdm[5185]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Apr 28 00:14:19 loki gdm[4819]: deal_with_x_crashes: Running the XKeepsCrashing script

partial Xorg:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux loki 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 28 00:14:18 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel i915"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 8086,7270 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 8086,7270 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:07:0: chip 8086,27a3 card 0000,0000 rev 03 class 11,01,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,27d8 card 8384,7680 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 8086,7270 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 8086,7270 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 8086,7270 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 8086,7270 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 8086,7270 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 8086,7270 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 8086,7270 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c4 card 8086,7270 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 8086,7270 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 11ab,4362 card 11ab,5321 rev 22 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 168c,001c card 106b,0086 rev 01 class 02,00,00 hdr 00
(II) PCI: 03:03:0: chip 11c1,5811 card 11c1,5811 rev 61 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x90500000 - 0x905fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x90100000 - 0x901fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x90000000 - 0x900fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0x90380000/19, 0x80000000/28, 0x90400000/18, I/O @ 0x20f0/3
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
	[0] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[1] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[2] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[3] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[4] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[5] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[6] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[7] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[8] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[12] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[13] -1	0	0x000020f8 - 0x000020fb (0x4) IX[B]
	[14] -1	0	0x000020d0 - 0x000020d7 (0x8) IX[B]
	[15] -1	0	0x000020fc - 0x000020ff (0x4) IX[B]
	[16] -1	0	0x000020d8 - 0x000020df (0x8) IX[B]
	[17] -1	0	0x000020c0 - 0x000020cf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[23] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[24] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[25] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[26] -1	0	0x000020f0 - 0x000020f7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[1] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[2] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[3] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[4] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[5] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[6] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[7] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[8] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[12] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[13] -1	0	0x000020f8 - 0x000020fb (0x4) IX[B]
	[14] -1	0	0x000020d0 - 0x000020d7 (0x8) IX[B]
	[15] -1	0	0x000020fc - 0x000020ff (0x4) IX[B]
	[16] -1	0	0x000020d8 - 0x000020df (0x8) IX[B]
	[17] -1	0	0x000020c0 - 0x000020cf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[23] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[24] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[25] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[26] -1	0	0x000020f0 - 0x000020f7 (0x8) IX[B](B)
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
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[18] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[19] -1	0	0x000020f8 - 0x000020fb (0x4) IX[B]
	[20] -1	0	0x000020d0 - 0x000020d7 (0x8) IX[B]
	[21] -1	0	0x000020fc - 0x000020ff (0x4) IX[B]
	[22] -1	0	0x000020d8 - 0x000020df (0x8) IX[B]
	[23] -1	0	0x000020c0 - 0x000020cf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[29] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[30] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[31] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[32] -1	0	0x000020f0 - 0x000020f7 (0x8) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(--) Chipset 945GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[18] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[19] -1	0	0x000020f8 - 0x000020fb (0x4) IX[B]
	[20] -1	0	0x000020d0 - 0x000020d7 (0x8) IX[B]
	[21] -1	0	0x000020fc - 0x000020ff (0x4) IX[B]
	[22] -1	0	0x000020d8 - 0x000020df (0x8) IX[B]
	[23] -1	0	0x000020c0 - 0x000020cf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[29] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[30] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[31] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[32] -1	0	0x000020f0 - 0x000020f7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90100000 - 0x9010ffff (0x10000) MX[B]
	[6] -1	0	0x90200000 - 0x90203fff (0x4000) MX[B]
	[7] -1	0	0x90445000 - 0x904453ff (0x400) MX[B]
	[8] -1	0	0x90445400 - 0x904457ff (0x400) MX[B]
	[9] -1	0	0x90440000 - 0x90443fff (0x4000) MX[B]
	[10] -1	0	0x90444000 - 0x90444fff (0x1000) MX[B]
	[11] -1	0	0x90400000 - 0x9043ffff (0x40000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0x90380000 - 0x903fffff (0x80000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[20] -1	0	0x0000efa0 - 0x0000efbf (0x20) IX[B]
	[21] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[22] -1	0	0x000020f8 - 0x000020fb (0x4) IX[B]
	[23] -1	0	0x000020d0 - 0x000020d7 (0x8) IX[B]
	[24] -1	0	0x000020fc - 0x000020ff (0x4) IX[B]
	[25] -1	0	0x000020d8 - 0x000020df (0x8) IX[B]
	[26] -1	0	0x000020c0 - 0x000020cf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[32] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[33] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[34] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[35] -1	0	0x000020f0 - 0x000020f7 (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16064 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) I810(0): Chipset: "945GM"
(--) I810(0): Linear framebuffer at 0x80000000
(--) I810(0): IO registers at addr 0x90380000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 16124 kB stolen memory.
(II) I810(0): Kernel reported 483584 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 1934332 kB available
(II) I810(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) I810(0): Monitoring connected displays enabled
(--) I810(0): Pre-allocated VideoRAM: 16124 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1284
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: TRUE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: TRUE, present: TRUE, size: (1,1)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,1543)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,1543)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,1543)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,1543)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,1543)
(II) I810(0): Size of device DFP (digital flat panel) is 1 x 1
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	DFP (digital flat panel)
(II) I810(0): Lowest common panel size for pipe A is 1 x 1
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: APP  Model: 9d08  Serial#: 16843009
(II) I810(0): Year: 2002  Week: 7
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Signal levels configurable
(II) I810(0): Sync:
(II) I810(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) I810(0): Gamma: 2.50
(II) I810(0): DPMS capabilities: Off; Non RGB Multicolor Display
(II) I810(0): First detailed timing not preferred mode in violation of standard!(II) I810(0): redX: 0.626 redY: 0.338   greenX: 0.278 greenY: 0.601
(II) I810(0): blueX: 0.150 blueY: 0.068   whiteX: 0.283 whiteY: 0.298
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): Manufacturer's mask: 61
(II) I810(0): Monitor name: NTSC/PAL
(II) I810(0): EDID (in hex):
(II) I810(0): 	00ffffffffffff000610089d01010101
(II) I810(0): 	070c0103100000963067a9a056479926
(II) I810(0): 	11484c00006101010101010101010101
(II) I810(0): 	01010101010101010101010101010101
(II) I810(0): 	01010101010101010101010101010101
(II) I810(0): 	01010101010101010101010101010101
(II) I810(0): 	010101010101010101010101000000fc
(II) I810(0): 	004e5453432f50414c0a202020200038
(II) I810(0): DDCModeFromDetailedTiming: 1x1 Warning: We only handle seperate sync.
(II) I810(0): DDCModeFromDetailedTiming: 1x1 Warning: We only handle seperate sync.
(II) I810(0): DDCModeFromDetailedTiming: 1x1 Warning: We only handle seperate sync.
(II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): Modeline "1x1"    2.57  1 2 3 258  1 1 18 258 -hsync -vsync
(II) I810(0): Modeline "1x1"    2.57  1 2 3 258  1 1 18 258 -hsync -vsync
(II) I810(0): Modeline "1x1"    2.57  1 2 3 258  1 1 18 258 -hsync -vsync
(--) I810(0): A non-CRT device is attached to pipe A.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 16064 kByte
(EE) I810(0): No Video BIOS modes for chosen depth.
(II) UnloadModule: "i810"
(II) UnloadModule: "ddc"
(II) UnloadModule: "vm86"
(II) Unloading /usr/lib/xorg/modules//libvm86.so
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

I'd be happy to provide any further information.
Thanks!

---

### Post by dimmer on 2007-05-20
This is now working on Ubuntu Feisty Fawn.  I don't think I did anything special to get it working. Although it's been a while and I can't quite remember. Basically it doesn't show any video until X11 starts, then video works fine. This is fine as long as I don't need to regularly watch ubuntu booting or shutting down.

Just for reference here are the relevant (or possibly irrelevant) parts of my xorg.conf:
```

Section "Device"
        Identifier      "Intel i915"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
        Option      "TVStandard" "NTSC"
        Option      "TVOutFormat" "COMPOSITE"
        Option      "TVOverScan" "0.6"
        Option      "ConnectedMonitor" "TV" # Add this if you're having problems
        Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


```

This just really shows that FSM helps those who help themselves.

---

