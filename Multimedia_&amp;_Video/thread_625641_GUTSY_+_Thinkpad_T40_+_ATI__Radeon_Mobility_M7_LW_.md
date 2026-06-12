---
title: "GUTSY + Thinkpad T40 + ATI  Radeon Mobility M7 LW (Mobility 7500) 3d ACCEL PLS HELP!"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by asbesto on 2007-11-28
Hi all, 

I was happy with my Ubuntu Feisty and my Thinkpad T40 with Radeon 7500. All effects working, acceleration, and so on. It was very nice to use! 

But now, with gutsy I can't solve this. I can't find a way to enable 3d Effects! 

My xorg.conf now is:

> 
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


glxinfo says:

> 
asbesto@gemini:~$ glxinfo
name of display: :6.0
display: :6  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:

ecc. ecc.



and Xorg.0.log is here:

> 


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux gemini 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 28 13:05:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Synaptics Touchpad"
(==) |-->Input Device "<default pointer>"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the default mouse configuration.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3340 card 1014,0529 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1014,052d rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1014,052e rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1014,052d rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1014,052d rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1014,0537 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1014,0524 rev 01 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4c57 card 1014,0530 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 104c,ac55 card 4000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:00:1: chip 104c,ac55 card 4800,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:08:0: chip 8086,103d card 1014,0522 rev 81 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
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
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
	[4] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[5] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[6] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[7] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
	[8] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[9] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[10] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[11] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
	[12] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[13] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[14] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[15] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
	[16] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[17] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[18] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[19] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xcfffffff (0xfe00000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:0:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (2:0:1), (2,7,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[1] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xe0000000/27, 0xc0100000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc0200000 - 0xc0200fff (0x1000) MX[B]
	[1] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[2] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[3] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[4] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[9] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[10] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[11] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[12] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[13] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[14] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0200000 - 0xc0200fff (0x1000) MX[B]
	[1] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[2] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[3] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[4] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[9] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[10] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[11] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[12] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[13] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[14] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0200000 - 0xc0200fff (0x1000) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[16] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[17] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[18] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon Mobility M7 LW (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0200000 - 0xc0200fff (0x1000) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[16] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[17] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[18] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0200000 - 0xc0200fff (0x1000) MX[B]
	[5] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[6] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[7] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[8] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[18] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[19] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[23] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xc0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
(--) RADEON(0): Linear framebuffer at 0xe0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12000 max=35000; xclk=18300
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-2, DACType-1, TMDSType-0, ConnectorType-4
(II) RADEON(0): Port4: DDCType-0, DACType-2, TMDSType-2, ConnectorType-1
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI_DDC" initialized.
(II) RADEON(0): DFP table revision: 2
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: 1024x768                
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 16, HSyncWidth: 136
VBlank: 38, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): Using LVDS Native Mode
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-D
 DAC Type  -- None
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- Proprietary/LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): Port3:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
finished output detect: 1
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
finished output detect: 2
finished output detect: 3
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1152x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0200000 - 0xc0200fff (0x1000) MX[B]
	[7] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[8] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[21] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[22] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[23] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[24] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xe0000000,0x2000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1024,1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x800000
(II) RADEON(0): Will use depth buffer at offset 0xc00000
(II) RADEON(0): Will use 16384 kb for textures at offset 0x1000000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0c29000
(II) RADEON(0): [drm] mapped SAREA 0xe0c29000 to 0xb7b20000
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x3340; Card 0x1002/0x4c57]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xd0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7a1f000
(II) RADEON(0): [agp] ring read ptr handle = 0xd0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7a1e000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb574a000
(II) RADEON(0): [agp] GART texture map handle = 0xd0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb526a000
(II) RADEON(0): [drm] register handle = 0xc0100000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe3ffe000 is: 0xe3ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd07fd000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd07fd000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7161
(II) RADEON(0): Detected Radeon Mobility M7, disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
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
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: Core Pointer
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 2
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
SetClientVersion: 0 9
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video



lsmod is:

> 
Module                  Size  Used by
snd_rtctimer            4384  1 
binfmt_misc            12936  1 
ppdev                  10244  0 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nvram                   9992  1 
uinput                 10368  1 
thinkpad_acpi          44588  0 
radeon                125472  3 
drm                    83348  4 radeon
speedstep_centrino      8256  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
video                  18060  0 
bay                     6912  0 
battery                11012  0 
sbs                    19592  0 
dock                   10656  1 bay
ac                      6148  0 
container               5504  0 
button                  8976  0 
prism2_usb             74756  0 
p80211                 33036  1 prism2_usb
ipv6                  273892  12 
lp                     12580  0 
joydev                 11328  0 
irtty_sir               9856  0 
sir_dev                17412  1 irtty_sir
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
irda                  202300  2 irtty_sir,sir_dev
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               3072  1 irda
serio_raw               8068  0 
snd                    54660  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcmcia                 41388  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
psmouse                39952  0 
pcspkr                  4224  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
af_packet              24840  2 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
floppy                 60004  0 
e100                   37644  0 
mii                     6528  1 e100
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 prism2_usb,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


Sorry for the long post but really I'm going nuts! 

Please someone help!

---

### Post by asbesto on 2007-11-28
I SOLVED my problem ... but I DON'T KNOW HOW!!! 

:confused:

I followed this thread:

[http://ubuntuforums.org/showthread.php?t=624016](http://ubuntuforums.org/showthread.php?t=624016)

and in particular the instructions on this blog:

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#)

After this, my Xorg was not working at all!

Confused, I simply deinstalled everything I installed reading that blog: So I disinstalled all ati drivers, all xserver-xgl stuff, everything!

also I removed fglrx and put "radeon" in the driver section of xorg.conf

I rebooted, and my X started, without any accel, but, HEY, I found this:

> 
name of display: :0.0
disabling 3D acceleration
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:


So, INCREDIBLY, direct rendering seem working!

But "glxgears" gave me about 25 FPS :(

So, I simply tried launching "compiz" as user from terminal, and I REALLY DON'T KNOW WHAT'S HAPPENED, but NOW I have everything working: compiz, all the effects, and it's everything fast and smooth! 

:)


Really I don't know - If someone need it, I can post my actual xorg.conf setup.

BOH!

:lolflag:

---

### Post by Vadi on 2007-12-05
Delete xorg.conf.

That solved problems with me, heh (t40 too here).

---

