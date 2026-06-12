---
title: "60Hz refresh rate issue Ubuntu 10.04. Solved but no GPU"
date: 2010-07-27
forum: Multimedia Software
---

### Post by wenus525 on 2010-07-27
I got integrated 4250 and CRT monitor. Refresh rate is a problem. Problem is in OpenSuse too. 

When I run first time computer with ubuntu there was no xorg.conf . Installing 10.6 drivers resolved this issue but 60hz problem still appeared.

I tried to make some modification in xorg.conf ....

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
Identifier "Monitor0"
HorizSync 31.5 - 96.0
VertRefresh 50.0 - 100.0
Option "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
Option "PreferredMode" "1600x1200_85"
Option "TargetRefresh" "85"
Option "Position" "0 0"
Option "Rotate" "normal"
Option "Disable" "false" 
Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
Modeline "1600x1200_85.00"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

If I change anything I loose refresh rate. I changed in driver section from fglrx to ati (loose 3d support gain resolution and  refresh rate)

---

### Post by wenus525 on 2010-07-28
up

---

### Post by wenus525 on 2010-07-29
I saw that xorg.log can help you solved my problem....


```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux piotr 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=e452371c-f1fd-4410-b3a7-eb37ec7409dc ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 29 13:18:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9715:1043:843e ATI Technologies Inc rev 0, Mem @ 0xf0000000/134217728, 0xfe8f0000/65536, 0xfe700000/1048576, I/O @ 0x0000b000/256
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
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
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
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
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
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
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
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
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
(II) Primary Device is: PCI 01@00:05:0
(II) [KMS] drm report modesetting isn't supported.
(II) RADEON(0): TOTO SAYS 00000000fe8f0000
(II) RADEON(0): MMIO registers at 0x00000000fe8f0000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon HD 4290" (ChipID = 0x9715)
(--) RADEON(0): Linear framebuffer at 0x00000000f0000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1002 SubsystemID: 0x1002
	IOBaseAddress: 0xb000
	Filename: 880P_DVI.bin
	BIOS Bootup Message: 
113-B43106-X11 RS880 DDR2 200e/500m                                         

(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 500000
(II) RADEON(0): Default Memory Clock: 667000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 14320
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card15
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card15
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): PLL parameters: rf=1432 rd=12 min=90000 max=120000; xclk=40000
(II) RADEON(0): Output VGA-0 using monitor section aticonfig-Monitor[0]-0
(**) RADEON(0): Option "PreferredMode" "1600x1200_85"
(**) RADEON(0): Option "Position" "0 0"
(**) RADEON(0): Option "Disable" "false"
(**) RADEON(0): Option "Rotate" "normal"
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e40
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP3: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e50
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:DDC control interface" registered at address 0x6E.
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
finished output detect: 1
finished all detect
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using mode "1600x1200_85.00" (hsync out of range)
(II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1024x768" (interlace mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1856x1392"x60.0  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.4 kHz)
(II) RADEON(0): Modeline "1792x1344"x60.0  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.7 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) RADEON(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x84.9  214.75  1680 1808 1984 2288  1050 1053 1059 1105 -hsync +vsync (93.9 kHz)
(II) RADEON(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x69.9  174.00  1680 1800 1976 2272  1050 1053 1059 1096 -hsync +vsync (76.6 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) RADEON(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "1280x1024_75.00"x75.0  138.54  1280 1368 1504 1728  1024 1025 1028 1069 -hsync +vsync (80.2 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): Panel infos found from DDC detailed: 1600x1200
(II) RADEON(0): Panel infos found from DDC VESA/EDID: 2048x1536
(II) RADEON(0): EDID vendor "IBM", prod id 6652
(II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1024x768" (interlace mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1600x1200"x85.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) RADEON(0): Modeline "2048x1536"x75.0  340.48  2048 2216 2440 2832  1536 1537 1540 1603 -hsync +vsync (120.2 kHz)
(II) RADEON(0): Modeline "2048x1536"x75.0  340.48  2048 2216 2440 2832  1536 1537 1540 1603 -hsync +vsync (120.2 kHz)
(II) RADEON(0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz)
(II) RADEON(0): Modeline "1920x1440"x85.0  341.35  1920 2072 2288 2656  1440 1441 1444 1512 -hsync +vsync (128.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x75.0  297.00  1920 2064 2288 2640  1440 1441 1444 1500 -hsync +vsync (112.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1856x1392"x75.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
(II) RADEON(0): Modeline "1856x1392"x60.0  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.4 kHz)
(II) RADEON(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
(II) RADEON(0): Modeline "1792x1344"x60.0  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.7 kHz)
(II) RADEON(0): Modeline "1600x1200"x85.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) RADEON(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x84.9  214.75  1680 1808 1984 2288  1050 1053 1059 1105 -hsync +vsync (93.9 kHz)
(II) RADEON(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x69.9  174.00  1680 1800 1976 2272  1050 1053 1059 1096 -hsync +vsync (76.6 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) RADEON(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using user preference for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1600x1200
(II) RADEON(0): Output DVI-0 using initial mode 1600x1200
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): RADEONScreenInit f0000000 0 0
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Output DIG0 transmitter setup success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (2048,8191)
(II) RADEON(0): Reserved area from (0,2048) to (2048,2050)
(II) RADEON(0): Largest offscreen area available: 2048 x 6141
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x01004000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x01008000
(II) RADEON(0): Largest offscreen area available: 2048 x 6137
(II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output CRT1 disable success
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1600x1200 - 2160 1250 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Picked PLL 0
before 20250
after 20250
best_freq: 202628
best_feedback_div: 283
best_frac_feedback_div: 0
best_ref_div: 4
best_post_div: 5
(II) RADEON(0): crtc(0) Clock: mode 202500, PLL 2026280
(II) RADEON(0): crtc(0) PLL  : refdiv 4, fbdiv 0x11B(283), fracfbdiv 0, pdiv 5
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Lock CRTC 0 success
Output CRT1 disable success
Output DIG0 transmitter setup success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Mode 1600x1200 - 2160 1250 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Picked PLL 1
before 22950
after 22950
best_freq: 229836
best_feedback_div: 321
best_frac_feedback_div: 0
best_ref_div: 4
best_post_div: 5
(II) RADEON(0): crtc(1) Clock: mode 229500, PLL 2298360
(II) RADEON(0): crtc(1) PLL  : refdiv 4, fbdiv 0x141(321), fracfbdiv 0, pdiv 5
Set CRTC 1 PLL success
Set CRTC Timing success
Set CRTC 1 Overscan success
Not using RMX
scaler 1 setup success
Set CRTC 1 Source success
crtc 1 YUV disable setup success
Output DIG0 transmitter setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Unlock CRTC 0 success
Output CRT1 enable success
Output DIG0 transmitter setup success
Enable CRTC 1 success
Enable CRTC memreq 1 success
Unblank CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Lock CRTC 0 success
Output CRT1 disable success
Output DIG0 transmitter setup success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Mode 1600x1200 - 2160 1250 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Picked PLL 1
before 22950
after 22950
best_freq: 229836
best_feedback_div: 321
best_frac_feedback_div: 0
best_ref_div: 4
best_post_div: 5
(II) RADEON(0): crtc(1) Clock: mode 229500, PLL 2298360
(II) RADEON(0): crtc(1) PLL  : refdiv 4, fbdiv 0x141(321), fracfbdiv 0, pdiv 5
Set CRTC 1 PLL success
Set CRTC Timing success
Set CRTC 1 Overscan success
Not using RMX
scaler 1 setup success
Set CRTC 1 Source success
crtc 1 YUV disable setup success
Output DIG0 transmitter setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Unlock CRTC 0 success
Output CRT1 enable success
Output DIG0 transmitter setup success
Enable CRTC 1 success
Enable CRTC memreq 1 success
Unblank CRTC 1 success
(WW) RADEON(0): Option "VendorName" is not used
(WW) RADEON(0): Option "ModelName" is not used
(WW) RADEON(0): Option "PreferredMode" is not used
(WW) RADEON(0): Option "TargetRefresh" is not used
(WW) RADEON(0): Option "Position" is not used
(WW) RADEON(0): Option "Rotate" is not used
(WW) RADEON(0): Option "Disable" is not used
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) GLX error: Can not get required symbols.
(II) RADEON(0): Setting screen physical size to 423 x 317
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pl"
(II) XKB: reuse xkmfile /var/lib/xkb/server-61818C6B46DD4F01AE1F641F27B555591612208F.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pl"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pl"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): EDID vendor "IBM", prod id 6652
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): EDID vendor "IBM", prod id 6652
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): EDID vendor "IBM", prod id 6652
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Output CRT1 disable success
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Output DIG0 transmitter setup success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Mode 1280x1024 - 1688 1066 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Picked PLL 1
before 10800
after 10800
best_freq: 108050
best_feedback_div: 166
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 11
(II) RADEON(0): crtc(1) Clock: mode 108000, PLL 1080500
(II) RADEON(0): crtc(1) PLL  : refdiv 2, fbdiv 0xA6(166), fracfbdiv 0, pdiv 11
Set CRTC 1 PLL success
Set CRTC Timing success
Set CRTC 1 Overscan success
Not using RMX
scaler 1 setup success
Set CRTC 1 Source success
crtc 1 YUV disable setup success
Output DIG0 transmitter setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Enable CRTC 1 success
Enable CRTC memreq 1 success
Unblank CRTC 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Lock CRTC 1 success
Output DIG0 transmitter setup success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1280x1024 - 1728 1072 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00c700c0 0x00c700c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Picked PLL 0
before 15750
after 15750
best_freq: 157520
best_feedback_div: 154
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 7
(II) RADEON(0): crtc(0) Clock: mode 157500, PLL 1575200
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x9A(154), fracfbdiv 0, pdiv 7
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Enable CRTC 1 success
Enable CRTC memreq 1 success
Unblank CRTC 1 success
Unlock CRTC 1 success
Output DIG0 transmitter setup success
Output CRT1 enable success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): EDID vendor "IBM", prod id 6652
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 19fc  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 38
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 229.5 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 170 Hz, H min: 30 H max: 130 kHz, PixClock max 340 MHz
(II) RADEON(0): Monitor name: IBM 6652 P275
(II) RADEON(0): Serial No: 23Z5960
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dfc1901010101
(II) RADEON(0): 	260d01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484cefcf00e14f3159455961598199
(II) RADEON(0): 	a94fa959d14fa659403062b0324040c0
(II) RADEON(0): 	130084231100001e000000fd0030aa1e
(II) RADEON(0): 	8222000a202020202020000000fc0049
(II) RADEON(0): 	424d20363635322050323735000000ff
(II) RADEON(0): 	0032335a353936300a20202020200061
(II) RADEON(0): EDID vendor "IBM", prod id 6652
```

---

