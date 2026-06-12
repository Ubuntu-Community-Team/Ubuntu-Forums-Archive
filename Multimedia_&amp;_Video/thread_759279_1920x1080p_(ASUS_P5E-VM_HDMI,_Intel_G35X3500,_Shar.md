---
title: "1920x1080p? (ASUS P5E-VM HDMI, Intel G35/X3500, Sharp Aquos)"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by vpuzzella on 2008-04-18
Hi Folks,

I just finished building my HTPC and I'm trying to get my Sharp Aquos to display 1080p. I've search high and low and tried a bunch of xorg configurations, but nothing seems to work. I'm at my wits end and hoping somebody can help. With my current config I only get 800X600. 

I am connected to the Sharp Aquos via **straight HDMI cable** (no DVI dongle).

**_Specs:_**

**Motherboard**: [Asus P5E-VM HDMI]("http://www.asus.com/products.aspx?modelmenu=1&model=1912&l1=3&l2=11&l3=584&l4=0")
**Onboard Graphics:** Intel Graphics Media Accelerator X3500 (G35) Itegrated Dual VGA (VGA & HDMI ports)  
**Display:** Sharp Aquos LC42D72U (42")
**OS:** Ubuntu Gutsy 7.10 (Fully updated)
**Driver Package:**
```

$ apt-show-versions | grep intel
xserver-xorg-video-intel/gutsy uptodate 2:2.1.1-0ubuntu9.1

```

**XOrg Config - Display stuff (Various options I've tried are commented out):**

```

Section "Device"
	Identifier	"Intel Corporation 965 G1 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:00:02:0"
	Option 		"Monitor-TMDS-1" 		"HDMI"
	Option 		"Monitor-VGA"			"VGA"
	#Option		"IgnoreEDID" 			"True"
	#Option 	"ExactModeTimingsDVI" 		"True"
	#Option 	"ModeValidation"		"NoDFPNativeResolutionCheck"
	#Option 	"FlatPanelProperties" 		"Scaling=Native"
	#Option 	"AddARGBGLXVisuals" 		"True"
	#Option 	"DisableGLXRootClipping" 	"True"	
	#Option         "NoAccel"
		
EndSection

Section "Monitor"
	Identifier	"HDMI"
	Option		"DPMS"
	Modeline "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
	#Modeline "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	#Option 		"PreferredMode" 	"1920x1080"
EndSection

Section "Monitor"
    Identifier "VGA"
    # Ignore this monitor because it does not exist.
    Option "Ignore" "True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 965 G1 Integrated Graphics Controller"
	Monitor		"HDMI"
	DefaultDepth	24
	SubSection "Display"	
		Depth 24
		Modes "1920x1080"
		Viewport 0 0		
		#Virtual 2048 2048	
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

**Log generated from startx:** (Note the "(II) intel(0): Output TMDS-1 disconnected" ... WTF???)

```

xauth:  creating new authority file /home/vpuzzella/.serverauth.17680
xauth:  error in locking authority file /home/vpuzzella/.Xauthority
xauth:  error in locking authority file /home/vpuzzella/.Xauthority
xauth:  error in locking authority file /home/vpuzzella/.Xauthority
xauth:  error in locking authority file /home/vpuzzella/.Xauthority

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux HTPC 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 18 21:25:16 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HDMI"
(**) |   |-->Device "Intel Corporation 965 G1 Integrated Graphics Controller"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cdb20
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
(--) using VT number 7


(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2980 card 1043,8295 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2982 card 1043,8276 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2983 card 1043,8276 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2937 card 1043,8277 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1043,8277 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1043,8277 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,294a card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1043,8277 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1043,8277 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1043,8277 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2922 card 1043,8277 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1043,8277 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1969,1048 card 1043,8226 rev b0 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 197b,2368 card 1043,827e rev 00 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 14e4,4329 card 1737,0060 rev 01 class 02,80,00 hdr 00
(II) PCI: 04:03:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:5), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 965 G1 Integrated Graphics Controller rev 3, Mem @ 0xfe800000/20, 0xd0000000/28, I/O @ 0xcc00/3
(--) PCI: (0:2:1) Intel Corporation unknown chipset (0x2983) rev 3, Mem @ 0xfe900000/20
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
	[0] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[B]
	[1] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[2] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B]
	[3] -1	0	0xfe7fb400 - 0xfe7fb4ff (0x100) MX[B]
	[4] -1	0	0xfe7fa800 - 0xfe7fafff (0x800) MX[B]
	[5] -1	0	0xfe7fb800 - 0xfe7fbbff (0x400) MX[B]
	[6] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[7] -1	0	0xfe7fbc00 - 0xfe7fbfff (0x400) MX[B]
	[8] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[11] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[13] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[15] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[17] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[18] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[20] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[24] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[26] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[28] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[B]
	[1] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[2] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B]
	[3] -1	0	0xfe7fb400 - 0xfe7fb4ff (0x100) MX[B]
	[4] -1	0	0xfe7fa800 - 0xfe7fafff (0x800) MX[B]
	[5] -1	0	0xfe7fb800 - 0xfe7fbbff (0x400) MX[B]
	[6] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[7] -1	0	0xfe7fbc00 - 0xfe7fbfff (0x400) MX[B]
	[8] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[11] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[13] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[15] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[17] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[18] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[20] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[24] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[26] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[28] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
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
	[4] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[6] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B]
	[7] -1	0	0xfe7fb400 - 0xfe7fb4ff (0x100) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fafff (0x800) MX[B]
	[9] -1	0	0xfe7fb800 - 0xfe7fbbff (0x400) MX[B]
	[10] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[11] -1	0	0xfe7fbc00 - 0xfe7fbfff (0x400) MX[B]
	[12] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[19] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[21] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[23] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[24] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[26] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[29] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[30] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[32] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[34] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.1
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[6] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B]
	[7] -1	0	0xfe7fb400 - 0xfe7fb4ff (0x100) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fafff (0x800) MX[B]
	[9] -1	0	0xfe7fb800 - 0xfe7fbbff (0x400) MX[B]
	[10] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[11] -1	0	0xfe7fbc00 - 0xfe7fbfff (0x400) MX[B]
	[12] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[19] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[21] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[23] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[24] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[26] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[29] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[30] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[32] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[34] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[6] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B]
	[7] -1	0	0xfe7fb400 - 0xfe7fb4ff (0x100) MX[B]
	[8] -1	0	0xfe7fa800 - 0xfe7fafff (0x800) MX[B]
	[9] -1	0	0xfe7fb800 - 0xfe7fbbff (0x400) MX[B]
	[10] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[11] -1	0	0xfe7fbc00 - 0xfe7fbfff (0x400) MX[B]
	[12] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[22] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[24] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[26] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[27] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[29] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[31] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[33] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[35] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[37] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[38] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "NoAccel"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965G
(--) intel(0): Chipset: "965G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFE800000
(II) intel(0): 2 display pipes available.
(**) intel(0): DRI is disabled because it needs HW cursor and 2D acceleration.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section VGA
(**) intel(0): Option "Ignore" "True"
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 using monitor section HDMI
(II) intel(0): SDVO device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): Output TMDS-1 disconnected
(II) intel(0): EDID for output TMDS-1
(II) intel(0): Output TMDS-1 disconnected
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 0 requests (0 known processed) with 0 events remaining.

xauth:  error in locking authority file /home/vpuzzella/.Xauthority

```

**ddcprobe Output**

```

$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)Q965/Q963/G965 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Q965/Q963/G965 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 0fe3
eisa: SHP0fe3
serial: 01010101
manufacture: 0 2006
input: analog signal.
screensize: 82 46
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
dtiming: 1920x1080@67
dtiming: 1360x768@70
monitorname: SHARP HDMI
monitorrange: 15-68, 55-76

```

**Output of lspci:**

```

$ lspci
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

**xresprobe Output**

```

$ sudo xresprobe intel
id: SHARP HDMI
res: 1920x1080 1360x768 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 15-68 55-76
disptype:

```

---

### Post by dallas7 on 2008-04-19
I just yesterday ordered a system built to my specs based on the same motherboard.  While the system won't be in for maybe 10-15 days, I picked up my 22" monitor and hooked it up to this P3/1GHz clunker I've been using for various distros of Linux for about 5 years.

Strangely, I found your post here by searching on "i810."  I can't get more than 1280x1024 even though up to 1600x1200 is supported according to Intel.  I'm running 7.04, Feisty.

The only thing I can pull from your data is that your config thinks it's running Intel 965, X3000, graphics while the G35 is X3500.  I can't imagine the 965 driver talking to the G35 correctly.

Then again, all the config data is CORRECT in my setup and I can't get it to work the way I want it to.  I think the over all conclusion we can come to is 7.x xserver-xorg sucks.  I don't believe I'm alone on that.

In any event, from the research I've done, I am counting on next week's release of 8.04 to be able to take advantage of all our P5E-VMs features, video included.

Good luck - to both of us!

---

### Post by sippnonacorona on 2008-05-18
I've been spending the past few days installing 8.04 HARDY on this mainboard and there is no support for the G35/X3500 chipset. I had to force VESA by using VGA= in the grub menu.lst file to get anything higher than 800x600. The VESA standards have no setting that maps to 1080p (yet?). I see 1920x1080 becoming a new standard with the expansion of HiDef TVs in the market but I figured I need to wait for a future upgrade for Ubuntu to catchup with the trend.

I have mounted this mainboard in a mini-chasis and for the first time, I will have a server in the mix of components in my home theater system. It will hook up directly to the HDMI input on my AV amp or TV. I hope for it to become my home media server, household shared disk storage, and household mail server.

---

### Post by trouble1313 on 2008-05-20
There certainly is (some) support for the G35/X3500 in Hardy. The 'intel' driver supports it. Unfortunately, the driver is somewhat wacky for HDMI. While the Hardy stock driver does work to some extent, I have found compiling xserver-intel-xorg-2.2.3 to do better but still not great. There is a long discussion in the mythbuntu forum. Do a search for P5E-VM, which is a G35 based board.

-Trouble

---

### Post by neoliv on 2008-06-11
Hum... I'm having problems with a very similar setup (see vpuzzella specs)
p5evm-hdmi (bios 506) + hdmi to a sharp aquos lc42xd1e. (full hd TV)
The thing is I've had all that working with the Hardy alpha, then the IGP had a fault and I've had to return the motherboard.
The "new" board is here since this morning and now the Hardy (updated to this day) is not able to run my old tested and approved xorg.conf anymore.
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
I've read a lot of thing since and found nothing that seems to help.
Does anyone of you run this board in HDMI 1080 mode with the 8.04 and intel driver?
The edid data had the same "2nd bloc" problem before but it didn't seem to break things with the old drivers.

Here are some more data:

```

lspci
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
03:00.0 Ethernet controller: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

```

get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0x11110 "Intel(r)Q965/Q963/G965 Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

EDID claims 1 more blocks left


*********** Something special has happened!
Please contact the author, John Fremlin
E-mail: one of vii@altern.org,vii@mailcc.com,vii@mailandnews.com
Please include full output from this program (especially that to stderr)



Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

EDID claims 1 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fc
        Identifier "SHARP HDMI"
        VendorName "SHP"
        ModelName "SHARP HDMI"
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
        HorizSync 15-75
        VertRefresh 49-61
        # Max dot clock (video bandwidth) 170 MHz
        # DPMS capabilities: Active off:yes  Suspend:no  Standby:no

        Mode    "1920x1080"     # vfreq 50.000Hz, hfreq 56.250kHz
                DotClock        148.500000
                HTimings        1920 1968 2012 2640
                VTimings        1080 1084 1089 1125
                Flags   "+HSync" "+VSync"
        EndMode
        Mode    "1920x1080"     # vfreq 60.000Hz, hfreq 67.500kHz
                DotClock        148.500000
                HTimings        1920 2008 2052 2200
                VTimings        1080 1084 1089 1125
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
EndSection


```


So? Any of you have an idea? Intel is working on its drivers... OK but it seems really flacky right now. Any chance with more recent (non yet hardy) versions?

---

### Post by neoliv on 2008-06-12
Just tried the suggested update to the latest intel video driver (the 2.3 from the git tree)
No luck either but maybe it is not a driver issue anyway.
Take a look at the log from the X server.
The line 
```

(II) intel(0): Output VGA using monitor section Sharp HDMI
...
(II) intel(0): Output TMDS-1 has no monitor section

```

Obviously it won't work because the only monitor I have plugged on the G35 is the Sharp... but in HDMI not VGA!
How can I ask to use the HDMI and not the VGA output?
No luck finding the driver option documentation and the sources are not that helpful.

I'm not too sure about the following lines (coming from the X -verbose 2 (see full log below)

```

(--) PCI:*(0:2:0) Intel Corporation 965 G1 Integrated Graphics Controller rev 3, Mem @ 0xfe700000/20, 0xd0000000/28, I/O @ 0xbc00/3
(--) PCI: (0:2:1) Intel Corporation unknown chipset (0x2983) rev 3, Mem @ 0xfe800000/20
...
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset G35 found

```



```

xorg.conf

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"Intel G35"
	Boardname	"intel"
	Driver		"intel"
#        Option          "AccelMethod" "XAA"
EndSection

Section "Monitor"
	Identifier	"Default Monitor"
	Vendorname	"Unknown"
	Modelname	"Unknown"
        Option          "DPMS"
EndSection

Section "Monitor"
	Identifier	"Sharp HDMI"
	Vendorname	"Sharp"
	Modelname	"aquos LC42XD1E"
        Option          "DPMS"
#       Modeline "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  
-HSync +Vsync
EndSection

Section "Screen"
	Identifier	"HDTV Screen"
	Device		"Intel G35"
	Monitor		"Sharp HDMI"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1920x1080"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0        "HDTV Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection


```

```

X -verbose 2

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.1)
Current Operating System: Linux miniwi 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686
Build Date: 21 May 2008  12:19:32PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 12 10:02:46 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "HDTV Screen" (0)
(**) |   |-->Monitor "Sharp HDMI"
(**) |   |-->Device "Intel G35"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2980 card 1043,8295 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2982 card 1043,8276 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2983 card 1043,8276 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2937 card 1043,8277 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1043,8277 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1043,829f rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2942 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,294a card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1043,8277 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1043,8277 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1043,8277 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1043,8277 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1043,8277 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1043,8277 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 1969,1048 card 1043,8226 rev b0 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 197b,2368 card 1043,827e rev 00 class 01,01,85 hdr 00
(II) PCI: 03:00:0: chip 8086,10b9 card 8086,1083 rev 06 class 02,00,00 hdr 00
(II) PCI: 05:03:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(--) PCI:*(0:2:0) Intel Corporation 965 G1 Integrated Graphics Controller rev 3, Mem @ 0xfe700000/20, 0xd0000000/28, I/O @ 0xbc00/3
(--) PCI: (0:2:1) Intel Corporation unknown chipset (0x2983) rev 3, Mem @ 0xfe800000/20
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset G35 found
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G35
(--) intel(0): Chipset: "G35"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFE700000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Sharp HDMI
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVOB: device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz
(II) intel(0): SDVOB: 1 input channel
(II) intel(0): SDVOB: TMDS0 output reported
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 disconnected
(EE) intel(0): No valid modes.
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

---

### Post by neoliv on 2008-06-13
Very strange... I did a lot of test/tweaks and plain dumb blind tries... and finaly reverted to a simple xorg.conf.
and it worked (see below)
The only thing I may have done to make it work is an electric reboot and a bios enter/save.
Have no clue about the cause of the problem but I can confirm the intel (git) driver is working perfectly now with my hardy.

(full HD playback thru HDMI on the aquos 42xd1e with <50% CPU usage on a e8200)

for references the list of options for the driver are here: [http://intellinuxgraphics.org/man.html](http://intellinuxgraphics.org/man.html)


```


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"Intel G35"
	Boardname	"p5evm-hdmi"
	Driver		"intel"
#        Option          "monitor-TMDS-1" "Sharp HDMI"
#        Option          "monitor-VGA" "Generic VGA"
EndSection


Section "Monitor"
	Identifier	"Generic VGA"
        Option          "DPMS"
EndSection

Section "Monitor"
	Identifier	"Sharp HDMI"
	Vendorname	"Sharp"
	Modelname	"Aquos LC42XD1E"
        DisplaySize     1161 653
        Option          "DPMS"
#        Modeline "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"HDMI Screen"
	Device		"Intel G35"
	Monitor		"Sharp HDMI"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1920x1080" "1280x720"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"VGA+HDMI Layout"
        screen 1        "HDMI Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection


```

---

### Post by bric on 2008-06-16
I'd had better luck with my setup (Toshiba 42lx177) running at 1920x1200.  It autodetected after first install.  However, after a few weeks I had a crash and then, though it rebooted ok, I couldn't get it into high res mode.  I spent a long (LOOOONNNG) time fiddling with modelines, reading forums and finally my solution turned out to be unplugging/replugging the hdmi cable.  Apparently some sort of auto jack-detection mechanism has frozen up or something and buggered things for me.  Once I unplugged then things auto-detected again nicely.
hth.

---

### Post by jhiza on 2008-06-17
I had a hell of a time with my tv as well.  I think I have a working version, however.  

Let me know if this works or not (pay attention to my ATI card/etc, dual screen setup, etc).  As you can see, I had to experiment a lot too.  You'll notice all of my commented out attempts.

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "Device"
        Identifier      "Card0"
        #Driver         "ati"
        Driver          "fglrx"
        Vendorname      "ATI Technologies Inc"
        Boardname       "rv350 ap [radeon 9600]"
        Busid           "PCI:3:0:0"
        #Screen 0
EndSection

Section "Device"
        Identifier      "Card1"
        #Driver         "ati"
        Driver          "fglrx"
        Vendorname      "ATI Technologies Inc"
        Boardname       "rv350 ap [radeon 9600]"
        Busid           "PCI:3:0:1"
        #Screen 1
EndSection

Section "Monitor"
        Identifier      "Acer"
        Option          "DPMS"
        Horizsync       30-81
        Vertrefresh     40-76
EndSection

Section "Monitor"
        Identifier      "Aquos"
        Option          "DPMS"
        Horizsync       31.5-75.0
        Vertrefresh     56.0-75.0
        # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
        Modeline "1080p"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
        #hiza -- the following is NOT the original, but didn't cause problems either....
        #ModeLine "1080p"   148.50   1920 2012 2068 2200   1080 1082 1088 1125

        #These don't seem to do much??
        #DisplaySize 1920    1080
        #DisplaySize 510 287
        ##DisplaySize 487 274

        #ModeLine "1920x1080_60.00"   148.50   1920 2012 2068 2200   1080 1082 1088 1125
        #ModeLine "1080i" 74.52 1920 1952 2016 2208 1080 1084 1096 1126 interlace #ModeLine "720p" 73.825 1280 1320 1368 1640 720 722 724 751
        Option "ReducedBlanking" "TRUE"
        Option "ExactModeTimingsDVI" "TRUE"
        Option "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Acer"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                #also drives 1080p, careful when changing
                Virtual 1920    1080
                #Virtual 1680    945
                #Virtual 1920    1200

                Modes           "1680x1050@60"  "1680x1050@75"
                #the following appears to do nothing
                #Modes           "1680x945@60"  "1680x945@75"
                #Modes           "1600x1024@60"  "1680x1050@60"  "1440x900@60"   "1680x1050@75"  "1440x900@75"   "1920x1200@60"  "1280x800@60"   "1280x768@75"   "1280x800@75"   "1280x768@60"   "800x600@75"    "800x600@72"
        EndSubSection
EndSection
Section "Screen"
        Identifier      "Screen1"
        Device          "Card1"
        Monitor         "Aquos"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1080p"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen "Screen0"
        screen "Screen1"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "Module"
        #Load           "glx"
        # hiza -- the following used to be commented out
        #Load           "ati"
        Load            "dri"
EndSection
Section "Extensions"
        #google earth fix
        Option          "Composite"     "false"
        Option          "Composite"     "0"
EndSection


```

---

