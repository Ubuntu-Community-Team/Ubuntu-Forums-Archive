---
title: "Play videofile in the xubuntu desktop"
date: 2007-10-26
forum: Mythbuntu
---

### Post by axelsvag on 2007-10-26
I have problem to view videofile in the xubuntu desktop after install in MCC. If I try to view a videofile using the xubuntu desktop with xine, vlc, mplayer or totem it just gives a lot of shades of green instead of a watchable picture. If I watch the same files in  for example var/lib/video from mythTV front everything is fine. Medibuntu was installed and when I used the totem the gstreamer plugins installed but nothing worked. Does anyone have any ideas?

---

### Post by superm1 on 2007-10-26
Try installing a proprietary video driver if you don't have one on.

---

### Post by axelsvag on 2007-10-26
The prop driver seems to be fully installed and enabled which in my world is confirmed by the fact that the files work perfectly played through the mythtv frontend.

---

### Post by axelsvag on 2007-10-27
Now I got one step further to the solution. I found out that if I use any session besides the mythbutnu session all is well for xine, vlc and friends but then the frontend can´t show any usable pictures just many "shades of green" And when I go back to a mythbuntu session the problem is back for xine, vlc etc but the frontend works again. I believe I have read about a few here on the forum that had trouble getting a usable picture out of frontend so it maybe has something to do with a driver error or?

---

### Post by superm1 on 2007-10-28
> **axelsvag said:**
> Now I got one step further to the solution. I found out that if I use any session besides the mythbutnu session all is well for xine, vlc and friends but then the frontend can´t show any usable pictures just many "shades of green" And when I go back to a mythbuntu session the problem is back for xine, vlc etc but the frontend works again. I believe I have read about a few here on the forum that had trouble getting a usable picture out of frontend so it maybe has something to do with a driver error or?
This is very very odd.  Can you post your /var/log/Xorg.0.log?  We can check a few things here about what's getting setup.

---

### Post by axelsvag on 2007-10-28
Here it comes. Maybe the error has something to do with the "pink screen of death" that have been discussed and the nvidia driver seems to be bad guy for the moment.
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux aco-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 27 17:40:46 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "Xinerama" "0"
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
(II) Loader magic: 0x7cd8a0
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
(II) PCI: 00:00:0: chip 1002,7910 card 1043,826d rev 00 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,7913 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1002,7917 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1043,81ef rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1043,81ef rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1043,81ef rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1043,81ef rev 13 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1043,81ef rev 00 class 01,01,82 hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1043,8249 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1043,81ef rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0392 card 1043,822a rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 10ec,8168 card 1043,81aa rev 01 class 02,00,00 hdr 00
(II) PCI: 03:06:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 03:07:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: 04:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 04:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:7:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000cfff (0x2000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdffffff (0x200000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (3:6:0), (3,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24, I/O @ 0xdf00/7, BIOS @ 0xfcfe0000/17
(--) PCI: (4:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf4000000/26
(--) PCI: (4:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf0000000/26
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
	[0] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[1] -1	0	0xfdcff000 - 0xfdcfffff (0x1000) MX[B]
	[2] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[3] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[4] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[9] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[10] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[18] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[19] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[25] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[27] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[30] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[1] -1	0	0xfdcff000 - 0xfdcfffff (0x1000) MX[B]
	[2] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[3] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[4] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[9] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[10] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[11] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[18] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[19] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[25] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[27] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[30] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
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
	[4] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[5] -1	0	0xfdcff000 - 0xfdcfffff (0x1000) MX[B]
	[6] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[7] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[8] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[15] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[16] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[24] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[25] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[31] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[32] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[33] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[34] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[35] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[36] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:51:24 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:10:47 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[5] -1	0	0xfdcff000 - 0xfdcfffff (0x1000) MX[B]
	[6] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[7] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[8] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[15] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[16] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[24] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[25] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[31] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[32] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[33] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[34] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[35] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[36] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[5] -1	0	0xfdcff000 - 0xfdcfffff (0x1000) MX[B]
	[6] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[7] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[8] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[15] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[16] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[28] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[34] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[36] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[38] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[39] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1024x768 +0+0; nvidia-auto-select +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.54.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: TV-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0):     "nvidia-auto-select+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[8] -1	0	0xfdcff000 - 0xfdcfffff (0x1000) MX[B]
	[9] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[10] -1	0	0xfed00000 - 0xfed003ff (0x400) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[14] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[15] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[16] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[17] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[18] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[19] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[20] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[21] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[22] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[23] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[27] 0	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[30] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[31] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[32] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[38] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[40] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[41] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[42] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[43] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1024x768+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
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
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
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
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

