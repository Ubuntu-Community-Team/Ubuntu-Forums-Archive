---
title: "X won't start: &quot;Mode pool is empty&quot; &amp; &quot;No valid modes found&quot;"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by SubGothius on 2007-11-25
X will not start for me in Gutsy (fresh nuke'n'pave install), tho' it worked just fine in Edgy and Feisty, as well as in Debian Etch. I reckon this has something to do with the newer version of Xorg, since the same thing started happening in Debian Lenny (testing) at some point. My vidcard is an ixMicro/IMS TwinTurbo 128+, so "imstt" is indeed the correct driver module, which worked fine in previous releases. Towards the end of my Xorg.0.log there's a whole bunch of lines like this:

(II) imstt(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1024x768" (unknown reason)
*(Repeat w/ a huge variety of other possible resolutions)*

...followed by this:

(WW) imstt(0): Mode pool is empty
(EE) imstt(0): No valid modes found

I have tried various mods to my xorg.conf, all to no avail, including:[list]
[*]Corrected HorizSync and VertRefresh to match monitor's actual range;
[*]Using a tried'n'true custom xorg.conf saved from previous versions;
[*]Running 'sudo dpkg-reconfigure xserver-xorg' to build a fresh xorg.conf;
[*]Adding/omitting a PCI BusID (I have only one vidcard, and Xorg had worked fine without any BusID in earlier releases);
[*]Changing the "UseFBDev" option to "false";
[*]Adding a Modeline (actually tried two slightly different modelines produced by different Modeline Generator pages)[/list]

**My xorg.conf:**
(commenting included to show experiments)
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"mac"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
	Driver		"imstt"
#	BusID		"PCI:0:14:0"
	Option		"UseFBDev"		"true"
#	Option		"UseFBDev"		"false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
#	Modeline "1024x768" 81.55 1024 1064 1168 1352 768 768 770 804
#	Modeline "1024x768@75" 85.52 1024 1056 1376 1408 768 782 792 807
	Option		"DPMS"
	HorizSync	31-65
	VertRefresh	60-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	DefaultFbBpp	32
	SubSection "Display"
#		Depth		24
#		FbBpp		32
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

**Complete Xorg.0.log:**
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux vesta 2.6.22-14-powerpc-smp #1 SMP Sun Oct 14 22:11:04 GMT 2007 ppc
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 12 00:20:03 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x101fb2e8
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
(II) PCI: 00:0b:0: chip 106b,0001 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:0d:0: chip 1045,c861 card 1045,c861 rev 10 class 0c,03,10 hdr 00
(II) PCI: 00:0e:0: chip 10e0,9128 card 0000,0000 rev 01 class 03,80,00 hdr 00
(II) PCI: 00:0f:0: chip 1011,0021 card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 106b,0002 card 0000,0000 rev 02 class ff,00,00 hdr 00
(II) PCI: 01:03:0: chip 11c1,5811 card dead,0800 rev 04 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:15:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x80800000 - 0x808fffff (0x100000) MX[B]
(--) PCI:*(0:14:0) Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128] rev 1, Mem @ 0x82000000/24, BIOS @ 0x80910000/16
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
(II) Active PCI resource ranges:
	[0] -1	0	0x80800000 - 0x80800fff (0x1000) MX[B]
	[1] -1	0	0xf3000000 - 0xf301ffff (0x20000) MX[B]
	[2] -1	0	0x80900000 - 0x80900fff (0x1000) MX[B]
	[3] -1	0	0x80910000 - 0x8091ffff (0x10000) MX[B](B)
	[4] -1	0	0x82000000 - 0x82ffffff (0x1000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x80800000 - 0x80800fff (0x1000) MX[B]
	[1] -1	0	0xf3000000 - 0xf301ffff (0x20000) MX[B]
	[2] -1	0	0x80900000 - 0x80900fff (0x1000) MX[B]
	[3] -1	0	0x80910000 - 0x8091ffff (0x10000) MX[B](B)
	[4] -1	0	0x82000000 - 0x82ffffff (0x1000000) MX[B](B)
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
	[4] -1	0	0x80800000 - 0x80800fff (0x1000) MX[B]
	[5] -1	0	0xf3000000 - 0xf301ffff (0x20000) MX[B]
	[6] -1	0	0x80900000 - 0x80900fff (0x1000) MX[B]
	[7] -1	0	0x80910000 - 0x8091ffff (0x10000) MX[B](B)
	[8] -1	0	0x82000000 - 0x82ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
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
(II) LoadModule: "imstt"
(II) Loading /usr/lib/xorg/modules/drivers//imstt_drv.so
(II) Module imstt: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) IMSTT: driver (version 1.1.0) for IMS TwinTurbo chipsets : imstt128,
	imstt3d
(II) Primary Device is: PCI 00:0e:0
(--) Assigning device section with no busID to primary device
(--) Chipset imstt128 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x80800000 - 0x80800fff (0x1000) MX[B]
	[5] -1	0	0xf3000000 - 0xf301ffff (0x20000) MX[B]
	[6] -1	0	0x80900000 - 0x80900fff (0x1000) MX[B]
	[7] -1	0	0x80910000 - 0x8091ffff (0x10000) MX[B](B)
	[8] -1	0	0x82000000 - 0x82ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x80800000 - 0x80800fff (0x1000) MX[B]
	[5] -1	0	0xf3000000 - 0xf301ffff (0x20000) MX[B]
	[6] -1	0	0x80900000 - 0x80900fff (0x1000) MX[B]
	[7] -1	0	0x80910000 - 0x8091ffff (0x10000) MX[B](B)
	[8] -1	0	0x82000000 - 0x82ffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] 0	0	0xf20003b0 - 0xf20003bb (0xc) IS[B]
	[15] 0	0	0xf20003c0 - 0xf20003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) imstt(0): Depth 24, (**) framebuffer bpp 32
(==) imstt(0): RGB weight 888
(==) imstt(0): Default visual is TrueColor
(**) imstt(0): Option "UseFBDev" "true"
(**) imstt(0): Using SW cursor
(**) imstt(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 1.2
(**) imstt(0): Chipset: "imstt128"
(==) imstt(0): Using gamma correction (1.0, 1.0, 1.0)
(--) imstt(0): using IBM ramdac
(--) imstt(0): revision 2
(--) imstt(0): probed videoram = 4096k
(II) imstt(0): Generic Monitor: Using hsync range of 28.00-65.00 kHz
(II) imstt(0): Generic Monitor: Using vrefresh range of 43.00-75.00 Hz
(II) imstt(0): Clock range:  20.00 to 120.00 MHz
(II) imstt(0): Not using default mode "640x350" (unknown reason)
(II) imstt(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "640x400" (unknown reason)
(II) imstt(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "720x400" (unknown reason)
(II) imstt(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "640x480" (unknown reason)
(II) imstt(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "640x480" (unknown reason)
(II) imstt(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "640x480" (unknown reason)
(II) imstt(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "640x480" (unknown reason)
(II) imstt(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "800x600" (unknown reason)
(II) imstt(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "800x600" (unknown reason)
(II) imstt(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "800x600" (unknown reason)
(II) imstt(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "800x600" (unknown reason)
(II) imstt(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "800x600" (unknown reason)
(II) imstt(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1024x768" (unknown reason)
(II) imstt(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1024x768" (unknown reason)
(II) imstt(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1024x768" (unknown reason)
(II) imstt(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1024x768" (unknown reason)
(II) imstt(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1152x864" (unknown reason)
(II) imstt(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) imstt(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) imstt(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) imstt(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) imstt(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) imstt(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) imstt(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) imstt(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) imstt(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) imstt(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) imstt(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) imstt(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "832x624" (unknown reason)
(II) imstt(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x768" (unknown reason)
(II) imstt(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1280x800" (unknown reason)
(II) imstt(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1152x768" (unknown reason)
(II) imstt(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) imstt(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) imstt(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) imstt(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) imstt(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) imstt(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) imstt(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) imstt(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) imstt(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) imstt(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) imstt(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) imstt(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) imstt(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) imstt(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(WW) imstt(0): Mode pool is empty
(EE) imstt(0): No valid modes found

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x94) [0x10093f44]
1: [0x100344]
2: /usr/lib/xorg/modules/drivers//imstt_drv.so [0xf941520]
3: /usr/lib/xorg/modules/drivers//imstt_drv.so [0xf94186c]
4: /usr/bin/X(InitOutput+0xb08) [0x1006e2c8]
5: /usr/bin/X(main+0x294) [0x1002e064]
6: /lib/libc.so.6 [0xfc79380]
7: /lib/libc.so.6 [0xfc795c4]

Fatal server error:
Caught signal 11.  Server aborting
```

---

