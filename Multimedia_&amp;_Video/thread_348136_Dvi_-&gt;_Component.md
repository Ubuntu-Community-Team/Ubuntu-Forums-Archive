---
title: "Dvi -&gt; Component"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by CanadianMan on 2007-01-28
I have onboard vga/dvi and my graphics card is a Geforce 6150.  I bought cables from dvi to component video to hook into my computer.  However I can not get any sort of picture to display on my tv.  If i turn off my computer and back on i'll get a scrambed picture of what looks to be my desktop but only for a short time then I get that tv blue screen.  I've installed the nvidia drivers and changed the "nv" to "nvidia".  I only want to use DVI -> component I have no desire to have clone or expanded desktops.  I've tried putting several options in my xorg.conf.

Option          "TVStandard" "NTSC-M", "HD480i", "HD1080i", "HD576i"
Option          "TVOutFormat" "COMPONENT", "Component"

I didn't actually include the commas in I just tried each option one at a time and rebooted.  I hope someone has gotten this to work successfully.  If so do tell :)

Thanks.

---

### Post by CanadianMan on 2007-02-04
So far within a week I've not been able to get my tv-out working with dvi -> component.  I have posted my current Xorg.conf and Xorg.0.log so possibly someone will be able see what I'm doing wrong.  Thank you.

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	#VideoRam	128
	#Option		"UseFBDev"		"true"
	Option		"TVOutFormat" "Component"
	Option		"TVStandard" "HD480i"
	Option		"ConnectedMonitor" "TV"
	Option	 	"IgnoreEDID" "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	#Option		"DPMS"
	#HorizSync	30-100
	HorizSync      30-50
	#VertRefresh	50-160
	VertRefresh    60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	#Option          "TVStandard" "NTSC-M"
	#Option         	"TVOutFormat" "COMPONENT"
        #Option 		"NoLogo"	
	SubSection "Display"
		Depth		1
		Modes		"800x600_60"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600_60"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600_60"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600_60"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600_60"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600_60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by CanadianMan on 2007-02-04
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux mythtv 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  4 20:23:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f0 card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 147b,1c26 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:05:0: chip 10de,0240 card 10de,0222 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 147b,1c26 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 147b,1c26 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 147b,1c26 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 147b,1c26 rev a3 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 147b,1c26 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 147b,1c26 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 147b,1c26 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 147b,1c26 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 147b,1c26 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 147b,1c26 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 147b,1c26 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:07:0: chip 104c,8023 card 147b,1c26 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:0a:0: chip 4444,0016 card 0070,8801 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:16:0), (0,3,3), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfb000000/24, 0xd0000000/28, 0xfc000000/24
(--) PCI: (3:10:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xec000000/26
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
	[0] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[1] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[14] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[15] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[16] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[17] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[24] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[1] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[14] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[15] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[16] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[17] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[24] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
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
	[4] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[5] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[30] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 10:21:43 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[5] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[30] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[5] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[33] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[34] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "IgnoreEDID" "True"
(**) NVIDIA(0): Option "ConnectedMonitor" "TV"
(**) NVIDIA(0): Option "TVStandard" "HD480i"
(**) NVIDIA(0): Option "TVOutFormat" "Component"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Forcing COMPONENT output
(**) NVIDIA(0): TV Standard string: "HD480i"
(**) NVIDIA(0): ConnectedMonitor string: "TV"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): The IgnoreEDID and NoDDC options have been deprecated.  The
(WW) NVIDIA(0):     NVIDIA X driver makes use of a display device's EDID
(WW) NVIDIA(0):     during construction of its modePool.  It is recommended
(WW) NVIDIA(0):     that you allow the X driver to make use of any available
(WW) NVIDIA(0):     EDID.  If, however, you know what you are doing and have
(WW) NVIDIA(0):     good reason to do so, you can disable the X driver's use
(WW) NVIDIA(0):     of EDIDs by setting the "UseEDID" X configuration option
(WW) NVIDIA(0):     to FALSE; e.g.,
(WW) NVIDIA(0): 
(WW) NVIDIA(0):   Option "UseEDID" "FALSE"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Note that, rather than globally disable all uses of the EDID,
(WW) NVIDIA(0):     you can individually disable each particular use of the
(WW) NVIDIA(0):     EDID; e.g.,
(WW) NVIDIA(0): 
(WW) NVIDIA(0):   Option "UseEDIDFreqs" "FALSE"
(WW) NVIDIA(0):   Option "UseEDIDDpi" "FALSE"
(WW) NVIDIA(0):   Option "ModeValidation" "NoEdidModes"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): See Appendix D: X Config Options in the README for details on
(WW) NVIDIA(0):     each of these options.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Invalid ConnectedMonitor request; request was for 'TV-0', but
(WW) NVIDIA(GPU-0):     the valid display devices are 'CRT-0, DFP-0'.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.45.79
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600_60"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[8] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[10] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[36] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[37] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "800x600_60"
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```

---

### Post by CanadianMan on 2007-02-07
Just some more information, I would really like to get this working.  I'm not too thrilled on watching a $500 box do nothing.

This is the tv I own.

[http://www.sanyo.com/entertainment/televisions/flatscreen/index.cfm?productID=1111](http://www.sanyo.com/entertainment/televisions/flatscreen/index.cfm?productID=1111)

These are the cables I bought to hook my htpc to my tv.

[http://www.newegg.com/Product/Product.asp?Item=N82E16812203023](http://www.newegg.com/Product/Product.asp?Item=N82E16812203023)

I hope some of this is useful to someone.  Thank you again.

---

### Post by snake98 on 2007-02-20
The 6150 Doesn't support Dvi to Componet, I currenlty have the 6150 and ran into the same problem.  The 6150 only has one digital to analog converter, so you can always use the dvi, but only one of the following, vga port,rgb port, or the tv port.  And you cannot use a dvi to componet cable.  sorry for the bad info.

---

### Post by CanadianMan on 2007-02-26
Thank you Snake98 for your response.  I bought myself a 6200 card with s-video out and have tv-out working just fine now. Thanks again.

---

