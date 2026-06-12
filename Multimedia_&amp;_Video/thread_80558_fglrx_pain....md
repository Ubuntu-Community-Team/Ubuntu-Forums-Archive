---
title: "fglrx pain..."
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by AnObfuscator on 2005-10-22
Hi -- 
I'm a linux newb, and I just got my new AMD64 system running a few days ago. I'm using the x86-64 build of breezy, and I just can't get the damn fglrx drivers to work.

I have followed the instructions [here]("http://ubuntuforums.org/showthread.php?p=408111") to the letter, 3 times, and each time, it fails in the same way. 

when I change my driver from ati to fglrx, xorg fails to start, and dumps me to the CLI. I saved a copy of the logfile, in case any of it is relevant -- but I couldn't make heads or tails of it.

 when I change the driver back to ATi, it loads X fine. fglrxinfo gives me a error:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

I've gone through several other threads on this forum, but can't make heads or tails of what i should do next. :/

Please help!

---

### Post by mlomker on 2005-10-22
You should post your Xorg.0.log file from one of the failed attempts and we'll see what it says.

---

### Post by jecos on 2005-10-22
[QUOTE=AnObfuscator]Hi -- 
I'm a linux newb, and I just got my new AMD64 system running a few days ago. I'm using the x86-64 build of breezy, and I just can't get the damn fglrx drivers to work.

I have followed the instructions [here]("http://ubuntuforums.org/showthread.php?p=408111") to the letter, 3 times, and each time, it fails in the same way. 

when I change my driver from ati to fglrx, xorg fails to start, and dumps me to the CLI. I saved a copy of the logfile, in case any of it is relevant -- but I couldn't make heads or tails of it.

 when I change the driver back to ATi, it loads X fine. fglrxinfo gives me a error:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

I've gone through several other threads on this forum, but can't make heads or tails of what i should do next. :/

Please help![/QUOTE]

I don't recommend AMD64 at this time..  many things don't work, and will take time to get working. 32bit breezy will run just as fast and everything should work. There is a bug in the amd64 breezy dri, you need a file from older version. 

Its foolish to run amd64 right now when your new to linux, b/c working around the issues takes knowledge that you wouldn't have yet.

---

### Post by AnObfuscator on 2005-10-22
[QUOTE=mlomker]You should post your Xorg.0.log file from one of the failed attempts and we'll see what it says.[/QUOTE]

Ok, here goes:

```



X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux Tintagel 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:27:39 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 22 13:46:42 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1458,e000 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:08:0: chip 168c,001a card 1186,3a16 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xf7ffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800] rev 0, Mem @ 0xe8000000/27, 0xfb000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary) rev 0, Mem @ 0xf0000000/27, 0xfb010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xf9ffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfc000000 - 0xfc00ffff (0x10000) MX[B]
	[1] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[2] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[3] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[4] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[5] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfb010000 - 0xfb01ffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfb00ffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[14] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[15] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[16] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfc000000 - 0xfc00ffff (0x10000) MX[B]
	[1] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[2] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[3] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[4] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[5] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfb010000 - 0xfb01ffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfb00ffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[14] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[15] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[16] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfc000000 - 0xfc00ffff (0x10000) MX[B]
	[6] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[7] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[8] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[9] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[10] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfb010000 - 0xfb01ffff (0x10000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfb00ffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[28] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[29] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure


Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.




```

---

### Post by AnObfuscator on 2005-10-22
[QUOTE=jecos]I don't recommend AMD64 at this time..  many things don't work, and will take time to get working. 32bit breezy will run just as fast and everything should work. There is a bug in the amd64 breezy dri, you need a file from older version. [/quote]

Right, in the howto, the dude posted the file, which i copied to my X11 library, as insructed, but still nada.

> 
Its foolish to run amd64 right now when your new to linux, b/c working around the issues takes knowledge that you wouldn't have yet.

... unless Linux is not "mission critical" for me, and part of the reason I'm using it is to learn. ;)

If I really have to do something on my box, I can just boot WinXP and do it in there.

Either way, I have my trusty Powerbook, which functions nicely as my primary computer.

If I get too damn frustrated, though, yeah, I'll just reinstall 32bit. I so relish the idea of a true 64bit environment, though...

---

### Post by mlomker on 2005-10-22
> Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o

Re-read the troubleshooting section of the how-to.  This error is specifically listed.

Post your /etc/X11/xorg.conf file if you've already commented out the int10a line.

---

### Post by AnObfuscator on 2005-10-22
[QUOTE=mlomker]Re-read the troubleshooting section of the how-to.  This error is specifically listed.

Post your /etc/X11/xorg.conf file if you've already commented out the int10a line.[/QUOTE]

ok, I tried commenting out that line. X starts without complaining when I select fglrx, and fglrxinfo doesn't return an error, but it still returns mesa drivers.

here's xorg.conf:
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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	#Load	"int10"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by mlomker on 2005-10-22
> I tried commenting out that line. X starts without complaining when I select fglrx, and fglrxinfo doesn't return an error, but it still returns mesa drivers.


I'm just a nerd, not a miracle worker.  ;)

Seriously, though, you'll want to look for errors.

```

dmesg | grep fglrx

```

And then look through the Xorg.0.log file again.  Only owners of 9550 cards seem to still be having problems.  What card do you have?

---

### Post by AnObfuscator on 2005-10-22
> **mlomker]I'm just a nerd, not a miracle worker.   said:**
> 

Oh, oh, I see.. er, I don't suppose you have a line for a linux god, or maybe demi-god? ;) 


[quote]
Seriously, though, you'll want to look for errors.

```

dmesg | grep fglrx

```

And then look through the Xorg.0.log file again.  Only owners of 9550 cards seem to still be having problems.  What card do you have?

I have a 9800 Pro.

```
onering@Tintagel:~$ dmesg | grep fglrx
[   75.936646] [fglrx] Maximum main memory to use for locked dma buffers: 853 MBytes.
[   75.936980] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[   75.951641] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[   75.953561] [fglrx:firegl_unlock] *ERROR* Process 7286 using kernel context 0
```

---

### Post by phup on 2005-10-22
I have 9800 pro as well, (but regular old 32 bit architecture so dunno if that makes a difference)

I installed the xorg-driver-fglrx package, the restricted package for my system, and the fglrx-config package.  I made a backup copy of my xorg.conf file and ran fglrxconfig to generate a new xorg.conf (i went pretty much with the default options except a couple of cases where i was absolutely certain there was a better choice). 

Comparing the old xorg.conf and the one generated, the only thing I decided to change was to put the FontPath information back in.  This was my ultimate xorg.conf ( took out a lot of commented lines for this post)

```

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
   [B] SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection[/B]

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection


# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present



# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"

    Identifier  "Server Layout"

    Screen "Screen0"

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

```

Anyway, I don't know what most of that stuff does, I don't know if I need the modules it took out (haven't noticed any probs), but I do know that when I tried to modify the config file by hand, I got various errors/freezings.  The fglrxconfig generated config file worked without modification (even though i did make a few changes (Both internal and external AGPGART work for me and provide pretty much the same frame rates.  Some seem to need to use one or the other)).

For more info, check out [this thread]("http://ubuntuforums.org/showthread.php?t=24557").

hope that helps.

---

### Post by mlomker on 2005-10-23
> firegl_unlock

That's the same error that the 9550 users are getting.  If you search on that error you'll find some threads.

Is your card ATI branded or one of the 3rd party/repackaged cards?  I'm wondering if there's a pattern as to what cards aren't working.

---

### Post by AnObfuscator on 2005-10-23
[QUOTE=mlomker]That's the same error that the 9550 users are getting.  If you search on that error you'll find some threads. [/quote]

really? I did some searching over the last hour, and haven't found that string yet. Ok, I'll keep digging.

> 
Is your card ATI branded or one of the 3rd party/repackaged cards?  I'm wondering if there's a pattern as to what cards aren't working.

Yes indeed, it's ATI branded. 

btw, I've been reading quite a few other threads on here with these problems, and let me take a second to say, thanks for all the work you've done on this problem. 

Linux is quite different from the MacOS/Windows world i'm used to, so having even-handed and helpful responses (even to questions that have been asked a thousand times ;) makes Ubuntu far more accessable than distros whose idea of help is, "OMG WTF BBQ RTFM U N00B!!!11one"... ;)

---

### Post by mlomker on 2005-10-23
> btw, I've been reading quite a few other threads on here with these problems, and let me take a second to say, thanks for all the work you've done on this problem. 


This is [the thread]("http://www.ubuntuforums.org/showthread.php?t=76147") that I was thinking of--the same unlock error.  I'm not sure what the answer is yet...maybe you all have the same motherboard chipset or something like that?  There must be some common element that is causing this problem.

---

### Post by AnObfuscator on 2005-10-23
[QUOTE=mlomker]This is [the thread]("http://www.ubuntuforums.org/showthread.php?t=76147") that I was thinking of--the same unlock error.  I'm not sure what the answer is yet...maybe you all have the same motherboard chipset or something like that?  There must be some common element that is causing this problem.[/QUOTE]

Interesting. I have a Gigabyte K8NS Socket 754 mobo, it's the Nvidia nForce3 250 chipset. 

hmmm. I've been doing some research on other distros, and there is an identical problem described in Fedora core 3 [here]("http://forums.fedoraforum.org/showpost.php?p=365700&postcount=56").

it seems the problem in Fedora is in, um, mismatched driver and kernel interface versions...?

Also, there is a potential problem with... AGP aperture?

*shrugs*

Overall, though, his howto is identical in form to yours.

---

