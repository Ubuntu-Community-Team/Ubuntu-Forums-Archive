---
title: "4 monitors, 2x ATI radeon 2600"
date: 2008-07-07
forum: Multimedia Software
---

### Post by Geoscientist on 2008-07-07
I am trying to run 4 monitors on ubuntu. 
2 x Radeon 2600 cards, each with 2 monitors. 

Here is the current xorg.conf file, which fails. To be followed with an error report once I replace all the 8) smileys with 8_)

Any advice would be greatly appreciated. 

Thankyou. 

Xorg.conf follows;


```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Radeon2600a0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Radeon2600a1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Device"
	Identifier	"Radeon2600b0"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Radeon2600b1"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screena0"
	Monitor		"Generic Monitor"
	Device		"Radeon2600a0"
EndSection

Section "Screen"
	Identifier	"Screena1"
	Monitor		"Generic Monitor"
	Device		"Radeon2600a1"
EndSection

Section "Screen"
	Identifier	"Screenb0"
	Monitor		"Generic Monitor"
	Device		"Radeon2600b0"
EndSection

Section "Screen"
	Identifier	"Screenb1"
	Monitor		"Generic Monitor"
	Device		"Radeon2600b1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screena0" 0 0
	Screen		"Screena1" RightOf "Screena0"
	Screen		"Screenb0" RightOf "Screena1"
	Screen		"Screenb1" RightOf "Screenb0"
EndSection
```

---

### Post by Geoscientist on 2008-07-07
And here is the error report for when it fails. 

```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux occam-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Jul  7 16:30:30 2008
(++) Using config file: "test_xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screena0" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Radeon2600a0"
(**) |-->Screen "Screena1" (1)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Radeon2600a1"
(**) |-->Screen "Screenb0" (2)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Radeon2600b0"
(**) |-->Screen "Screenb1" (3)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Radeon2600b1"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "X11_cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	X11_misc,
	X11_100dpi/:unscaled,
	X11_75dpi/:unscaled,
	X11_Type1,
	X11_100dpi,
	X11_75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "usr\lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) Loading usr\lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(--) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,294a card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1458,b000 rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,9589 card 1787,2233 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,aa08 card 1787,aa08 rev 00 class 04,03,00 hdr 80
(II) PCI: 02:00:0: chip 1002,9589 card 1787,2233 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,aa08 card 1787,aa08 rev 00 class 04,03,00 hdr 80
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1458,e000 rev 01 class 02,00,00 hdr 00
(II) PCI: 05:06:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x9589) rev 0, Mem @ 0xd0000000/28, 0xf7000000/16, I/O @ 0xa000/8
(--) PCI: (2:0:0) ATI Technologies Inc unknown chipset (0x9589) rev 0, Mem @ 0xe0000000/28, 0xf5000000/16, I/O @ 0xb000/8
(II) Loading usr\lib/xorg/modules/extensions//libextmod.so
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
(II) Loading usr\lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) Loading usr\lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading usr\lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) Loading usr\lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) Loading usr\lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Loading usr\lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) Loading usr\lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) Loading usr\lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Loading usr\lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18_) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28_) (PCIE),
	ATI Mobility FireGL V5100 (M28_) (PCIE),
	ATI Mobility Radeon X800 (M28_) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:00:0
(--) Chipset ATI Radeon HD 2600 Pro found
(--) Chipset ATI Radeon HD 2600 Pro found
(--) Chipset ATI Radeon HD 2600 Pro found
(--) Chipset ATI Radeon HD 2600 Pro found
(II) RADEON(0): MMIO registers at 0x00000000f7000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Screena0" for depth/fbbpp 24/32
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading usr\lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading usr\lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): using shadow framebuffer
(II) Loading usr\lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): Getting BIOS copy from legacy VBIOS location
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1787 SubsystemID: 0x2233
	IOBaseAddress: 0xa000
(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 600000
(II) RADEON(0): Default Memory Clock: 405000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(WW) RADEON(0): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
Please use the radeon MergedFB option if you want Dual-head with DRI.
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Using 131072k of videoram for primary head
(II) RADEON(0): Color tiling disabled
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 405.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 000a 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 2113 19
src object id 2116 22
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[1] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 0002 02
src object id 210f 15
src object id 2115 21
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[0] EngineID: 1 I2CAddr: 0
record type 2
record type 4
(II) RADEON(0): Output None using monitor section Generic Monitor
(II) RADEON(0): Output DVI-1 has no monitor section
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x7e50
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "BNQ", prod id 30373
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x76.0  140.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (81.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x71.9  133.00  1280 1368 1504 1728  1024 1027 1034 1070 -hsync +vsync (77.0 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 203
(II) RADEON(0): Year: 2006  Week: 15
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
(II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: BenQ FP91G+
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0009d1a576cb000000
(II) RADEON(0): 	0f1001036c261e78ea6d66a25a4c9d23
(II) RADEON(0): 	134f54bdef80714f81908180818c0101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001ed50980a0205e6310
(II) RADEON(0): 	10605208782d1100001a000000fd0038
(II) RADEON(0): 	4c1f530e000a202020202020000000fc
(II) RADEON(0): 	0042656e512046503931472b0a2000c7
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "BNQ", prod id 30373
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x76.0  140.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (81.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x71.9  133.00  1280 1368 1504 1728  1024 1027 1034 1070 -hsync +vsync (77.0 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 203
(II) RADEON(0): Year: 2006  Week: 15
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
(II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: BenQ FP91G+
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0009d1a576cb000000
(II) RADEON(0): 	0f1001036c261e78ea6d66a25a4c9d23
(II) RADEON(0): 	134f54bdef80714f81908180818c0101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001ed50980a0205e6310
(II) RADEON(0): 	10605208782d1100001a000000fd0038
(II) RADEON(0): 	4c1f530e000a202020202020000000fc
(II) RADEON(0): 	0042656e512046503931472b0a2000c7
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "BNQ", prod id 30373
(II) RADEON(0): Output DVI-1 connected
(II) RADEON(0): Output DVI-1 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (380, 300) mm
(**) RADEON(0): DPI set to (85, 101)
(II) Loading usr\lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Module "ramdac" already built-in
(==) RADEON(0): No acceleration support available on R600 yet.
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): MM_TABLE: bb-c9-05-e8-c7-05-24-e3-0a-c4-e8-bb-04-b8
(II) RADEON(0): This card has MM_TABLE we do not recognize.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(1): MMIO registers at 0x00000000f7000000: size 64KB
(II) RADEON(1): PCI bus 1 card 0 func 0
(II) RADEON(1): Creating default Display subsection in Screen section
	"Screena1" for depth/fbbpp 24/32
(**) RADEON(1): Depth 24, (--) framebuffer bpp 32
(II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(1): Default visual is TrueColor
(II) Reloading usr\lib/xorg/modules//libvgahw.so
(==) RADEON(1): RGB weight 888
(II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
(II) Reloading usr\lib/xorg/modules//libint10.so
(II) RADEON(1): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(1): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
(WW) RADEON(1): R600 support is mostly incomplete and very experimental
(--) RADEON(1): Linear framebuffer at 0x00000000d0000000
(II) RADEON(1): PCIE card detected
(II) RADEON(1): using shadow framebuffer
(II) Reloading usr\lib/xorg/modules//libshadow.so
(II) RADEON(1): ATOM BIOS detected
(II) RADEON(1): Getting BIOS copy from legacy VBIOS location
(II) RADEON(1): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1787 SubsystemID: 0x2233
	IOBaseAddress: 0xa000
(II) RADEON(1): Framebuffer space used by Firmware (kb): 20
(II) RADEON(1): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(1): Framebuffer space used by Firmware (kb): 20
(II) RADEON(1): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(1): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(1): AtomBIOS VRAM scratch base: 0x1fffb000
(II) RADEON(1): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(1): Default Engine Clock: 600000
(II) RADEON(1): Default Memory Clock: 405000
(II) RADEON(1): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(1): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(1): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(1): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(1): Maximum Pixel Clock: 400000
(II) RADEON(1): Reference Clock: 27000
(WW) RADEON(1): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
Please use the radeon MergedFB option if you want Dual-head with DRI.
(II) RADEON(1): Generation 2 PCI interface, using max accessible memory
(II) RADEON(1): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(1): Mapped VideoRAM: 262144 kByte (64 bit DDR SDRAM)
(II) RADEON(1): Using 131072k of videoram for secondary head
(II) RADEON(1): Color tiling disabled
(II) RADEON(1): Max desktop size set to 2560x1200
(II) RADEON(1): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(1): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) RADEON(1): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 405.000000
(II) RADEON(1): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 000a 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 2113 19
src object id 2116 22
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[1] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 0002 02
src object id 210f 15
src object id 2115 21
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[0] EngineID: 1 I2CAddr: 0
record type 2
record type 4
(II) RADEON(1): Output None using monitor section Generic Monitor
(II) RADEON(1): Output DVI-1 has no monitor section
(II) RADEON(1): I2C bus "DVI-1" initialized.
(II) RADEON(1): Output DVI-0 has no monitor section
(II) RADEON(1): I2C bus "DVI-0" initialized.
(II) RADEON(1): Port0:
 Monitor   -- AUTO
 Connector -- SCART
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(1): Output: None, Detected Monitor Type: 0
CailReadATIRegister(7a04) = 1
CailReadATIRegister(7a5c) = 0
CailReadATIRegister(7a54) = 202002
CailReadATIRegister(7a58_) = 0
CailReadATIRegister(7a28_) = 70000
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a50) = 0
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a40) = 1e6
CailWriteATIRegister(7a40,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,1)
CailReadATIRegister(7a5c) = 0
CailWriteATIRegister(7a5c,70000)
CailReadATIRegister(7a54) = 202002
CailWriteATIRegister(7a54,202202)
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
(II) RADEON(1): Delay 5000 usec
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a40) = 0
CailWriteATIRegister(7a40,1e6)
(II) RADEON(1): Delay 200 usec
CailReadATIRegister(7a5c) = 70000
CailWriteATIRegister(7a5c,70100)
(II) RADEON(1): Delay 100 usec
CailReadATIRegister(7a60) = f
CailReadATIRegister(7a5c) = 70100
CailWriteATIRegister(7a5c,0)
CailReadATIRegister(7a54) = 202202
CailWriteATIRegister(7a54,202002)
CailReadATIRegister(7a58_) = 1
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a00) = 1
CailWriteATIRegister(7a00,1)
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a04) = 1
CailWriteATIRegister(7a04,1)
CailReadATIRegister(1724) = 202
CailWriteATIRegister(1724,2)
CailReadATIRegister(1724) = 2
CailWriteATIRegister(1724,202)
Dac detection success
DAC connect 00000202
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(1): Output: None, Detected Monitor Type: 0
CailReadATIRegister(7a04) = 1
CailReadATIRegister(7a5c) = 0
CailReadATIRegister(7a54) = 202002
CailReadATIRegister(7a58_) = 0
CailReadATIRegister(7a28_) = 70000
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a50) = 0
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a40) = 1e6
CailWriteATIRegister(7a40,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,1)
CailReadATIRegister(7a5c) = 0
CailWriteATIRegister(7a5c,70000)
CailReadATIRegister(7a54) = 202002
CailWriteATIRegister(7a54,202202)
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
(II) RADEON(1): Delay 5000 usec
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a40) = 0
CailWriteATIRegister(7a40,1e6)
(II) RADEON(1): Delay 200 usec
CailReadATIRegister(7a5c) = 70000
CailWriteATIRegister(7a5c,70100)
(II) RADEON(1): Delay 100 usec
CailReadATIRegister(7a60) = f
CailReadATIRegister(7a5c) = 70100
CailWriteATIRegister(7a5c,0)
CailReadATIRegister(7a54) = 202202
CailWriteATIRegister(7a54,202002)
CailReadATIRegister(7a58_) = 1
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a00) = 1
CailWriteATIRegister(7a00,1)
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a04) = 1
CailWriteATIRegister(7a04,1)
CailReadATIRegister(1724) = 202
CailWriteATIRegister(1724,2)
CailReadATIRegister(1724) = 2
CailWriteATIRegister(1724,202)
Dac detection success
DAC connect 00000202
in RADEONProbeOutputModes

(II) RADEON(1): Total number of valid Screen mode(s) added: 0
(II) RADEON(1): Output None connected
(II) RADEON(1): Output None using initial mode 1280x768
after xf86InitialConfiguration
(==) RADEON(1): DPI set to (96, 96)
(II) Reloading usr\lib/xorg/modules//libfb.so
(==) RADEON(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Module "ramdac" already built-in
(==) RADEON(1): No acceleration support available on R600 yet.
(==) RADEON(1): Assuming overlay scaler buffer width is 1536
(II) RADEON(1): MM_TABLE: bb-c9-05-e8-c7-05-24-e3-0a-c4-e8-bb-04-b8
(II) RADEON(1): This card has MM_TABLE we do not recognize.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(1): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(1): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(2): MMIO registers at 0x00000000f5000000: size 64KB
(II) RADEON(2): PCI bus 2 card 0 func 0
(II) RADEON(2): Creating default Display subsection in Screen section
	"Screenb0" for depth/fbbpp 24/32
(**) RADEON(2): Depth 24, (--) framebuffer bpp 32
(II) RADEON(2): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(2): Default visual is TrueColor
(II) Reloading usr\lib/xorg/modules//libvgahw.so
(==) RADEON(2): RGB weight 888
(II) RADEON(2): Using 8 bits per RGB (8 bit DAC)
(II) Reloading usr\lib/xorg/modules//libint10.so
(II) RADEON(2): initializing int10
(--) RADEON(2): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
(WW) RADEON(2): R600 support is mostly incomplete and very experimental
(--) RADEON(2): Linear framebuffer at 0x00000000e0000000
(II) RADEON(2): PCIE card detected
(II) RADEON(2): using shadow framebuffer
(II) Reloading usr\lib/xorg/modules//libshadow.so
(II) RADEON(2): ATOM BIOS detected
(II) RADEON(2): Getting BIOS copy from legacy VBIOS location
(II) RADEON(2): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1787 SubsystemID: 0x2233
	IOBaseAddress: 0xa000
(II) RADEON(2): Framebuffer space used by Firmware (kb): 20
(II) RADEON(2): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(2): Framebuffer space used by Firmware (kb): 20
(II) RADEON(2): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(2): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(2): AtomBIOS VRAM scratch base: 0x1fffb000
(II) RADEON(2): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(2): Default Engine Clock: 600000
(II) RADEON(2): Default Memory Clock: 405000
(II) RADEON(2): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(2): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(2): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(2): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(2): Maximum Pixel Clock: 400000
(II) RADEON(2): Reference Clock: 27000
(WW) RADEON(2): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
Please use the radeon MergedFB option if you want Dual-head with DRI.
(II) RADEON(2): Generation 2 PCI interface, using max accessible memory
(II) RADEON(2): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(2): Mapped VideoRAM: 262144 kByte (64 bit DDR SDRAM)
(II) RADEON(2): Using 131072k of videoram for primary head
(II) RADEON(2): Color tiling disabled
(II) RADEON(2): Max desktop size set to 2560x1200
(II) RADEON(2): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(2): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) RADEON(2): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 405.000000
(II) RADEON(2): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 000a 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 2113 19
src object id 2116 22
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[1] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 0002 02
src object id 210f 15
src object id 2115 21
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[0] EngineID: 1 I2CAddr: 0
record type 2
record type 4
(II) RADEON(2): Output None using monitor section Generic Monitor
(II) RADEON(2): Output DVI-1 has no monitor section
(II) RADEON(2): I2C bus "DVI-1" initialized.
(II) RADEON(2): Output DVI-0 has no monitor section
(II) RADEON(2): I2C bus "DVI-0" initialized.
(II) RADEON(2): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x7e50
(II) RADEON(2): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(2): EDID vendor "CMO", prod id 408
(II) RADEON(2): Using EDID range info for horizontal sync
(II) RADEON(2): Using EDID range info for vertical refresh
(II) RADEON(2): Printing DDC gathered Modelines:
(II) RADEON(2): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(2): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(2): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(2): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(2): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(2): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(2): Output: DVI-1, Detected Monitor Type: 1
(II) RADEON(2): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(2): Manufacturer: CMO  Model: 198  Serial#: 16843009
(II) RADEON(2): Year: 2005  Week: 5
(II) RADEON(2): EDID Version: 1.3
(II) RADEON(2): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(2): Sync:  Separate
(II) RADEON(2): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(2): Gamma: 2.20
(II) RADEON(2): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(2): Default color space is primary color space
(II) RADEON(2): First detailed timing is preferred mode
(II) RADEON(2): GTF timings supported
(II) RADEON(2): redX: 0.634 redY: 0.348   greenX: 0.285 greenY: 0.590
(II) RADEON(2): blueX: 0.143 blueY: 0.073   whiteX: 0.313 whiteY: 0.329
(II) RADEON(2): Supported VESA Video Modes:
(II) RADEON(2): 720x400@70Hz
(II) RADEON(2): 640x480@60Hz
(II) RADEON(2): 640x480@67Hz
(II) RADEON(2): 640x480@72Hz
(II) RADEON(2): 640x480@75Hz
(II) RADEON(2): 800x600@56Hz
(II) RADEON(2): 800x600@60Hz
(II) RADEON(2): 800x600@72Hz
(II) RADEON(2): 800x600@75Hz
(II) RADEON(2): 832x624@75Hz
(II) RADEON(2): 1024x768@60Hz
(II) RADEON(2): 1024x768@70Hz
(II) RADEON(2): 1024x768@75Hz
(II) RADEON(2): 1280x1024@75Hz
(II) RADEON(2): Manufacturer's mask: 0
(II) RADEON(2): Supported Future Video Modes:
(II) RADEON(2): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(2): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(2): Supported additional Video Mode:
(II) RADEON(2): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(2): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(2): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(2): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(2): Monitor name: CMC 19" AD
(II) RADEON(2): Serial No: 0
(II) RADEON(2): EDID (in hex):
(II) RADEON(2): 	00ffffffffffff000daf980101010101
(II) RADEON(2): 	050f010368261e782f40b5a259499724
(II) RADEON(2): 	125054bfef008180714f010101010101
(II) RADEON(2): 	010101010101302a009851002a403070
(II) RADEON(2): 	1300520e1100001e000000fd00384c1e
(II) RADEON(2): 	520e000a202020202020000000fc0043
(II) RADEON(2): 	4d43203139222041440a2020000000ff
(II) RADEON(2): 	00300a20202020202020202020200062
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(2): EDID vendor "CMO", prod id 408
(II) RADEON(2): Using hsync ranges from config file
(II) RADEON(2): Using vrefresh ranges from config file
(II) RADEON(2): Printing DDC gathered Modelines:
(II) RADEON(2): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(2): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(2): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(2): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(2): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(2): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(2): Output: DVI-1, Detected Monitor Type: 1
(II) RADEON(2): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(2): Manufacturer: CMO  Model: 198  Serial#: 16843009
(II) RADEON(2): Year: 2005  Week: 5
(II) RADEON(2): EDID Version: 1.3
(II) RADEON(2): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(2): Sync:  Separate
(II) RADEON(2): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(2): Gamma: 2.20
(II) RADEON(2): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(2): Default color space is primary color space
(II) RADEON(2): First detailed timing is preferred mode
(II) RADEON(2): GTF timings supported
(II) RADEON(2): redX: 0.634 redY: 0.348   greenX: 0.285 greenY: 0.590
(II) RADEON(2): blueX: 0.143 blueY: 0.073   whiteX: 0.313 whiteY: 0.329
(II) RADEON(2): Supported VESA Video Modes:
(II) RADEON(2): 720x400@70Hz
(II) RADEON(2): 640x480@60Hz
(II) RADEON(2): 640x480@67Hz
(II) RADEON(2): 640x480@72Hz
(II) RADEON(2): 640x480@75Hz
(II) RADEON(2): 800x600@56Hz
(II) RADEON(2): 800x600@60Hz
(II) RADEON(2): 800x600@72Hz
(II) RADEON(2): 800x600@75Hz
(II) RADEON(2): 832x624@75Hz
(II) RADEON(2): 1024x768@60Hz
(II) RADEON(2): 1024x768@70Hz
(II) RADEON(2): 1024x768@75Hz
(II) RADEON(2): 1280x1024@75Hz
(II) RADEON(2): Manufacturer's mask: 0
(II) RADEON(2): Supported Future Video Modes:
(II) RADEON(2): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(2): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(2): Supported additional Video Mode:
(II) RADEON(2): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(2): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(2): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(2): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(2): Monitor name: CMC 19" AD
(II) RADEON(2): Serial No: 0
(II) RADEON(2): EDID (in hex):
(II) RADEON(2): 	00ffffffffffff000daf980101010101
(II) RADEON(2): 	050f010368261e782f40b5a259499724
(II) RADEON(2): 	125054bfef008180714f010101010101
(II) RADEON(2): 	010101010101302a009851002a403070
(II) RADEON(2): 	1300520e1100001e000000fd00384c1e
(II) RADEON(2): 	520e000a202020202020000000fc0043
(II) RADEON(2): 	4d43203139222041440a2020000000ff
(II) RADEON(2): 	00300a20202020202020202020200062
in RADEONProbeOutputModes
(II) RADEON(2): EDID vendor "CMO", prod id 408
(II) RADEON(2): Output DVI-1 connected
(II) RADEON(2): Output DVI-1 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(2): Display dimensions: (380, 300) mm
(**) RADEON(2): DPI set to (85, 101)
(II) Reloading usr\lib/xorg/modules//libfb.so
(==) RADEON(2): Using gamma correction (1.0, 1.0, 1.0)
(II) Module "ramdac" already built-in
(==) RADEON(2): No acceleration support available on R600 yet.
(==) RADEON(2): Assuming overlay scaler buffer width is 1536
(II) RADEON(2): MM_TABLE: bb-c9-05-e8-c7-05-24-e3-0a-c4-e8-bb-04-b8
(II) RADEON(2): This card has MM_TABLE we do not recognize.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(2): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(2): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(3): MMIO registers at 0x00000000f5000000: size 64KB
(II) RADEON(3): PCI bus 2 card 0 func 0
(II) RADEON(3): Creating default Display subsection in Screen section
	"Screenb1" for depth/fbbpp 24/32
(**) RADEON(3): Depth 24, (--) framebuffer bpp 32
(II) RADEON(3): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(3): Default visual is TrueColor
(II) Reloading usr\lib/xorg/modules//libvgahw.so
(==) RADEON(3): RGB weight 888
(II) RADEON(3): Using 8 bits per RGB (8 bit DAC)
(II) Reloading usr\lib/xorg/modules//libint10.so
(II) RADEON(3): initializing int10
Requesting insufficient memory window!: start: 0xf4000000 end: 0xf5ffffff size 0x10000000
(EE) Cannot find empty range to map base to
(EE) RADEON(2): Cannot read V_BIOS (3)
(--) RADEON(3): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
(WW) RADEON(3): R600 support is mostly incomplete and very experimental
(--) RADEON(3): Linear framebuffer at 0x00000000e0000000
(II) RADEON(3): PCIE card detected
(II) RADEON(3): using shadow framebuffer
(II) Reloading usr\lib/xorg/modules//libshadow.so
Requesting insufficient memory window!: start: 0xf4000000 end: 0xf5ffffff size 0x10000000
(EE) Cannot find empty range to map base to
(WW) RADEON(3): Video BIOS not detected in PCI space!
(WW) RADEON(3): Attempting to read Video BIOS from legacy ISA space!
(II) RADEON(3): ATOM BIOS detected
(II) RADEON(3): Getting BIOS copy from legacy VBIOS location
(II) RADEON(3): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1787 SubsystemID: 0x2233
	IOBaseAddress: 0xa000
(II) RADEON(3): Framebuffer space used by Firmware (kb): 20
(II) RADEON(3): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(3): Framebuffer space used by Firmware (kb): 20
(II) RADEON(3): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(3): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(3): AtomBIOS VRAM scratch base: 0x1fffb000
(II) RADEON(3): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(3): Default Engine Clock: 600000
(II) RADEON(3): Default Memory Clock: 405000
(II) RADEON(3): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(3): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(3): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(3): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(3): Maximum Pixel Clock: 400000
(II) RADEON(3): Reference Clock: 27000
(WW) RADEON(3): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
Please use the radeon MergedFB option if you want Dual-head with DRI.
(II) RADEON(3): Generation 2 PCI interface, using max accessible memory
(II) RADEON(3): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(3): Mapped VideoRAM: 262144 kByte (64 bit DDR SDRAM)
(II) RADEON(3): Using 131072k of videoram for secondary head
(II) RADEON(3): Color tiling disabled
(II) RADEON(3): Max desktop size set to 2560x1200
(II) RADEON(3): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(3): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) RADEON(3): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 405.000000
(II) RADEON(3): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 000a 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 2113 19
src object id 2116 22
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[1] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 0002 02
src object id 210f 15
src object id 2115 21
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[0] EngineID: 1 I2CAddr: 0
record type 2
record type 4
(II) RADEON(3): Output None using monitor section Generic Monitor
(II) RADEON(3): Output DVI-1 has no monitor section
(II) RADEON(3): I2C bus "DVI-1" initialized.
(II) RADEON(3): Output DVI-0 has no monitor section
(II) RADEON(3): I2C bus "DVI-0" initialized.
(II) RADEON(3): Port0:
 Monitor   -- AUTO
 Connector -- SCART
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(3): Output: None, Detected Monitor Type: 0
CailReadATIRegister(7a04) = 1
CailReadATIRegister(7a5c) = 0
CailReadATIRegister(7a54) = 202002
CailReadATIRegister(7a58_) = 0
CailReadATIRegister(7a28_) = 70000
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a50) = 0
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a40) = 0
CailWriteATIRegister(7a40,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,1)
CailReadATIRegister(7a5c) = 0
CailWriteATIRegister(7a5c,70000)
CailReadATIRegister(7a54) = 202002
CailWriteATIRegister(7a54,202202)
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
(II) RADEON(3): Delay 5000 usec
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a40) = 0
CailWriteATIRegister(7a40,1e6)
(II) RADEON(3): Delay 200 usec
CailReadATIRegister(7a5c) = 70000
CailWriteATIRegister(7a5c,70100)
(II) RADEON(3): Delay 100 usec
CailReadATIRegister(7a60) = f
CailReadATIRegister(7a5c) = 70100
CailWriteATIRegister(7a5c,0)
CailReadATIRegister(7a54) = 202202
CailWriteATIRegister(7a54,202002)
CailReadATIRegister(7a58_) = 1
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a00) = 1
CailWriteATIRegister(7a00,1)
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a04) = 1
CailWriteATIRegister(7a04,1)
CailReadATIRegister(1724) = 20200
CailWriteATIRegister(1724,20000)
CailReadATIRegister(1724) = 20000
CailWriteATIRegister(1724,20200)
Dac detection success
DAC connect 00020200
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(3): Output: None, Detected Monitor Type: 0
CailReadATIRegister(7a04) = 1
CailReadATIRegister(7a5c) = 0
CailReadATIRegister(7a54) = 202002
CailReadATIRegister(7a58_) = 0
CailReadATIRegister(7a28_) = 70000
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a50) = 0
CailReadATIRegister(7a00) = 1
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a40) = 1e6
CailWriteATIRegister(7a40,0)
CailReadATIRegister(7a58_) = 0
CailWriteATIRegister(7a58,1)
CailReadATIRegister(7a5c) = 0
CailWriteATIRegister(7a5c,70000)
CailReadATIRegister(7a54) = 202002
CailWriteATIRegister(7a54,202202)
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
(II) RADEON(3): Delay 5000 usec
CailReadATIRegister(7a50) = 0
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a40) = 0
CailWriteATIRegister(7a40,1e6)
(II) RADEON(3): Delay 200 usec
CailReadATIRegister(7a5c) = 70000
CailWriteATIRegister(7a5c,70100)
(II) RADEON(3): Delay 100 usec
CailReadATIRegister(7a60) = f
CailReadATIRegister(7a5c) = 70100
CailWriteATIRegister(7a5c,0)
CailReadATIRegister(7a54) = 202202
CailWriteATIRegister(7a54,202002)
CailReadATIRegister(7a58_) = 1
CailWriteATIRegister(7a58,0)
CailReadATIRegister(7a28_) = 70000
CailWriteATIRegister(7a28,70000)
CailReadATIRegister(7a00) = 1
CailWriteATIRegister(7a00,1)
CailWriteATIRegister(7a50,0)
CailReadATIRegister(7a04) = 1
CailWriteATIRegister(7a04,1)
CailReadATIRegister(1724) = 20200
CailWriteATIRegister(1724,20000)
CailReadATIRegister(1724) = 20000
CailWriteATIRegister(1724,20200)
Dac detection success
DAC connect 00020200
in RADEONProbeOutputModes
(II) RADEON(3): Total number of valid Screen mode(s) added: 0
(II) RADEON(3): Output None connected
(II) RADEON(3): Output None using initial mode 1280x768
after xf86InitialConfiguration
(==) RADEON(3): DPI set to (96, 96)
(II) Reloading usr\lib/xorg/modules//libfb.so
(==) RADEON(3): Using gamma correction (1.0, 1.0, 1.0)
(II) Module "ramdac" already built-in
(==) RADEON(3): No acceleration support available on R600 yet.
(==) RADEON(3): Assuming overlay scaler buffer width is 1536
(II) RADEON(3): MM_TABLE: bb-c9-05-e8-c7-05-24-e3-0a-c4-e8-bb-04-b8
(II) RADEON(3): This card has MM_TABLE we do not recognize.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(3): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(3): MergedFB support has been removed and replaced with xrandr 1.2 support
```

---

### Post by bapoumba on 2008-07-07
I've added code tags to the two posts above. Please use them when you have a long set of code lines to add to a post. Otherwise, it is completely unreadable. Thanks.

Code tags are labeled with a # in the message tool box.
[More bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")

---

