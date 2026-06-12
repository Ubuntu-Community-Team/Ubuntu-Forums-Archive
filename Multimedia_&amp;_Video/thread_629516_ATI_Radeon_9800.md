---
title: "ATI Radeon 9800"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by jesusaves on 2007-12-02
I down graded from a ATI Radeon 9800 card to an Nvidia5200 128m card, and honestly this card is garbage. I am a huge Enemy Territory nut and i can only pull 20-30 FPS in game. Now my ATI card on a windows box could pull 120 FPS with out blinking an eye. I must ask, is there any hope for ATI support in the future on Ubuntu 7.10? When I originally launched 7.10 on my box I had my ATI card in and I only got a black screen and could not pull up the GUI. 
  Now currently I am using the above mentioned nvidia card, I stripped down all of the in game graphics but still am fighting really low frame rates. I have launched compiz on this install and that seems to work great, I did shut it all off to play the game but still had low frame rates. Should I buy a faster vid card? or is there any settings that could be changed to improve the performance of the card? I want to make sure that this card is doing the best it can. On one more note, I use a 19" Flat Panel from Dell with DVI support. 

Any help or ideas would be greatly appreciated.

Thank you,

---

### Post by acoustibop on 2007-12-02
The trick to booting the Live Ubuntu CD with an ATI card is to start it in VGA mode, jesusaves.  Older cards often work anyway - my Rage Fury card (in another machine) boots without this workaround.  You can always run the text install, as well.

ATI are supposed to be becoming much more proactive with the open source community since AMD bought them out, and the last couple of drivers, the 8.42.3 fglrx and the new 7.11 (they've just changed over to Catalyst numbering) support composite and AIGLX.  My 9800 XT is running Compiz very happily.

If you have a 9800, I'd very much recommend the 7.11 driver - use the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") installation method; it works perfectly for me and, although it may look daunting, it's really only a matter of paste-and-copying lines into a terminal and making a few simple decisions, such as whether you've already installed an fglrx driver.

Or, if you really don't want to do that, install the repository driver with the Restricted Driver Manager - no expertise needed! ;)  The present repository driver is the 8.37.6.

---

### Post by jesusaves on 2007-12-02
Well let me ask this. As it stands, i have installed Ubuntu 7.10 to the hard drive and am using the Nvidia FX5200 with the nvidia driver from the repository. Number one should I try using a different driver with it to improve performance, or should I change back to the Radeon 9800? Now if I change back to the 9800, can I do that without reinstalling Ubuntu? Please understand that I am a big noob using Linux, so I may need a step by step on that procedure. 

Thank you for your time.

---

### Post by acoustibop on 2007-12-02
I've never used any Nvidia cards, jesusaves, so I can't say about that.

Yes, I think you should be able to change to the ATI card: if you remove the Nvidia drivers, then power down and swap cards, Gutsy should detect your card and install a suitable (free) driver.  I've never swapped cards in Ubuntu that would need a driver change, though, so I can't say for sure.

---

### Post by jesusaves on 2007-12-02
Thank you so much for your time on replying about this. That is the one thing that has made changing over to Linux so easy. That is the help from all of the great and talented people in this community.. people such as yourself. I feel so strongly about Linux and its success that i have built my own site to start keeping a log of all of my findings, your welcome to visit it. I figured as I grow in the knowledge of Linux so too would my site.
[http://www.whojah.com/wiki/index.php/Main_Page]("http://www.whojah.com/wiki/index.php/Main_Page")

---

### Post by LeBurt on 2007-12-02
I never has any success with ATI (I've a 9600) and 7.10. Tried every trick out there, did a couple clean installs and always ended up on the same black screen when trying the fglrx driver, no matter what version. I've given up, baffled. I keep hoping that someday, an official update will get it fixed. Realistically however, my GPU will die before that and I'll end up buying an Nvidia product as a replacement. What a shame...

---

### Post by acoustibop on 2007-12-03
How did you install the 7.10 driver, LeBurt?

---

### Post by LeBurt on 2007-12-03
I tried installing the 7.11 fglrx driver on Ubuntu 7.10 like this:

1) clean install, followed [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"). Got this Xorg.0.log, which doesn't appear to have terminated correctly:

> X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Desktopita 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec  2 20:53:50 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "Acer AL2216W"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 1039,0760 card 105b,0c54 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 105b,0c54 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 105b,0c54 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 105b,0c54 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 105b,0c54 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 105b,0c54 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 105b,0c54 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 163c,3052 card 163c,3052 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4150 card 1002,4722 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4170 card 1002,4723 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe00fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xd0000000/27, 0xe0030000/16, I/O @ 0xd000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) rev 0, Mem @ 0xd8000000/27, 0xe0020000/16
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe0124000 - 0xe0124fff (0x1000) MX[B]
	[1] -1	0	0xe0123000 - 0xe0123fff (0x1000) MX[B]
	[2] -1	0	0xe0122000 - 0xe0122fff (0x1000) MX[B]
	[3] -1	0	0xe0121000 - 0xe0121fff (0x1000) MX[B]
	[4] -1	0	0xe0120000 - 0xe0120fff (0x1000) MX[B]
	[5] -1	0	0xe0125000 - 0xe0125fff (0x1000) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xe0030000 - 0xe003ffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe0020000 - 0xe002ffff (0x10000) MX[B](B)
	[1] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe0124000 - 0xe0124fff (0x1000) MX[B]
	[1] -1	0	0xe0123000 - 0xe0123fff (0x1000) MX[B]
	[2] -1	0	0xe0122000 - 0xe0122fff (0x1000) MX[B]
	[3] -1	0	0xe0121000 - 0xe0121fff (0x1000) MX[B]
	[4] -1	0	0xe0120000 - 0xe0120fff (0x1000) MX[B]
	[5] -1	0	0xe0125000 - 0xe0125fff (0x1000) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xe0030000 - 0xe003ffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[11] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[12] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe0020000 - 0xe002ffff (0x10000) MX[B](B)
	[1] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xe0124000 - 0xe0124fff (0x1000) MX[B]
	[5] -1	0	0xe0123000 - 0xe0123fff (0x1000) MX[B]
	[6] -1	0	0xe0122000 - 0xe0122fff (0x1000) MX[B]
	[7] -1	0	0xe0121000 - 0xe0121fff (0x1000) MX[B]
	[8] -1	0	0xe0120000 - 0xe0120fff (0x1000) MX[B]
	[9] -1	0	0xe0125000 - 0xe0125fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xe0030000 - 0xe003ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0020000 - 0xe002ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.43.2
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.43.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.433                    
(II) ATI Proprietary Linux Driver Build Date: Nov  9 2007 21:19:16
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4150) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0124000 - 0xe0124fff (0x1000) MX[B]
	[5] -1	0	0xe0123000 - 0xe0123fff (0x1000) MX[B]
	[6] -1	0	0xe0122000 - 0xe0122fff (0x1000) MX[B]
	[7] -1	0	0xe0121000 - 0xe0121fff (0x1000) MX[B]
	[8] -1	0	0xe0120000 - 0xe0120fff (0x1000) MX[B]
	[9] -1	0	0xe0125000 - 0xe0125fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xe0030000 - 0xe003ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0020000 - 0xe002ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[23] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82095e0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0124000 - 0xe0124fff (0x1000) MX[B]
	[5] -1	0	0xe0123000 - 0xe0123fff (0x1000) MX[B]
	[6] -1	0	0xe0122000 - 0xe0122fff (0x1000) MX[B]
	[7] -1	0	0xe0121000 - 0xe0121fff (0x1000) MX[B]
	[8] -1	0	0xe0120000 - 0xe0120fff (0x1000) MX[B]
	[9] -1	0	0xe0125000 - 0xe0125fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xe0030000 - 0xe003ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0020000 - 0xe002ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[22] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[26] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI RADEON 9600 Series" (Chipset = 0x4150)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x4722)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe0030000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.43.2
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1646273351
(II) fglrx(0): Year: 2006  Week: 22
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
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
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) fglrx(0): Monitor name: Acer AL2216W
(II) fglrx(0): Serial No: ETL7409038
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00047274ad47232062
(II) fglrx(0): 	16100103682f1e782ec585a459499a24
(II) fglrx(0): 	125054bfef0081808140714f9500950f
(II) fglrx(0): 	b30081c08bc021399030621a274068b0
(II) fglrx(0): 	3600d9281100001c000000fd00384c1e
(II) fglrx(0): 	5215000a202020202020000000fc0041
(II) fglrx(0): 	63657220414c32323136570a000000ff
(II) fglrx(0): 	0045544c373430393033382020200006
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001

2) Clean install, used [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), got me to the same point.

---

### Post by acoustibop on 2007-12-03
I notice a line in there, LeBurt:> Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."From the 7.11 release Notes:> The ATI Catalyst&#8482; Linux software suite 7.11 does not support ATI Workstation products. AMD recommends using the AMD Catalyst&#8482; Linux software driver version 8.40.4.

---

### Post by LeBurt on 2007-12-03
Thanks for the help!

Well, I don't know why it says that, my Card is not a workstation one, it's a Radeon All-In-Wonder 9600 (based on the RV350 GPU, I think). Could the system be detecting the wrong hardware?

---

### Post by acoustibop on 2007-12-03
Either detecting the wrong hardware, or your card has an inappropriate bios, LeBurt.  I'm not sure, but I wouldn't have thought there were workstation AIW models.

ATM I use a Hauppauge card because the ATI VIVO and AIW cards are impossible to get working as such in Ubuntu.  However, I've had 9800 and 9700 AIWs working quite happily as straight videocards on this machine - the 9700 quite recently, so I probably would have been running the 8.42.3 driver on it.

Edit: I wonder if the fact that it's an AIW has anything to do with its being identified as a workstation card?

---

