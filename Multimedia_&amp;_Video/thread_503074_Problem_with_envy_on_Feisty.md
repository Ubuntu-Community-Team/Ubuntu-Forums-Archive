---
title: "Problem with envy on Feisty"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by fatsheep on 2007-07-17
I have a fresh install of Ubuntu Feisty 7.04 (64-bit) on a new computer with a Intel Core Duo E6420 processor, Nvidia 7600 GT video card, and an Acer 22" Widescreen LCD.  I tried using envy to install the Nvidia graphics drivers as I have done before on my other system.  It caused Xserver to crash with an "API mismatch" type error resulting in "No screens found" (I can post details if that would be helpful).  So I uninstalled the Nvidia driver, cleaned any possible installations of the Nvidia driver, reinstalled the Nvidia driver and it's the same deal.  I am using the vesa drivers right now but why isn't envy working?  

Thanks,

-sheep

---

### Post by dabl on 2007-07-17
Can't say why it doesn't always work right in GUI mode, but occasionally it works only in text mode.  If you want to try it, reboot your system to "recovery mode" to a text prompt, log in, and then enter ```
sudo envy -t
``` to start the text mode installer.  Sounds like you might want to first have it "Remove" the Nvidia driver, and then exit Envy, and then run it again and the second time have it "Install" the driver, and start the X server.  No guarantees, but it's been known to work this way.  :)

---

### Post by fatsheep on 2007-07-17
> **dabl said:**
> Can't say why it doesn't always work right in GUI mode, but occasionally it works only in text mode.  If you want to try it, reboot your system to "recovery mode" to a text prompt, log in, and then enter ```
sudo envy -t
``` to start the text mode installer.  Sounds like you might want to first have it "Remove" the Nvidia driver, and then exit Envy, and then run it again and the second time have it "Install" the driver, and start the X server.  No guarantees, but it's been known to work this way.  :)

I have been using the text installer.  I don't know about recovery mode though, I haven't tried that yet.  I'm about to though.  I'll post back with results.

---

### Post by fatsheep on 2007-07-17
Ok I tried going into recovery mode, removing the nvidia driver, cleaning any previous installation of the nvidia driver (had to run 'telinit 3' to do this), and installing the nvidia driver with **envy -t** but I get the same error.  Here's my /var/log/xorg.0.log file for details on my problem:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux alex-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 17 19:39:08 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Acer AL2223W"
(**) |   |-->Device "Nvidia Geforce 7600 GT"
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
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2946 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0391 card 3842,c615 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1458,e000 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xf90fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf7000000 - 0xf8ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GT] rev 161, Mem @ 0xf4000000/24, 0xe0000000/28, 0xf5000000/24, I/O @ 0xb000/7
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
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[11] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[12] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[13] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[33] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[11] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[12] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[13] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[33] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
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
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[18] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[19] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[24] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 17:16:40 PDT 2007
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 16:35:28 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[18] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[19] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[24] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[21] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[22] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[25] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[26] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[27] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[29] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[41] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[42] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[43] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.05
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[8] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[9] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[10] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[11] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[12] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[13] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[25] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[26] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[29] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[30] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[31] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[33] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[34] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[42] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[43] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[44] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[45] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[46] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[47] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[48] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[49] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2ad1c4c90d40]
2: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv001082X+0x36) [0x2ad1c714deb6]

Fatal server error:
Caught signal 11.  Server aborting

```

I have also tried method one from this how to: [http://doc.gwos.org/index.php/Latest_nvidia_feisty#REQUIREMENTS](http://doc.gwos.org/index.php/Latest_nvidia_feisty#REQUIREMENTS)

I get similar results:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux alex-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 17 20:07:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Acer AL2223W"
(**) |   |-->Device "Nvidia Geforce 7600 GT"
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
(++) using VT number 8

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2946 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0391 card 3842,c615 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1458,e000 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xf90fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf7000000 - 0xf8ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GT] rev 161, Mem @ 0xf4000000/24, 0xe0000000/28, 0xf5000000/24, I/O @ 0xb000/7
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
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[11] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[12] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[13] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[33] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[11] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[12] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[13] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[33] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
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
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[18] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[19] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[24] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:18:52 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[18] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[19] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[24] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[21] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[22] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[25] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[26] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[27] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[29] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[41] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[42] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[43] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by dabl on 2007-07-17
Hmmmmm.  I can see a couple of items that aren't quite right, like pixel depth = 32 (you only want 24), but these should not be install-killers.

And, have you tried the packaged driver, "nvidia-glx-new"?  It has driver ver. -9755, which will run your card just fine.  I would set up as a generic VESA display first, use Envy to remove the proprietary driver that is presently installed, then run Synaptic and mark the packaged driver for installation.

I must admit, if neither the packaged driver nor Envy will work, I'm kinda stuck.  I don't know if there's anything you can turn off in BIOS that might be interfering, like power-saving features or something like that?  :confused:

---

### Post by fatsheep on 2007-07-17
> **dabl said:**
> Hmmmmm.  I can see a couple of items that aren't quite right, like pixel depth = 32 (you only want 24), but these should not be install-killers.

And, have you tried the packaged driver, "nvidia-glx-new"?  It has driver ver. -9755, which will run your card just fine.  I would set up as a generic VESA display first, use Envy to remove the proprietary driver that is presently installed, then run Synaptic and mark the packaged driver for installation.

I must admit, if neither the packaged driver nor Envy will work, I'm kinda stuck.  I don't know if there's anything you can turn off in BIOS that might be interfering, like power-saving features or something like that?  :confused:

Yea I used nvidia-glx-new for the method  1 install.  How would I set up a generic VESA display?

---

### Post by fatsheep on 2007-07-18
I just tried the method on [www.ubuntuguide.com](www.ubuntuguide.com) with similar results.  Basically it just said to enable the nvidia driver under System > Administration > Restricted Drivers Manager and then run Add / Remove to check for dependences.  I ran **sudo apt-get update && sudo apt-get upgrade** just to make sure everything was up to date.  Restricted Drivers Manager installed the "nvidia-glx" package.  After that I rebooted to this:

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux alex-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 18 11:09:14 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Acer AL2223W"
(**) |   |-->Device "Nvidia Geforce 7600 GT"
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
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2946 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0391 card 3842,c615 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1458,e000 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xf90fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf7000000 - 0xf8ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GT] rev 161, Mem @ 0xf4000000/24, 0xe0000000/28, 0xf5000000/24, I/O @ 0xb000/7
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
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[11] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[12] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[13] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[33] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[11] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[12] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[13] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[17] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[33] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
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
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[18] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[19] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[24] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:37:27 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[18] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[19] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[23] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[24] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[21] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[22] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[25] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[26] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[27] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[29] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[41] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[42] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[43] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by dabl on 2007-07-18
Bummer!

That "failed to initialize the Nvidia kernel module" is a troubling one.

I assume ```
lspci
``` shows your Nvidia card on the PCI bus?  And```
 lsmod 
```shows the Nvidia module(s)? Is there any chance the card isn't seated completely on the mobo?  You did connect the extra 4-pin power connector to the card?

I must admit, I'm outta gas here -- this is sad.

To set it up as a generic VESA display, get a text prompt and enter ```
sudo dpkg-reconfigure xserver-xorg
``` On the first screen answer "NO" to autodetect, and on the second screen choose "VESA" as the display type.  You can accept defaults through the following screens to the monitor section.  In the monitor resolution, "x" only one that you can live with for awhile, like 1024 x 768, and then choose suitable refresh rates for your LCD or CRT, and when it completes it will dump you back to the text prompt.  At that point you can enter ```
startx
``` and you'll get a GUI, although it won't exploit the capabilities of your Nvidia card.  Then you can continue your research on the driver issue.  Worst case, maybe you can get the open source "nv" driver to work.   :(

---

### Post by fatsheep on 2007-07-18
Below is the output of both of those commands.  One thing that's worth mentioning is that Ubuntu did not seem to detect anything about my card.  On my other system it identified the graphics card as a "Nvidia 6600 GT" or something like that (which is correct), however on this system I had to enter the names of the monitor and graphics card when I reconfiguring X.  

```
**alex@alex-desktop:~$ lspci**
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


**alex@alex-desktop:~$ lsmod**
Module                  Size  Used by
isofs                  38628  1 
udf                    86664  0 
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62468  4 rfcomm,l2cap
ppdev                  11272  0 
ipv6                  307456  18 
acpi_cpufreq           10760  1 
cpufreq_conservative     9736  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       10640  2 
freq_table              6336  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       6176  0 
cpufreq_powersave       3072  0 
dev_acpi               17028  0 
sony_acpi               7064  0 
pcc_acpi               15616  0 
tc1100_wmi              9224  0 
video                  19080  0 
sbs                    17856  0 
asus_acpi              19756  0 
dock                   11992  0 
ac                      6920  0 
i2c_ec                  6912  1 sbs
backlight               8448  1 asus_acpi
battery                12040  0 
container               6144  0 
button                 10016  0 
lp                     15048  0 
fuse                   51888  0 
snd_hda_intel          24224  1 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
af_packet              27020  2 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             40104  1 
pcspkr                  4736  0 
i2c_core               26496  1 i2c_ec
parport                43404  3 ppdev,lp,parport_pc
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
psmouse                43536  0 
serio_raw               9092  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sd_mod                 25092  3 
sr_mod                 18980  1 
cdrom                  40744  1 sr_mod
generic                 6532  0 [permanent]
pata_jmicron            9088  0 
ata_piix               18308  3 
ahci                   25348  0 
ata_generic            10628  0 
ehci_hcd               37004  0 
uhci_hcd               28320  0 
floppy                 67944  0 
libata                137000  4 pata_jmicron,ata_piix,ahci,ata_generic
scsi_mod              166968  4 sg,sd_mod,sr_mod,libata
r8169                  35720  0 
usbcore               154416  3 ehci_hcd,uhci_hcd
thermal                16912  0 
processor              34952  2 acpi_cpufreq,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

On that first command it lists a whole bunch of intel device but in the middle of them you can see it looks like it detected my graphics card.  My motherboard has no onboard video if you are wondering about that:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128050](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128050)

EDIT:

Also, I forgot to mention, I did double check the mounting of the video card.  It is in the PC Express slot securely.  Also, there is no power connector on my video card.

---

### Post by dabl on 2007-07-18
Nice motherboard!  I googled "GIGABYTE GA-P35-DS3 + Linux" and didn't see reported problems.

I'm a bit surprised at all the "unkown device" items on your PCI bus -- what is that all about? Where's that Realtek onboard audio chip?  I don't think I have any unknown devices on mine. It almost looks like it's reporting every PCI bus line, whether anything is connected there or not.

In the notes about your motherboard, there was some mention of going into "F1 Basic BIOS", if I understood it correctly.  Is there anything about your PCI bus defaults in there?  Do you have the latest BIOS update installed?

I don't know what your capability to load another OS on that system might be -- it would interesting to see if any version of Windows would load up and run on it, including recognizing the Nvidia card.  I'm getting a little suspicious that it might not be a Linux or Ubuntu issue -- I dunno, guess I'm reaching for straws here .... :confused:

---

### Post by fatsheep on 2007-07-18
> **dabl said:**
> Nice motherboard!  I googled "GIGABYTE GA-P35-DS3 + Linux" and didn't see reported problems.

I'm a bit surprised at all the "unkown device" items on your PCI bus -- what is that all about? Where's that Realtek onboard audio chip?  I don't think I have any unknown devices on mine. It almost looks like it's reporting every PCI bus line, whether anything is connected there or not.

In the notes about your motherboard, there was some mention of going into "F1 Basic BIOS", if I understood it correctly.  Is there anything about your PCI bus defaults in there?  Do you have the latest BIOS update installed?

I don't know what your capability to load another OS on that system might be -- it would interesting to see if any version of Windows would load up and run on it, including recognizing the Nvidia card.  I'm getting a little suspicious that it might not be a Linux or Ubuntu issue -- I dunno, guess I'm reaching for straws here .... :confused:

Nope, I haven't updated the BIOS yet, I should probably try that next.  I could go try pressing F1 at bootup and see if it shows anything about the PCI bus defaults.  I'll edit this post after I do that.  What do you want me to look for specifically?  

BTW, I tried installing the driver off of Nvidia's website with similar results so I posted on their forums:

[http://www.nvnews.net/vbulletin/showthread.php?p=1316876#post1316876](http://www.nvnews.net/vbulletin/showthread.php?p=1316876#post1316876)

They have been pretty helpful in the past so I'm hopeful. ;)

---

### Post by fatsheep on 2007-07-18
The NVIDIA rep pointed me to a part in the error log that was infront of me the whole time.  Apparently my problem corresponds to the first header in Chapter 8 of the [README](http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.11/README/chapter-08.html).  The Nvidia rep thinks it's either a BIOS or kernel problem.  I am about to update the BIOS even though there were no changes listed in the changelog that should effect my problem (it's worth a try).  

So I'm thinking, since the BIOS update most likely will not effect anything, I think I'll end up applying those parameters to the kernel.  Do I have to compile my own kernel to apply these parameters (I'm assuming parameters are applied on compilation)?

---

### Post by Soybean on 2007-07-19
> **fatsheep said:**
> So I'm thinking, since the BIOS update most likely will not effect anything, I think I'll end up applying those parameters to the kernel.  Do I have to compile my own kernel to apply these parameters (I'm assuming parameters are applied on compilation)?

Actually, I think those ones are applied at boot time. And... I forget the exact procedure. :oops: When the grub menu is up, there's a button you can press to edit the boot options... you can add the parameters there. Or you can add them in your grub configuration, so they'll be used every time.

Sorry I can't remember the specifics, but a bit of searching for a grub guide or grub-related forum posts should get you the details that I lack. :) Good luck!

---

### Post by Nkari on 2007-07-20
I had a mismatch problem when I was trying to get my 7600s to work on a fresh install of 64bit Feisty. 

First I tried to get envy to work.Then updated everything through aptitude. Then used envy'
s remove option then told envy to install again. This somehow fixed the problem.

Later when I knew a little bit more I realised that the updating had updated the kernel too so there where version issues with multiple components, and apparently video kernels need to be recompiled to work with the main kernel.

---

### Post by tseliot on 2007-07-20
> **fatsheep said:**
> Do I have to compile my own kernel to apply these parameters (I'm assuming parameters are applied on compilation)?
There's no need to recompile your kernel.

You can follow the instructions on this page:
[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

but of course you will have to use the parameters suggested by Nvidia.

---

### Post by tseliot on 2007-07-20
> **Nkari said:**
> Later when I knew a little bit more I realised that the updating had updated the kernel too so there where version issues with multiple components, and apparently video kernels need to be recompiled to work with the main kernel.
Each kernel needs its kernel module of the Nvidia driver.

---

### Post by fatsheep on 2007-07-21
> **tseliot said:**
> There's no need to recompile your kernel.

You can follow the instructions on this page:
[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

but of course you will have to use the parameters suggested by Nvidia.

Thanks for that, I'm trying it now.  I thought the lines preceded with "#" were always commented in that file but I guess not?

---

### Post by fatsheep on 2007-07-21
I have substituted my trusty old 6600 GT card in place of the 7600 GT and everything is A OK now.  Apparently the 7600 GT was in good enough condition to run the VESA drivers correctly and pass POST but could not handle the accelerated NVIDIA drivers.  There was no software problem, it was the graphics card.  I am going to RMA it to newegg ASAP.  I feel relieved that the problem is solved.  For a few days I was thinking that I might never get the drivers installed on this machine! :p  Thanks for the help everyone.

 - sheep

---

### Post by benx009 on 2007-07-21
> **fatsheep said:**
> I have a fresh install of Ubuntu Feisty 7.04 (64-bit) on a new computer with a Intel Core Duo E6420 processor, Nvidia 7600 GT video card, and an Acer 22" Widescreen LCD.  I tried using envy to install the Nvidia graphics drivers as I have done before on my other system.  It caused Xserver to crash with an "API mismatch" type error resulting in "No screens found" (I can post details if that would be helpful).  So I uninstalled the Nvidia driver, cleaned any possible installations of the Nvidia driver, reinstalled the Nvidia driver and it's the same deal.  I am using the vesa drivers right now but why isn't envy working?  

Thanks,

-sheep

i had a similar problem w/ an nvidia legacy card; gnome wouldn't load up so i had to use text mode.  envy isn't perfect

---

