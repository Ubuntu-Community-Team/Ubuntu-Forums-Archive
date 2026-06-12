---
title: "Black screen with ATI 8.41.7 / X1950"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by aoanla on 2007-09-16
There seem to be a few posts complaining about black screens with the ATI drivers, but most of them seem very inactive - and none of them refer to the current driver, in any case.

This is with Ubuntu Feisty, fully updated.

So. I have a X1950 Pro, which was "working" (for ATI driver values of working) with the 8.39 drivers. I skipped 8.40 because apparently there was very little change for most users, but considering the hype about 8.41 I decided that I had to try it.

I followed the instructions on the Ubuntu wiki (generating an install package for Ubuntu/feisty, then using module assistant to build and install). I ensured that "fglrx" was blacklisted.
I also ensured that AIGLX and Composite were disabled in the xorg.conf.

Rebooting... gives a black screen, after the Ubuntu loading splash. It's not totally black - you actually see it switch from black to very dark grey, then back to black, then back to very dark grey, and the monitor believes that it is getting a signal. 

The monitor's status menu reports that at this point it is being driven at about 55kHz/59.9Hz at 1400x900. (Which is, according to my monitor's manual, an entirely valid mode.)

The resultant Xorg.0.log looks like:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ninhursaga 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 16 13:14:47 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
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
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
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
(II) PCI: 00:00:0: chip 1106,0351 card 1106,0351 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1351 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2351 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3351 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4351 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5351 card 0000,0000 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:6: chip 1106,6238 card 0008,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7351 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b999 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1106,a238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 1106,c238 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:03:1: chip 1106,d238 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:03:2: chip 1106,e238 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:03:3: chip 1106,f238 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:0f:0: chip 1106,0591 card 1106,0591 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1106,0571 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1106,3337 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:13:1: chip 1106,337a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 02:00:0: chip 1002,7280 card 0000,0000 rev 9a class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,72a0 card 0000,0001 rev 9a class 03,80,00 hdr 00
(II) PCI: 04:00:0: chip 1969,1048 card 1043,8226 rev b0 class 02,00,00 hdr 00
(II) PCI: 06:00:0: chip 11ab,6121 card 1043,8212 rev b1 class 01,01,8f hdr 00
(II) PCI: 80:01:0: chip 1106,3288 card 1043,81e7 rev 10 class 04,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,128), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0003 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfbc00000 - 0xfbcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:3:0), (0,6,6), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xfbe00000 - 0xfbefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:3:1), (0,5,5), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xfaf00000 - 0xfaffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:3:2), (0,4,4), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfbd00000 - 0xfbdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:3), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfae00000 - 0xfaefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 128: bridge is at (0:19:0), (0,128,128), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 128 non-prefetchable memory range:
	[0] -1	0	0xfbf00000 - 0xfbffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:19:1), (0,7,7), BCTRL: 0x0003 (VGA_EN is cleared)
(--) PCI:*(2:0:0) ATI Technologies Inc ATI Radeon X1950 Pro Primary (PCIE) rev 154, Mem @ 0xd0000000/28, 0xfbce0000/16, I/O @ 0xd000/8, BIOS @ 0xfbcc0000/17
(--) PCI: (2:0:1) ATI Technologies Inc ATI Radeon X1950 Pro Secondary (PCIE) rev 154, Mem @ 0xfbcf0000/16
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
	[0] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[1] -1	0	0xfbeffc00 - 0xfbefffff (0x400) MX[B]
	[2] -1	0	0xfbdc0000 - 0xfbdfffff (0x40000) MX[B]
	[3] -1	0	0xfbbffc00 - 0xfbbffcff (0x100) MX[B]
	[4] -1	0	0xfbcf0000 - 0xfbcfffff (0x10000) MX[B](B)
	[5] -1	0	0xfbcc0000 - 0xfbcdffff (0x20000) MX[B](B)
	[6] -1	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[9] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[11] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[12] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[14] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[16] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[22] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[1] -1	0	0xfbeffc00 - 0xfbefffff (0x400) MX[B]
	[2] -1	0	0xfbdc0000 - 0xfbdfffff (0x40000) MX[B]
	[3] -1	0	0xfbbffc00 - 0xfbbffcff (0x100) MX[B]
	[4] -1	0	0xfbcf0000 - 0xfbcfffff (0x10000) MX[B](B)
	[5] -1	0	0xfbcc0000 - 0xfbcdffff (0x20000) MX[B](B)
	[6] -1	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[9] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[11] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[12] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[14] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[16] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[22] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[5] -1	0	0xfbeffc00 - 0xfbefffff (0x400) MX[B]
	[6] -1	0	0xfbdc0000 - 0xfbdfffff (0x40000) MX[B]
	[7] -1	0	0xfbbffc00 - 0xfbbffcff (0x100) MX[B]
	[8] -1	0	0xfbcf0000 - 0xfbcfffff (0x10000) MX[B](B)
	[9] -1	0	0xfbcc0000 - 0xfbcdffff (0x20000) MX[B](B)
	[10] -1	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[15] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[17] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[20] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[28] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.41.7
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.41.7
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.413.1                  
(II) ATI Proprietary Linux Driver Build Date: Sep  7 2007 22:36:05
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7280) found
(II) AMD Video driver is running on the exact device targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[5] -1	0	0xfbeffc00 - 0xfbefffff (0x400) MX[B]
	[6] -1	0	0xfbdc0000 - 0xfbdfffff (0x40000) MX[B]
	[7] -1	0	0xfbbffc00 - 0xfbbffcff (0x100) MX[B]
	[8] -1	0	0xfbcf0000 - 0xfbcfffff (0x10000) MX[B](B)
	[9] -1	0	0xfbcc0000 - 0xfbcdffff (0x20000) MX[B](B)
	[10] -1	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[15] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[17] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[20] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[28] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7c8500
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[5] -1	0	0xfbeffc00 - 0xfbefffff (0x400) MX[B]
	[6] -1	0	0xfbdc0000 - 0xfbdfffff (0x40000) MX[B]
	[7] -1	0	0xfbbffc00 - 0xfbbffcff (0x100) MX[B]
	[8] -1	0	0xfbcf0000 - 0xfbcfffff (0x10000) MX[B](B)
	[9] -1	0	0xfbcc0000 - 0xfbcdffff (0x20000) MX[B](B)
	[10] -1	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[18] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[23] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[25] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[29] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[31] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[32] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1950 Series" (Chipset = 0x7280)
(--) fglrx(0): (PciSubVendor = 0x0000, PciSubDevice = 0x0000)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfbce0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV570
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: HSD  Model: b020  Serial#: 8647
(II) fglrx(0): Year: 2006  Week: 51
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 25
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.644 redY: 0.327   greenX: 0.289 greenY: 0.613
(II) fglrx(0): blueX: 0.142 blueY: 0.078   whiteX: 0.310 whiteY: 0.340
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #4: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) fglrx(0): #5: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
(II) fglrx(0): #6: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #7: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) fglrx(0): Serial No: 651HW2BY08647
(II) fglrx(0): Ranges: V min: 55  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: AH191
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00226420b0c7210000
(II) fglrx(0): 	33100103682819782af044a4534a9d24
(II) fglrx(0): 	144f57bfef806146714f81c081809040
(II) fglrx(0): 	904f9500950f9a29a0d0518422305098
(II) fglrx(0): 	360098ff1000001c000000ff00363531
(II) fglrx(0): 	48573242593038363437000000fd0037
(II) fglrx(0): 	4b1e530e000a202020202020000000fc
(II) fglrx(0): 	0041483139310a20202020202020006a
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 574/689MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 27 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (400, 250) mm
(--) fglrx(0): DPI set to (91, 91)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.41.7
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[7] -1	0	0xfbeffc00 - 0xfbefffff (0x400) MX[B]
	[8] -1	0	0xfbdc0000 - 0xfbdfffff (0x40000) MX[B]
	[9] -1	0	0xfbbffc00 - 0xfbbffcff (0x100) MX[B]
	[10] -1	0	0xfbcf0000 - 0xfbcfffff (0x10000) MX[B](B)
	[11] -1	0	0xfbcc0000 - 0xfbcdffff (0x20000) MX[B](B)
	[12] -1	0	0xfbce0000 - 0xfbceffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[21] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[26] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[28] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[32] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[34] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading sub module "glx"
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xd0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 7291

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b0e7c60fd40]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxModeInit+0x43) [0x2b0e7e3cd0c3]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxScreenInit+0x4a6) [0x2b0e7e3cc306]
4: /usr/X11R6/bin/X(AddScreen+0x222) [0x436652]
5: /usr/X11R6/bin/X(InitOutput+0x268) [0x465098]
6: /usr/X11R6/bin/X(main+0x275) [0x436e55]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b0e7c5fc8e4]
8: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

```

I had to hard reset to get out of this - I couldn't switch to any consoles.

Moving the xorg.conf elsewhere, to force X to detect everything itself and build a default configuration on boot, allows me to use the VESA driver (but since this doesn't support XVGA and other wide screen resolutions, it looks horrible).

The log seems to imply that this is either a problem with DRM or DRI, but I have no idea why either would have broken in this release...

Any ideas?

---

### Post by aoanla on 2007-09-18
*bump*

---

### Post by aoanla on 2007-09-19
*bump* 

Considering that this seems to be a problem affecting several people (quite a few with X1950s), I was kind of hoping someone might have suggestions...

---

### Post by inzeo on 2007-10-22
I too have an x1950 and ran into the same exact problem.  I was unable to fix it though so I'm in the same boat as you :(.  If you figure it out, please let me know and I'll do the same!

---

### Post by scottfro on 2007-10-25
i am having this issue very intermitnatly.  Some times I boot up fine other times i get the black screen after the splash.  Only way out is a hard reset.

I'm using an ATI Radeon X1950 with Envy installed drivers (so I assume they are the latest).

This is pretty much the only issue i'm having with ubuntu and would really like to solve it!

---

### Post by mrastas on 2007-10-25
Hi guys!

Don't know if you have the same problem that i did with my X600 and fglrx in the new gutsy after upgrading.

I had the black screens also and discovered that it was because of this option in device section of xorg.conf.

option forcemonitors crt1,lvds

If i do not have a crt connected while booting up, then i will get a black screen with fglrx. So i would suggest you to try to remove every fglrx option in xorg.conf and reboot.

---

### Post by scottfro on 2007-10-25
hrm nope i don't have that option in the xorg....the thing is about removing everything about fglrx and rebooting is that the issue is very intermitent.  it might happen once a day or not at all.  very odd.  any other advice?

---

