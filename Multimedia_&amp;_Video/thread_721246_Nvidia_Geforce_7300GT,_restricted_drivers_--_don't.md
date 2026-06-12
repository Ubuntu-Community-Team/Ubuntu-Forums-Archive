---
title: "Nvidia Geforce 7300GT, restricted drivers -- don't work for me."
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by shadowfirebird on 2008-03-11
Hi folks, any help would be wonderful.

It would appear that my Nvidia 7300GT doesn't like the 'nvidia' restricted driver.  It's okay with Ubuntu's 'nv' one.  A quick summary:

1) In Gnome, I open the "restricted drivers" screen and tick the box.  Everything appears to work.

2) Restart. But now we have low graphics mode, and a dialog "your screen and graphics card could not be detected correctly".  It doesn't matter what I do here, I always get:

3) GDM login, low graphics mode.  I log into Gnome again.

4) looking at the "screens & graphics" screen, I see I am using the Vesa driver; and the "plug and play" screen.  Changing these settings does nothing; I can't even change back to the 'nv' driver (and yes, I've tried logging out, even rebooting).

4a) I can use the "test" button, though.  If I change to the nv driver and change back to my real monitor, then clicking it shows me a good high-res screen.  Doing the same with the 'nvidia' driver makes the "screens & graphics" screen close (presumably, crash).

5) I *can* get back to the nv driver, by doing a 'sudo dpkg-reconfig xserver-xorg', answering all the questions, and *then* going into the "screens & graphics" screen.  nothing else seems to work.


I have a motherboard with a graphic card built in and no way to turn it off in the BIOS -- perhaps that's something to do with it, although lspci only shows one graphics card so the motherboard has presumably switched out its graphics automagically.  OTOH Ubuntu can't autodetect my monitor now.

I've tried Envy, with, I'm afraid, exactly the same results.  The "change nv to nvidia" fix doesn't seem to apply here.  I'm afraid I'm out of ideas.  All suggestions would be greatfully appreciated.


Okay, some outputs now, taken from the Gnome session at point (3) above:

**lspci:**
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GT (rev a2)

```

**xorg.conf:**
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Nvidia GE7300GT"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Hanns-G"
	Option		"DPMS"
	Horizsync	30-100
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GE7300GT"
	Monitor		"Hanns-G"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

**/var/log/xorg.0.log:**
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux Blake 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 11 10:33:32 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
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
(II) Loader magic: 0x81e9800
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
(II) PCI: 00:00:0: chip 1106,0204 card 1106,0204 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 104c,8023 card 11bd,000e rev 00 class 0c,00,10 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1458,b003 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1458,5002 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1458,5004 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1458,5004 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1458,5001 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1458,a002 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1458,e000 rev 78 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,02e2 card 0000,0000 rev a2 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x02e2) rev 162, Mem @ 0xe4000000/24, 0xd0000000/28, 0xe5000000/24
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe7006000 - 0xe70060ff (0x100) MX[B]
	[1] -1	0	0xe7005000 - 0xe70050ff (0x100) MX[B]
	[2] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[3] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[9] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[10] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[20] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe7006000 - 0xe70060ff (0x100) MX[B]
	[1] -1	0	0xe7005000 - 0xe70050ff (0x100) MX[B]
	[2] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[3] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[9] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[10] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[20] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
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
	[4] -1	0	0xe7006000 - 0xe70060ff (0x100) MX[B]
	[5] -1	0	0xe7005000 - 0xe70050ff (0x100) MX[B]
	[6] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[7] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[24] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[25] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[26] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
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
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7006000 - 0xe70060ff (0x100) MX[B]
	[5] -1	0	0xe7005000 - 0xe70050ff (0x100) MX[B]
	[6] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[7] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[24] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[25] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[26] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7006000 - 0xe70060ff (0x100) MX[B]
	[5] -1	0	0xe7005000 - 0xe70050ff (0x100) MX[B]
	[6] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[7] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[27] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[28] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[29] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
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
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G73 Board - p508h0  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 146 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 147 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 1400
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 148 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2800
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 152 (2048x1536)
	ModeAttributes: 0x3db
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009415
	BytesPerScanline: 8192
	XResolution: 2048
	YResolution: 1536
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 8192
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Failsafe Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Failsafe Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (111)
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
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7006000 - 0xe70060ff (0x100) MX[B]
	[5] -1	0	0xe7005000 - 0xe70050ff (0x100) MX[B]
	[6] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[7] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[27] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[28] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[29] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G73 Board - p508h0  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xd0000000,0x10000000)
(II) VESA(0): virtual address = 0xa7a3c000,
	physical address = 0xd0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

```

**dmesg:**
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f51d0
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6B50 checksum 0
[    0.000000] ACPI: RSDP 000F6B50, 0014 (r0 VIAK8 )
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 1FFF30C0, 44CB (r1 VIAK8  AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF75C0, 005A (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=87736db3-0905-4da3-87b1-919cf3c7215e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1808.388 MHz processor.
[   22.612253] Console: colour VGA+ 80x25
[   22.612483] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.612893] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.622200] Memory: 508300k/524224k available (2015k kernel code, 15408k reserved, 915k data, 364k init, 0k highmem)
[   22.622210] virtual kernel memory layout:
[   22.622211]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   22.622213]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.622214]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   22.622215]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   22.622217]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   22.622218]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   22.622219]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   22.622223] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.622256] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.702250] Calibrating delay using timer specific routine.. 3620.96 BogoMIPS (lpj=7241934)
[   22.702272] Security Framework v1.0.0 initialized
[   22.702277] SELinux:  Disabled at boot.
[   22.702289] Mount-cache hash table entries: 512
[   22.702391] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   22.702399] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.702402] CPU: L2 Cache: 128K (64 bytes/line)
[   22.702404] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   22.702413] Compat vDSO mapped to ffffe000.
[   22.702423] Checking 'hlt' instruction... OK.
[   22.718369] SMP alternatives: switching to UP code
[   22.718618] Freeing SMP alternatives: 11k freed
[   22.718928] Early unpacking initramfs... done
[   23.034815] ACPI: Core revision 20070126
[   23.034885] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.107341] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
[   23.107364] Total of 1 processors activated (3620.96 BogoMIPS).
[   23.107864] ENABLING IO-APIC IRQs
[   23.108183] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   23.254058] Brought up 1 CPUs
[   23.254182] Booting paravirtualized kernel on bare hardware
[   23.254271] Time: 10:31:42  Date: 02/11/108
[   23.254293] NET: Registered protocol family 16
[   23.254379] EISA bus registered
[   23.254397] ACPI: bus type pci registered
[   23.261971] PCI: PCI BIOS revision 2.10 entry at 0xfb140, last bus=1
[   23.261973] PCI: Using configuration type 1
[   23.261975] Setting up standard PCI resources
[   23.264964] ACPI: EC: Look up EC in DSDT
[   23.268643] ACPI: Interpreter enabled
[   23.268648] ACPI: (supports S0 S1 S4 S5)
[   23.268665] ACPI: Using IOAPIC for interrupt routing
[   23.273261] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.273266] PCI: Probing PCI hardware (bus 00)
[   23.274133] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.307250] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   23.307384] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[   23.307517] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[   23.307635] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.307748] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.307856] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.307964] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.308073] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.308230] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[   23.308386] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[   23.308558] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[   23.308714] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[   23.308812] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.308823] pnp: PnP ACPI init
[   23.308838] ACPI: bus type pnp registered
[   23.311613] pnp: PnP ACPI: found 13 devices
[   23.311616] ACPI: ACPI bus type pnp unregistered
[   23.311621] PnPBIOS: Disabled by ACPI PNP
[   23.311671] PCI: Using ACPI for IRQ routing
[   23.311674] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.336825] NET: Registered protocol family 8
[   23.336827] NET: Registered protocol family 20
[   23.336902] pnp: 00:00: iomem range 0xcde00-0xcffff has been reserved
[   23.336905] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   23.336908] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   23.336911] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   23.336917] pnp: 00:02: ioport range 0x4000-0x407f has been reserved
[   23.336920] pnp: 00:02: ioport range 0x40f0-0x40ff has been reserved
[   23.336923] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   23.337995] Time: tsc clocksource has been installed.
[   23.367176] PCI: Bridge: 0000:00:01.0
[   23.367178]   IO window: disabled.
[   23.367183]   MEM window: e4000000-e6ffffff
[   23.367186]   PREFETCH window: d0000000-dfffffff
[   23.367202] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.367216] NET: Registered protocol family 2
[   23.406008] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.406055] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   23.406226] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   23.406366] TCP: Hash tables configured (established 16384 bind 16384)
[   23.406369] TCP reno registered
[   23.418093] checking if image is initramfs... it is
[   23.869782] Switched to high resolution mode on CPU 0
[   24.039751] Freeing initrd memory: 7037k freed
[   24.040095] audit: initializing netlink socket (disabled)
[   24.040108] audit(1205231502.044:1): initialized
[   24.041709] VFS: Disk quotas dquot_6.5.1
[   24.041757] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.041849] io scheduler noop registered
[   24.041851] io scheduler anticipatory registered
[   24.041853] io scheduler deadline registered
[   24.041869] io scheduler cfq registered (default)
[   24.041882] PCI: VIA PCI bridge detected. Disabling DAC.
[   24.041949] Boot video device is 0000:01:00.0
[   24.042089] isapnp: Scanning for PnP cards...
[   24.396124] isapnp: No Plug & Play device found
[   24.437418] Real Time Clock Driver v1.12ac
[   24.437521] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.437614] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.437892] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.438648] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.438977] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.439646] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.439853] input: Macintosh mouse button emulation as /class/input/input0
[   24.439920] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.440287] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.440292] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.440421] mice: PS/2 mouse device common for all mice
[   24.440515] EISA: Probing bus 0 at eisa.0
[   24.440536] Cannot allocate resource for EISA slot 4
[   24.440538] Cannot allocate resource for EISA slot 5
[   24.440551] EISA: Detected 0 cards.
[   24.440707] TCP cubic registered
[   24.440724] NET: Registered protocol family 1
[   24.440745] Using IPI No-Shortcut mode
[   24.440930]   Magic number: 0:344:527
[   24.441351] Freeing unused kernel memory: 364k freed
[   24.477507] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.668391] AppArmor: AppArmor initialized<5>audit(1205231503.544:2):  type=1505 info="AppArmor initialized" pid=1196
[   25.676393] fuse init (API version 7.8)
[   25.682069] Failure registering capabilities with primary security module.
[   26.317810] SCSI subsystem initialized
[   26.345410] libata version 2.21 loaded.
[   26.348478] sata_via 0000:00:0f.0: version 2.2
[   26.348787] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[   26.348790] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   26.348798] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   26.348839] sata_via 0000:00:0f.0: routed to hard irq line 11
[   26.348921] scsi0 : sata_via
[   26.348975] scsi1 : sata_via
[   26.348999] ata1: SATA max UDMA/133 cmd 0x00019000 ctl 0x00019402 bmdma 0x0001a000 irq 16
[   26.349003] ata2: SATA max UDMA/133 cmd 0x00019800 ctl 0x00019c02 bmdma 0x0001a008 irq 16
[   26.353629] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.353634] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.373479] usbcore: registered new interface driver usbfs
[   26.373500] usbcore: registered new interface driver hub
[   26.384260] usbcore: registered new device driver usb
[   26.385060] USB Universal Host Controller Interface driver v3.0
[   26.521175] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   26.552431] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.588449] Floppy drive(s): fd0 is 1.44M
[   26.622372] FDC 0 is a post-1991 82077
[   26.764289] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.774989] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   26.775008] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   26.775019] VP_IDE: chipset revision 6
[   26.775021] VP_IDE: not 100% native mode: will probe irqs later
[   26.775031] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   26.775039]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:DMA
[   26.775051]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:DMA, hdd:DMA
[   26.775058] Probing IDE interface ide0...
[   27.188164] hda: Maxtor 6Y120L0, ATA DISK drive
[   27.468027] hdb: WDC WD1600BB-00RDA0, ATA DISK drive
[   27.524348] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.532387] Probing IDE interface ide1...
[   28.395560] hdc: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive
[   29.179172] hdd: Memorex SixteenMAXX 1040, ATAPI CD/DVD-ROM drive
[   29.236057] ide1 at 0x170-0x177,0x376 on irq 15
[   29.240835] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 17
[   29.291110] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e7004000-e70047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.292459] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[   29.292464] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   29.292472] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   29.292483] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   29.292697] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.292728] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000ac00
[   29.292847] usb usb1: configuration #1 chosen from 1 choice
[   29.292871] hub 1-0:1.0: USB hub found
[   29.292878] hub 1-0:1.0: 2 ports detected
[   29.297445] hda: max request size: 128KiB
[   29.311352] hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[   29.311627] hda: cache flushes supported
[   29.311679]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 hda10 hda11<6>ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   29.395116] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   29.395137] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.395159] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000b000
[   29.395249] usb usb2: configuration #1 chosen from 1 choice
[   29.395272] hub 2-0:1.0: USB hub found
[   29.395279] hub 2-0:1.0: 2 ports detected
[   29.402709]  hda12 hda13 hda14 hda15 hda16 >
[   29.458582] hdb: max request size: 512KiB
[   29.466330] hdb: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[   29.466408] hdb: cache flushes supported
[   29.466448]  hdb: hdb1
[   29.496525] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.496533] Uniform CD-ROM driver Revision: 3.20
[   29.499096] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   29.499110] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.499132] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.499154] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000b400
[   29.499249] usb usb3: configuration #1 chosen from 1 choice
[   29.499273] hub 3-0:1.0: USB hub found
[   29.499279] hub 3-0:1.0: 2 ports detected
[   29.501289] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   29.602983] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   29.602997] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   29.603019] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   29.603041] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000b800
[   29.603140] usb usb4: configuration #1 chosen from 1 choice
[   29.603167] hub 4-0:1.0: USB hub found
[   29.603174] hub 4-0:1.0: 2 ports detected
[   29.707055] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   29.707070] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   29.707096] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   29.707135] ehci_hcd 0000:00:10.4: irq 18, io mem 0xe7005000
[   29.762826] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   29.762842] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.762962] usb usb5: configuration #1 chosen from 1 choice
[   29.762986] hub 5-0:1.0: USB hub found
[   29.762994] hub 5-0:1.0: 8 ports detected
[   29.867246] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[   29.867251] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   29.867258] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
[   29.867359] eth0: VIA Rhine II at 0x1c000, 00:14:85:c9:f6:ed, IRQ 19.
[   29.868070] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   30.386532] Attempting manual resume
[   30.386536] swsusp: Resume From Partition 3:7
[   30.386538] PM: Checking swsusp image.
[   30.394097] PM: Resume from disk failed.
[   30.430248] kjournald starting.  Commit interval 5 seconds
[   30.430261] EXT3-fs: mounted filesystem with ordered data mode.
[   30.562493] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00308d0120c0958d]
[   31.074148] usb 5-3: new high speed USB device using ehci_hcd and address 3
[   31.223764] usb 5-3: configuration #1 chosen from 1 choice
[   31.461944] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   31.660788] usb 1-2: configuration #1 chosen from 1 choice
[   34.138415] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.720782] Linux agpgart interface v0.102 (c) Dave Jones
[   35.780693] agpgart: Detected AGP bridge 0
[   35.782766] agpgart: AGP aperture is 64M @ 0xe0000000
[   35.900848] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.092720] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.795986] input: PC Speaker as /class/input/input2
[   37.215199] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8704
[   37.215218] usbcore: registered new interface driver usblp
[   37.215222] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   37.447037] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   37.448647] usbcore: registered new interface driver libusual
[   37.574127] Initializing USB Mass Storage driver...
[   37.574307] scsi2 : SCSI emulation for USB Mass Storage devices
[   37.606171] usbcore: registered new interface driver usb-storage
[   37.606176] USB Mass Storage support registered.
[   37.606255] usb-storage: device found at 3
[   37.606257] usb-storage: waiting for device to settle before scanning
[   37.717589] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   37.717593] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   37.717601] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   37.717738] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   38.966223] lp: driver loaded but no devices found
[   39.024945] Adding 524120k swap on /dev/hda14.  Priority:-1 extents:1 across:524120k
[   39.025277] Adding 524120k swap on /dev/hda7.  Priority:-2 extents:1 across:524120k
[   39.364932] EXT3 FS on hda1, internal journal
[   41.531216] kjournald starting.  Commit interval 5 seconds
[   41.531628] EXT3 FS on hda5, internal journal
[   41.531633] EXT3-fs: mounted filesystem with ordered data mode.
[   41.565956] kjournald starting.  Commit interval 5 seconds
[   41.566280] EXT3 FS on hda13, internal journal
[   41.566285] EXT3-fs: mounted filesystem with ordered data mode.
[   41.582759] kjournald starting.  Commit interval 5 seconds
[   41.582934] EXT3 FS on hda10, internal journal
[   41.582938] EXT3-fs: mounted filesystem with ordered data mode.
[   41.599118] kjournald starting.  Commit interval 5 seconds
[   41.599302] EXT3 FS on hda15, internal journal
[   41.599306] EXT3-fs: mounted filesystem with ordered data mode.
[   41.824431] kjournald starting.  Commit interval 5 seconds
[   41.824781] EXT3 FS on hda11, internal journal
[   41.824786] EXT3-fs: mounted filesystem with ordered data mode.
[   41.871768] kjournald starting.  Commit interval 5 seconds
[   41.896925] EXT3 FS on hda8, internal journal
[   41.896933] EXT3-fs: mounted filesystem with ordered data mode.
[   42.600589] usb-storage: device scan complete
[   42.608423] scsi 2:0:0:0: Direct-Access     GENERIC  USB Storage-SMC  I19B PQ: 0 ANSI: 0 CCS
[   42.613355] scsi 2:0:0:1: Direct-Access     GENERIC  USB Storage-CFC  I19B PQ: 0 ANSI: 0 CCS
[   42.617587] scsi 2:0:0:2: Direct-Access     GENERIC  USB Storage-SDC  I19B PQ: 0 ANSI: 0 CCS
[   42.621815] scsi 2:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  I19B PQ: 0 ANSI: 0 CCS
[   42.733774] sd 2:0:0:0: [sda] Attached SCSI removable disk
[   42.735845] sd 2:0:0:1: [sdb] Attached SCSI removable disk
[   42.738527] sd 2:0:0:2: [sdc] Attached SCSI removable disk
[   42.739784] sd 2:0:0:3: [sdd] Attached SCSI removable disk
[   42.757836] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   42.757856] sd 2:0:0:1: Attached scsi generic sg1 type 0
[   42.757874] sd 2:0:0:2: Attached scsi generic sg2 type 0
[   42.757898] sd 2:0:0:3: Attached scsi generic sg3 type 0
[   45.620162] input: Power Button (FF) as /class/input/input4
[   45.624437] ACPI: Power Button (FF) [PWRF]
[   45.658041] input: Power Button (CM) as /class/input/input5
[   45.662277] ACPI: Power Button (CM) [PWRB]
[   45.806979] No dock devices found.
[   46.062375] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
[   46.062406] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   46.062409] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   50.719424] Failure registering capabilities with primary security module.
[   51.117005] NET: Registered protocol family 10
[   51.117119] lo: Disabled Privacy Extensions
[   51.248405] Failure registering capabilities with primary security module.
[   51.408082] ppdev: user-space parallel port driver
[   51.685380] audit(1205231530.485:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4984 profile="/usr/sbin/cupsd"
[   51.741372] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   51.741377] apm: overridden by ACPI.
[   33.556000] Marking TSC unstable due to: cpufreq changes.
[   33.560000] Time: acpi_pm clocksource has been installed.
[   34.072000] Clocksource tsc unstable (delta = -222245697 ns)
[   34.432000] Bluetooth: Core ver 2.11
[   34.432000] NET: Registered protocol family 31
[   34.432000] Bluetooth: HCI device and connection manager initialized
[   34.432000] Bluetooth: HCI socket layer initialized
[   34.524000] Bluetooth: L2CAP ver 2.8
[   34.524000] Bluetooth: L2CAP socket layer initialized
[   34.564000] Bluetooth: RFCOMM socket layer initialized
[   34.564000] Bluetooth: RFCOMM TTY layer initialized
[   34.564000] Bluetooth: RFCOMM ver 1.8
[   38.856000] NET: Registered protocol family 17
[   38.960000] eth0: no IPv6 routers present

```

As I say, all suggestions greatfully received...

---

### Post by shadowfirebird on 2008-03-11
::sigh:: sorry, I forgot to say: Gutsy.

---

