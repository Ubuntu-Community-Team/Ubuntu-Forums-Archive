---
title: "SLOW log in and painfully slow log out."
date: 2007-11-07
forum: Mythbuntu
---

### Post by Daminator on 2007-11-07
Hello all,

I have a problem that I'm not sure if it happened directly after adding Mythbuntu to my Ubuntu+Myth boxes or if it's just a coincidence, but now, when the log in screen should come up, I get a spinning mouse cursor for about 4 minuted before the log in screen actually comes onto screen.

When I log out, it seems to log out fine, then goes to the same cream background and spinning mouse cursor (which use to be there for 3 seconds tops) for about 7 minutes before the log in screen pops up.

Is there anyway of finding out what's going on behind the gui when this long delay is happening?

Is there any way to remove Mythbuntu but leave Ubuntu and MythTV on my system for the sake of trouble shooting?

Cheers
Damian

---

### Post by superm1 on 2007-11-07
Are you using NFS home directories?

Check out /var/log/Xorg.0.log
/var/log/gdm/
and ~/.xsession-errors for more information and to debug.

You didn't turn on the Xfce splash screen did you?

---

### Post by Daminator on 2007-11-08
If NFS home directories means are they on a network, then the answer is no. They're all local to the machine. The only network use is to the MythTV Backend machine.

Here's my /var/log/Xorg.0.log:


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux cait-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  8 23:55:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Radeon R250 [Mobility Radeon 9200]"
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
(II) PCI: 00:00:0: chip 8086,3340 card 0e11,0860 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 0e11,0860 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 0e11,0860 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 0e11,0860 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 0e11,0860 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 0e11,0860 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 0e11,0860 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 0e11,0860 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 0e11,0860 rev 01 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4c66 card 0e11,0860 rev 01 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:01:0: chip 10ec,8139 card 0e11,0860 rev 20 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 8086,1043 card 8086,2522 rev 04 class 02,80,00 hdr 00
(II) PCI: 02:04:0: chip 1524,1410 card 2800,0000 rev 00 class 06,07,00 hdr 02
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x90400000 - 0x904fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x90000000 - 0x903fffff (0x400000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x33ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[1] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x33ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] rev 1, Mem @ 0x98000000/27, 0x90400000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xb0000000 from 0xbfffffff to 0xafffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[1] -1	0	0x90300000 - 0x903000ff (0x100) MX[B]
	[2] -1	0	0x90200000 - 0x902007ff (0x800) MX[B]
	[3] -1	0	0xa0300000 - 0xa03000ff (0x100) MX[B]
	[4] -1	0	0xa0200000 - 0xa02001ff (0x200) MX[B]
	[5] -1	0	0x34000000 - 0x340003ff (0x400) MX[B]
	[6] -1	0	0xa0000000 - 0xa00003ff (0x400) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0x90400000 - 0x9040ffff (0x10000) MX[B](B)
	[9] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[11] -1	0	0x00002400 - 0x0000247f (0x80) IX[B]
	[12] -1	0	0x00004800 - 0x0000487f (0x80) IX[B]
	[13] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[14] -1	0	0x00004880 - 0x000048bf (0x40) IX[B]
	[15] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[16] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[17] -1	0	0x00004c40 - 0x00004c4f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[23] -1	0	0x000048e0 - 0x000048ff (0x20) IX[B]
	[24] -1	0	0x000048c0 - 0x000048df (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[1] -1	0	0x90300000 - 0x903000ff (0x100) MX[B]
	[2] -1	0	0x90200000 - 0x902007ff (0x800) MX[B]
	[3] -1	0	0xa0300000 - 0xa03000ff (0x100) MX[B]
	[4] -1	0	0xa0200000 - 0xa02001ff (0x200) MX[B]
	[5] -1	0	0x34000000 - 0x340003ff (0x400) MX[B]
	[6] -1	0	0xa0000000 - 0xa00003ff (0x400) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0x90400000 - 0x9040ffff (0x10000) MX[B](B)
	[9] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[11] -1	0	0x00002400 - 0x0000247f (0x80) IX[B]
	[12] -1	0	0x00004800 - 0x0000487f (0x80) IX[B]
	[13] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[14] -1	0	0x00004880 - 0x000048bf (0x40) IX[B]
	[15] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[16] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[17] -1	0	0x00004c40 - 0x00004c4f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[23] -1	0	0x000048e0 - 0x000048ff (0x20) IX[B]
	[24] -1	0	0x000048c0 - 0x000048df (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90300000 - 0x903000ff (0x100) MX[B]
	[6] -1	0	0x90200000 - 0x902007ff (0x800) MX[B]
	[7] -1	0	0xa0300000 - 0xa03000ff (0x100) MX[B]
	[8] -1	0	0xa0200000 - 0xa02001ff (0x200) MX[B]
	[9] -1	0	0x34000000 - 0x340003ff (0x400) MX[B]
	[10] -1	0	0xa0000000 - 0xa00003ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0x90400000 - 0x9040ffff (0x10000) MX[B](B)
	[13] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[17] -1	0	0x00002400 - 0x0000247f (0x80) IX[B]
	[18] -1	0	0x00004800 - 0x0000487f (0x80) IX[B]
	[19] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[20] -1	0	0x00004880 - 0x000048bf (0x40) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[23] -1	0	0x00004c40 - 0x00004c4f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[29] -1	0	0x000048e0 - 0x000048ff (0x20) IX[B]
	[30] -1	0	0x000048c0 - 0x000048df (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
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
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90300000 - 0x903000ff (0x100) MX[B]
	[6] -1	0	0x90200000 - 0x902007ff (0x800) MX[B]
	[7] -1	0	0xa0300000 - 0xa03000ff (0x100) MX[B]
	[8] -1	0	0xa0200000 - 0xa02001ff (0x200) MX[B]
	[9] -1	0	0x34000000 - 0x340003ff (0x400) MX[B]
	[10] -1	0	0xa0000000 - 0xa00003ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0x90400000 - 0x9040ffff (0x10000) MX[B](B)
	[13] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[17] -1	0	0x00002400 - 0x0000247f (0x80) IX[B]
	[18] -1	0	0x00004800 - 0x0000487f (0x80) IX[B]
	[19] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[20] -1	0	0x00004880 - 0x000048bf (0x40) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[23] -1	0	0x00004c40 - 0x00004c4f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[29] -1	0	0x000048e0 - 0x000048ff (0x20) IX[B]
	[30] -1	0	0x000048c0 - 0x000048df (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90300000 - 0x903000ff (0x100) MX[B]
	[6] -1	0	0x90200000 - 0x902007ff (0x800) MX[B]
	[7] -1	0	0xa0300000 - 0xa03000ff (0x100) MX[B]
	[8] -1	0	0xa0200000 - 0xa02001ff (0x200) MX[B]
	[9] -1	0	0x34000000 - 0x340003ff (0x400) MX[B]
	[10] -1	0	0xa0000000 - 0xa00003ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0x90400000 - 0x9040ffff (0x10000) MX[B](B)
	[13] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x00002400 - 0x0000247f (0x80) IX[B]
	[21] -1	0	0x00004800 - 0x0000487f (0x80) IX[B]
	[22] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[23] -1	0	0x00004880 - 0x000048bf (0x40) IX[B]
	[24] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[25] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c4f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[32] -1	0	0x000048e0 - 0x000048ff (0x20) IX[B]
	[33] -1	0	0x000048c0 - 0x000048df (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: ATI MOBILITY RADEON 9200
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: M9  
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 24, (--) framebuffer bpp 24
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 2 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: LGP  Model: 0  Serial#: 0
(II) VESA(0): Year: 2003  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.585 redY: 0.324   greenX: 0.319 greenY: 0.545
(II) VESA(0): blueX: 0.149 blueY: 0.135   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1408 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 816 v_border: 0
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0030f0000000000000
(II) VESA(0): 	000d0103802115780ace609553518b26
(II) VESA(0): 	22505400000001010101010101010101
(II) VESA(0): 	010101010101ea1a0080502010301520
(II) VESA(0): 	44004bcf100000190000000f00000000
(II) VESA(0): 	0000000000324a041400000000100000
(II) VESA(0): 	00000000000000000000000000000010
(II) VESA(0): 	000000000000000000000000000000fc
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 182 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 10d (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 10f (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 192 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 194 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1a2 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 400
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1a3 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1a4 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 1a5 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1200
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1a6 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1600
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1b2 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1b4 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1536
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 112
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1c2 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1c4 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 92
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 184 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 110 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 112 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 52
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 113 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 115 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2400
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 45
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 116 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
*Mode: 118 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 3072
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 119 (1280x1024)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 11a (1280x1024)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 11b (1280x1024)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 3840
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 124 (1280x1024)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 140 (1400x1050)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1400
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 43
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 141 (1400x1050)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 21
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 142 (1400x1050)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 21
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 143 (1400x1050)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 4200
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 144 (1400x1050)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 5600
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 172 (1600x1200)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 173 (1600x1200)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 174 (1600x1200)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 175 (1600x1200)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 4800
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000
Mode: 176 (1600x1200)
	ModeAttributes: 0xba
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00051c6
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x98000000

(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(II) VESA(0): Generic Monitor: Using hsync range of 28.00-50.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-75.00 Hz
(II) VESA(0): Not using mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Generic Monitor: Using hsync range of 28.00-50.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-75.00 Hz
(II) VESA(0): Not using mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "400x300" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "512x384"
(++) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90000fff (0x1000) MX[B]
	[5] -1	0	0x90300000 - 0x903000ff (0x100) MX[B]
	[6] -1	0	0x90200000 - 0x902007ff (0x800) MX[B]
	[7] -1	0	0xa0300000 - 0xa03000ff (0x100) MX[B]
	[8] -1	0	0xa0200000 - 0xa02001ff (0x200) MX[B]
	[9] -1	0	0x34000000 - 0x340003ff (0x400) MX[B]
	[10] -1	0	0xa0000000 - 0xa00003ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[12] -1	0	0x90400000 - 0x9040ffff (0x10000) MX[B](B)
	[13] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x00002400 - 0x0000247f (0x80) IX[B]
	[21] -1	0	0x00004800 - 0x0000487f (0x80) IX[B]
	[22] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[23] -1	0	0x00004880 - 0x000048bf (0x40) IX[B]
	[24] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[25] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c4f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[32] -1	0	0x000048e0 - 0x000048ff (0x20) IX[B]
	[33] -1	0	0x000048c0 - 0x000048df (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: ATI MOBILITY RADEON 9200
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: M9  
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0x98000000,0x4000000)
(II) VESA(0): virtual address = 0xb39f8000,
	physical address = 0x98000000, size = 67108864
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(WW) VESA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
SetGrabKeysState - disabled
SetGrabKeysState - enabled



Here's my /var/log/gdm/0.log:


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux cait-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  8 23:55:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(EE) AIGLX: Screen 0 is not DRI capable
Atom 4, CARD32 4, unsigned long 4
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
SetGrabKeysState - disabled
SetGrabKeysState - enabled



and here's my ~/.xsession-errors file:



(process:7549): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:7553): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)
Warning:          No symbols defined for <FK13> (keycode 118)
Warning:          No symbols defined for <FK14> (keycode 119)
Warning:          No symbols defined for <FK15> (keycode 120)
Warning:          No symbols defined for <FK16> (keycode 121)
Warning:          No symbols defined for <FK17> (keycode 122)
Warning:          No symbols defined for <KPDC> (keycode 123)
Warning:          No symbols defined for <XFER> (keycode 129)
Warning:          No symbols defined for <I02> (keycode 130)
Warning:          No symbols defined for <NFER> (keycode 131)
Warning:          No symbols defined for <I04> (keycode 132)
Warning:          No symbols defined for <AE13> (keycode 133)
Warning:          No symbols defined for <I06> (keycode 134)
Warning:          No symbols defined for <I07> (keycode 135)
Warning:          No symbols defined for <I08> (keycode 136)
Warning:          No symbols defined for <I09> (keycode 137)
Warning:          No symbols defined for <I0A> (keycode 138)
Warning:          No symbols defined for <I0B> (keycode 139)
Warning:          No symbols defined for <I0C> (keycode 140)
Warning:          No symbols defined for <I0D> (keycode 141)
Warning:          No symbols defined for <I0E> (keycode 142)
Warning:          No symbols defined for <I0F> (keycode 143)
Warning:          No symbols defined for <I10> (keycode 144)
Warning:          No symbols defined for <I11> (keycode 145)
Warning:          No symbols defined for <I12> (keycode 146)
Warning:          No symbols defined for <I13> (keycode 147)
Warning:          No symbols defined for <I14> (keycode 148)
Warning:          No symbols defined for <I15> (keycode 149)
Warning:          No symbols defined for <I16> (keycode 150)
Warning:          No symbols defined for <I17> (keycode 151)
Warning:          No symbols defined for <I18> (keycode 152)
Warning:          No symbols defined for <I19> (keycode 153)
Warning:          No symbols defined for <I1A> (keycode 154)
Warning:          No symbols defined for <I1B> (keycode 155)
Warning:          No symbols defined for <K59> (keycode 157)
Warning:          No symbols defined for <I1E> (keycode 158)
Warning:          No symbols defined for <I1F> (keycode 159)
Warning:          No symbols defined for <I20> (keycode 160)
Warning:          No symbols defined for <I21> (keycode 161)
Warning:          No symbols defined for <I22> (keycode 162)
Warning:          No symbols defined for <I23> (keycode 163)
Warning:          No symbols defined for <I24> (keycode 164)
Warning:          No symbols defined for <I25> (keycode 165)
Warning:          No symbols defined for <I26> (keycode 166)
Warning:          No symbols defined for <I27> (keycode 167)
Warning:          No symbols defined for <I28> (keycode 168)
Warning:          No symbols defined for <I29> (keycode 169)
Warning:          No symbols defined for <K5A> (keycode 170)
Warning:          No symbols defined for <I2B> (keycode 171)
Warning:          No symbols defined for <I2C> (keycode 172)
Warning:          No symbols defined for <I2D> (keycode 173)
Warning:          No symbols defined for <I2E> (keycode 174)
Warning:          No symbols defined for <I2F> (keycode 175)
Warning:          No symbols defined for <I30> (keycode 176)
Warning:          No symbols defined for <I31> (keycode 177)
Warning:          No symbols defined for <I32> (keycode 178)
Warning:          No symbols defined for <I33> (keycode 179)
Warning:          No symbols defined for <I34> (keycode 180)
Warning:          No symbols defined for <K5B> (keycode 181)
Warning:          No symbols defined for <K5D> (keycode 182)
Warning:          No symbols defined for <K5E> (keycode 183)
Warning:          No symbols defined for <K5F> (keycode 184)
Warning:          No symbols defined for <I39> (keycode 185)
Warning:          No symbols defined for <I3A> (keycode 186)
Warning:          No symbols defined for <I3B> (keycode 187)
Warning:          No symbols defined for <I3C> (keycode 188)
Warning:          No symbols defined for <K62> (keycode 189)
Warning:          No symbols defined for <K63> (keycode 190)
Warning:          No symbols defined for <K64> (keycode 191)
Warning:          No symbols defined for <K65> (keycode 192)
Warning:          No symbols defined for <K66> (keycode 193)
Warning:          No symbols defined for <I42> (keycode 194)
Warning:          No symbols defined for <I43> (keycode 195)
Warning:          No symbols defined for <I44> (keycode 196)
Warning:          No symbols defined for <I45> (keycode 197)
Warning:          No symbols defined for <K67> (keycode 198)
Warning:          No symbols defined for <K68> (keycode 199)
Warning:          No symbols defined for <K69> (keycode 200)
Warning:          No symbols defined for <K6A> (keycode 201)
Warning:          No symbols defined for <I4A> (keycode 202)
Warning:          No symbols defined for <K6B> (keycode 203)
Warning:          No symbols defined for <K6C> (keycode 204)
Warning:          No symbols defined for <K6D> (keycode 205)
Warning:          No symbols defined for <K6E> (keycode 206)
Warning:          No symbols defined for <K6F> (keycode 207)
Warning:          No symbols defined for <HKTG> (keycode 208)
Warning:          No symbols defined for <K71> (keycode 209)
Warning:          No symbols defined for <K72> (keycode 210)
Warning:          No symbols defined for <AB11> (keycode 211)
Warning:          No symbols defined for <I54> (keycode 212)
Warning:          No symbols defined for <I55> (keycode 213)
Warning:          No symbols defined for <I56> (keycode 214)
Warning:          No symbols defined for <I57> (keycode 215)
Warning:          No symbols defined for <I58> (keycode 216)
Warning:          No symbols defined for <I59> (keycode 217)
Warning:          No symbols defined for <I5A> (keycode 218)
Warning:          No symbols defined for <K74> (keycode 219)
Warning:          No symbols defined for <K75> (keycode 220)
Warning:          No symbols defined for <K76> (keycode 221)
Warning:          No symbols defined for <I5E> (keycode 222)
Warning:          No symbols defined for <I5F> (keycode 223)
Warning:          No symbols defined for <I60> (keycode 224)
Warning:          No symbols defined for <I61> (keycode 225)
Warning:          No symbols defined for <I62> (keycode 226)
Warning:          No symbols defined for <I63> (keycode 227)
Warning:          No symbols defined for <I64> (keycode 228)
Warning:          No symbols defined for <I65> (keycode 229)
Warning:          No symbols defined for <I66> (keycode 230)
Warning:          No symbols defined for <I67> (keycode 231)
Warning:          No symbols defined for <I68> (keycode 232)
Warning:          No symbols defined for <I69> (keycode 233)
Warning:          No symbols defined for <I6A> (keycode 234)
Warning:          No symbols defined for <I6B> (keycode 235)
Warning:          No symbols defined for <I6C> (keycode 236)
Warning:          No symbols defined for <I6D> (keycode 237)
Warning:          No symbols defined for <I6E> (keycode 238)
Warning:          No symbols defined for <I6F> (keycode 239)
Warning:          No symbols defined for <I70> (keycode 240)
Warning:          No symbols defined for <I71> (keycode 241)
Warning:          No symbols defined for <I72> (keycode 242)
Warning:          No symbols defined for <I73> (keycode 243)
Warning:          No symbols defined for <I74> (keycode 244)
Warning:          No symbols defined for <I75> (keycode 245)
Warning:          No symbols defined for <I76> (keycode 246)
Warning:          No symbols defined for <I77> (keycode 247)
Warning:          No symbols defined for <I78> (keycode 248)
Warning:          No symbols defined for <I79> (keycode 249)
Warning:          No symbols defined for <I7A> (keycode 250)
Warning:          No symbols defined for <I7B> (keycode 251)
Warning:          No symbols defined for <I7C> (keycode 252)
Warning:          No symbols defined for <I7D> (keycode 253)
Warning:          No symbols defined for <I7E> (keycode 254)
Warning:          No symbols defined for <I7F> (keycode 255)
** Message: Querying Xkb extension
** Message: Xkb extension found

** (update-notifier:7621): WARNING **: not starting because user is not in admin group



Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0



Any idea what's going on?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-08
Hi Damian,

[QUOTE=Daminator]
Is there anyway of finding out what's going on behind the gui when this long delay is happening?
[/QUOTE]
While loading the login, you can press Ctrl+Alt+F1 to switch to TTY and login there, enter command 'top' to see which process is loading.
Press Alt-F7 to back to the X login.
Additionally, you can see which process that have high CPU loading (if any).

Regardless the X errors, I might had the same problem as yours (slow login), do you have many fonts in your /home/yourname/.fonts directory?
I solved my problem by removing the fonts I put in .fonts directory.

---

### Post by Daminator on 2007-11-12
I think I found the problem,

System/Login window/General/Default session had changed to Mythbuntu session. Changing that back to Gnome got things loading up in a few seconds rather than a few minutes.

Loging out for a different user to log in still takes a few seconds longer than I'd like. Is there any way to speed that up?

Damian

---

