---
title: "Lost 3d acceleration after dist-upgrade (ATI Radeon X1950 GT)"
date: 2011-05-29
forum: Multimedia Software
---

### Post by SaToNiO on 2011-05-29
I'm using now ubuntu 11.04 (i was using ubuntu 10.04 and did two dist-upgrades in a row). It was working fine in 10.04 but now...

I'm using xserver-xorg-video-radeon driver, but it seems not to be working properly because it's using software rasterizer.

satonio@satonio-desktop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 


Here is my Xorg.0.log:
```
[    32.482] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    32.489] X Protocol Version 11, Revision 0
[    32.489] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    32.489] Current Operating System: Linux satonio-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    32.489] Kernel command line: root=UUID=aff10773-a118-41b0-8082-00e5236acfe9 ro quiet splash 
[    32.489] Build Date: 19 April 2011  03:40:45PM
[    32.489] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    32.489] Current version of pixman: 0.20.2
[    32.489] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    32.489] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.489] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May 29 15:16:39 2011
[    32.490] (==) Using config file: "/etc/X11/xorg.conf"
[    32.490] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.490] (==) No Layout section.  Using the first Screen section.
[    32.490] (==) No screen section available. Using defaults.
[    32.490] (**) |-->Screen "Default Screen Section" (0)
[    32.490] (**) |   |-->Monitor "<default monitor>"
[    32.490] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    32.490] (==) Automatically adding devices
[    32.490] (==) Automatically enabling devices
[    32.490] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.490] 	Entry deleted from font path.
[    32.490] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    32.490] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.490] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    32.490] (II) Loader magic: 0x7e0280
[    32.490] (II) Module ABI versions:
[    32.490] 	X.Org ANSI C Emulation: 0.4
[    32.490] 	X.Org Video Driver: 10.0
[    32.490] 	X.Org XInput driver : 12.3
[    32.490] 	X.Org Server Extension : 5.0
[    32.491] (--) PCI:*(0:2:0:0) 1002:7288:0000:0000 rev 154, Mem @ 0xd0000000/268435456, 0xfbbe0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    32.491] (--) PCI: (0:2:0:1) 1002:72a8:0000:0001 rev 154, Mem @ 0xfbbf0000/65536
[    32.492] (II) Open ACPI successful (/var/run/acpid.socket)
[    32.492] (II) LoadModule: "extmod"
[    32.507] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    32.532] (II) Module extmod: vendor="X.Org Foundation"
[    32.532] 	compiled for 1.10.1, module version = 1.0.0
[    32.532] 	Module class: X.Org Server Extension
[    32.532] 	ABI class: X.Org Server Extension, version 5.0
[    32.532] (II) Loading extension MIT-SCREEN-SAVER
[    32.532] (II) Loading extension XFree86-VidModeExtension
[    32.532] (II) Loading extension XFree86-DGA
[    32.532] (II) Loading extension DPMS
[    32.532] (II) Loading extension XVideo
[    32.532] (II) Loading extension XVideo-MotionCompensation
[    32.532] (II) Loading extension X-Resource
[    32.532] (II) LoadModule: "dbe"
[    32.532] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    32.532] (II) Module dbe: vendor="X.Org Foundation"
[    32.532] 	compiled for 1.10.1, module version = 1.0.0
[    32.532] 	Module class: X.Org Server Extension
[    32.532] 	ABI class: X.Org Server Extension, version 5.0
[    32.532] (II) Loading extension DOUBLE-BUFFER
[    32.532] (II) LoadModule: "glx"
[    32.533] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.533] (II) Module glx: vendor="X.Org Foundation"
[    32.533] 	compiled for 1.10.1, module version = 1.0.0
[    32.533] 	ABI class: X.Org Server Extension, version 5.0
[    32.533] (==) AIGLX enabled
[    32.533] (II) Loading extension GLX
[    32.533] (II) LoadModule: "record"
[    32.533] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.533] (II) Module record: vendor="X.Org Foundation"
[    32.533] 	compiled for 1.10.1, module version = 1.13.0
[    32.533] 	Module class: X.Org Server Extension
[    32.533] 	ABI class: X.Org Server Extension, version 5.0
[    32.533] (II) Loading extension RECORD
[    32.533] (II) LoadModule: "dri"
[    32.533] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.533] (II) Module dri: vendor="X.Org Foundation"
[    32.533] 	compiled for 1.10.1, module version = 1.0.0
[    32.533] 	ABI class: X.Org Server Extension, version 5.0
[    32.533] (II) Loading extension XFree86-DRI
[    32.533] (II) LoadModule: "dri2"
[    32.533] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.534] (II) Module dri2: vendor="X.Org Foundation"
[    32.534] 	compiled for 1.10.1, module version = 1.2.0
[    32.534] 	ABI class: X.Org Server Extension, version 5.0
[    32.534] (II) Loading extension DRI2
[    32.534] (==) Matched fglrx as autoconfigured driver 0
[    32.534] (==) Matched ati as autoconfigured driver 1
[    32.534] (==) Matched vesa as autoconfigured driver 2
[    32.534] (==) Matched fbdev as autoconfigured driver 3
[    32.534] (==) Assigned the driver to the xf86ConfigLayout
[    32.534] (II) LoadModule: "fglrx"
[    32.543] (WW) Warning, couldn't open module fglrx
[    32.543] (II) UnloadModule: "fglrx"
[    32.543] (II) Unloading fglrx
[    32.543] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    32.543] (II) LoadModule: "ati"
[    32.543] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    32.543] (II) Module ati: vendor="X.Org Foundation"
[    32.543] 	compiled for 1.10.0, module version = 6.14.0
[    32.543] 	Module class: X.Org Video Driver
[    32.543] 	ABI class: X.Org Video Driver, version 10.0
[    32.543] (II) LoadModule: "radeon"
[    32.543] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.544] (II) Module radeon: vendor="X.Org Foundation"
[    32.544] 	compiled for 1.10.0, module version = 6.14.0
[    32.544] 	Module class: X.Org Video Driver
[    32.544] 	ABI class: X.Org Video Driver, version 10.0
[    32.544] (II) LoadModule: "vesa"
[    32.544] (WW) Warning, couldn't open module vesa
[    32.544] (II) UnloadModule: "vesa"
[    32.544] (II) Unloading vesa
[    32.544] (EE) Failed to load module "vesa" (module does not exist, 0)
[    32.544] (II) LoadModule: "fbdev"
[    32.544] (WW) Warning, couldn't open module fbdev
[    32.544] (II) UnloadModule: "fbdev"
[    32.544] (II) Unloading fbdev
[    32.544] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    32.544] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
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
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    32.552] (++) using VT number 7

[    32.552] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.552] (II) [KMS] Kernel modesetting enabled.
[    32.552] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    32.552] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    32.552] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    32.552] (==) RADEON(0): Default visual is TrueColor
[    32.552] (==) RADEON(0): RGB weight 888
[    32.552] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    32.552] (--) RADEON(0): Chipset: "ATI Radeon X1950 GT" (ChipID = 0x7288)
[    32.552] (II) RADEON(0): PCIE card detected
[    32.552] drmOpenDevice: node name is /dev/dri/card0
[    32.552] drmOpenDevice: open result is 9, (OK)
[    32.552] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    32.552] drmOpenDevice: node name is /dev/dri/card0
[    32.552] drmOpenDevice: open result is 9, (OK)
[    32.552] drmOpenByBusid: drmOpenMinor returns 9
[    32.552] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    32.552] (II) RADEON(0): KMS Color Tiling: enabled
[    32.552] (II) RADEON(0): KMS Pageflipping: enabled
[    32.552] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    32.608] (II) RADEON(0): Output DVI-0 has no monitor section
[    32.640] (II) RADEON(0): Output S-video has no monitor section
[    32.680] (II) RADEON(0): Output DVI-1 has no monitor section
[    32.735] (II) RADEON(0): EDID for output DVI-0
[    32.735] (II) RADEON(0): Manufacturer: HKC  Model: 988  Serial#: 1
[    32.735] (II) RADEON(0): Year: 2007  Week: 3
[    32.735] (II) RADEON(0): EDID Version: 1.3
[    32.735] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    32.735] (II) RADEON(0): Sync:  Separate
[    32.735] (II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    32.735] (II) RADEON(0): Gamma: 2.20
[    32.735] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    32.735] (II) RADEON(0): First detailed timing is preferred mode
[    32.735] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    32.735] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    32.735] (II) RADEON(0): Supported established timings:
[    32.735] (II) RADEON(0): 720x400@70Hz
[    32.735] (II) RADEON(0): 640x480@60Hz
[    32.735] (II) RADEON(0): 640x480@72Hz
[    32.735] (II) RADEON(0): 640x480@75Hz
[    32.735] (II) RADEON(0): 800x600@56Hz
[    32.735] (II) RADEON(0): 800x600@60Hz
[    32.735] (II) RADEON(0): 800x600@72Hz
[    32.735] (II) RADEON(0): 800x600@75Hz
[    32.735] (II) RADEON(0): 1024x768@60Hz
[    32.735] (II) RADEON(0): 1024x768@70Hz
[    32.735] (II) RADEON(0): 1024x768@75Hz
[    32.735] (II) RADEON(0): 1280x1024@75Hz
[    32.735] (II) RADEON(0): Manufacturer's mask: 0
[    32.735] (II) RADEON(0): Supported standard timings:
[    32.735] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    32.735] (II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    32.735] (II) RADEON(0): Supported detailed timing:
[    32.735] (II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
[    32.735] (II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    32.735] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    32.735] (II) RADEON(0): Monitor name: HKC988
[    32.735] (II) RADEON(0): Ranges: V min: 60 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 145 MHz
[    32.735] (II) RADEON(0): Serial No: 200704121253
[    32.735] (II) RADEON(0): EDID (in hex):
[    32.735] (II) RADEON(0): 	00ffffffffffff002163880901000000
[    32.735] (II) RADEON(0): 	0311010308291a78eade95a3544c9926
[    32.735] (II) RADEON(0): 	0f5054afcf0081809500010101010101
[    32.735] (II) RADEON(0): 	0101010101019a29a0d0518422305098
[    32.735] (II) RADEON(0): 	36009a001100001c000000fc00484b43
[    32.735] (II) RADEON(0): 	3938380a202020202020000000fd003c
[    32.735] (II) RADEON(0): 	4b1e500e000a202020202020000000ff
[    32.735] (II) RADEON(0): 	003230303730343132313235330a0031
[    32.735] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    32.735] (II) RADEON(0): Using EDID range info for horizontal sync
[    32.735] (II) RADEON(0): Using EDID range info for vertical refresh
[    32.735] (II) RADEON(0): Printing DDC gathered Modelines:
[    32.735] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    32.735] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    32.735] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    32.735] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    32.735] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    32.735] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    32.735] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    32.735] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    32.735] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    32.735] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    32.736] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.736] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    32.736] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    32.736] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    32.736] (II) RADEON(0): Printing probed modes for output DVI-0
[    32.736] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    32.736] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    32.736] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    32.736] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    32.736] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    32.736] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.736] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    32.736] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    32.736] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    32.736] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    32.736] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    32.736] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    32.736] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    32.736] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    32.770] (II) RADEON(0): EDID for output S-video
[    32.810] (II) RADEON(0): EDID for output DVI-1
[    32.810] (II) RADEON(0): Output DVI-0 connected
[    32.810] (II) RADEON(0): Output S-video disconnected
[    32.810] (II) RADEON(0): Output DVI-1 disconnected
[    32.810] (II) RADEON(0): Using exact sizes for initial modes
[    32.810] (II) RADEON(0): Output DVI-0 using initial mode 1440x900
[    32.810] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    32.810] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fab2000
[    32.810] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    32.810] (**) RADEON(0): Display dimensions: (410, 260) mm
[    32.810] (**) RADEON(0): DPI set to (89, 87)
[    32.810] (II) Loading sub module "fb"
[    32.810] (II) LoadModule: "fb"
[    32.810] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.810] (II) Module fb: vendor="X.Org Foundation"
[    32.810] 	compiled for 1.10.1, module version = 1.0.0
[    32.810] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    32.810] (II) Loading sub module "ramdac"
[    32.810] (II) LoadModule: "ramdac"
[    32.810] (II) Module "ramdac" already built-in
[    32.810] (II) RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
[    32.810] (II) Loading sub module "shadow"
[    32.810] (II) LoadModule: "shadow"
[    32.811] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    32.811] (II) Module shadow: vendor="X.Org Foundation"
[    32.811] 	compiled for 1.10.1, module version = 1.1.0
[    32.811] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    32.811] (--) Depth 24 pixmap format is 32 bpp
[    32.811] (II) RADEON(0): Front buffer size: 5244K
[    32.811] (II) RADEON(0): VRAM usage limit set to 226321K
[    32.811] (==) RADEON(0): Backing store disabled
[    32.811] (WW) RADEON(0): Direct rendering disabled
[    32.811] (II) RADEON(0): Acceleration disabled
[    32.811] (==) RADEON(0): DPMS enabled
[    32.811] (==) RADEON(0): Silken mouse enabled
[    32.811] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    32.811] (--) RandR disabled
[    32.811] (II) Initializing built-in extension Generic Event Extension
[    32.811] (II) Initializing built-in extension SHAPE
[    32.811] (II) Initializing built-in extension MIT-SHM
[    32.811] (II) Initializing built-in extension XInputExtension
[    32.811] (II) Initializing built-in extension XTEST
[    32.811] (II) Initializing built-in extension BIG-REQUESTS
[    32.811] (II) Initializing built-in extension SYNC
[    32.811] (II) Initializing built-in extension XKEYBOARD
[    32.811] (II) Initializing built-in extension XC-MISC
[    32.811] (II) Initializing built-in extension SECURITY
[    32.811] (II) Initializing built-in extension XINERAMA
[    32.811] (II) Initializing built-in extension XFIXES
[    32.811] (II) Initializing built-in extension RENDER
[    32.811] (II) Initializing built-in extension RANDR
[    32.811] (II) Initializing built-in extension COMPOSITE
[    32.811] (II) Initializing built-in extension DAMAGE
[    32.811] (II) Initializing built-in extension GESTURE
[    32.818] (II) AIGLX: Screen 0 is not DRI2 capable
[    32.818] (II) AIGLX: Screen 0 is not DRI capable
[    32.818] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    32.876] (II) AIGLX: Loaded and initialized swrast
[    32.876] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    32.877] (II) RADEON(0): Setting screen physical size to 381 x 238
[    32.951] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.002] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    33.003] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.003] (II) LoadModule: "evdev"
[    33.003] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.003] (II) Module evdev: vendor="X.Org Foundation"
[    33.003] 	compiled for 1.10.0.902, module version = 2.6.0
[    33.003] 	Module class: X.Org XInput Driver
[    33.003] 	ABI class: X.Org XInput driver, version 12.3
[    33.003] (II) Using input driver 'evdev' for 'Power Button'
[    33.003] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.003] (**) Power Button: always reports core events
[    33.003] (**) Power Button: Device: "/dev/input/event2"
[    33.003] (--) Power Button: Found keys
[    33.003] (II) Power Button: Configuring as keyboard
[    33.003] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    33.003] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.003] (**) Option "xkb_rules" "evdev"
[    33.003] (**) Option "xkb_model" "pc105"
[    33.004] (**) Option "xkb_layout" "es"
[    33.005] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    33.041] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.041] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.041] (II) Using input driver 'evdev' for 'Power Button'
[    33.041] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.041] (**) Power Button: always reports core events
[    33.041] (**) Power Button: Device: "/dev/input/event1"
[    33.050] (--) Power Button: Found keys
[    33.050] (II) Power Button: Configuring as keyboard
[    33.050] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    33.050] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.050] (**) Option "xkb_rules" "evdev"
[    33.050] (**) Option "xkb_model" "pc105"
[    33.050] (**) Option "xkb_layout" "es"
[    33.050] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    33.050] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.050] (II) Using input driver 'evdev' for 'Sleep Button'
[    33.050] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.050] (**) Sleep Button: always reports core events
[    33.050] (**) Sleep Button: Device: "/dev/input/event0"
[    33.050] (--) Sleep Button: Found keys
[    33.050] (II) Sleep Button: Configuring as keyboard
[    33.050] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    33.050] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    33.050] (**) Option "xkb_rules" "evdev"
[    33.050] (**) Option "xkb_model" "pc105"
[    33.050] (**) Option "xkb_layout" "es"
[    33.056] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[    33.056] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    33.056] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    33.056] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.056] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    33.056] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[    33.060] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    33.060] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    33.060] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    33.060] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    33.060] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    33.060] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    33.060] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    33.060] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.060] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input4/event4"
[    33.060] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    33.060] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    33.060] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    33.060] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    33.060] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    33.060] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    33.060] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    33.060] (II) No input driver/identifier specified (ignoring)
[    33.061] (II) config/udev: Adding input device GreenAsia Inc.    USB Joystick      (/dev/input/event5)
[    33.061] (II) No input driver/identifier specified (ignoring)
[    33.061] (II) config/udev: Adding input device GreenAsia Inc.    USB Joystick      (/dev/input/js0)
[    33.061] (II) No input driver/identifier specified (ignoring)
[    33.063] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    33.063] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.063] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.063] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.063] (**) AT Translated Set 2 keyboard: always reports core events
[    33.063] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    33.063] (--) AT Translated Set 2 keyboard: Found keys
[    33.063] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    33.063] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    33.064] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    33.064] (**) Option "xkb_rules" "evdev"
[    33.064] (**) Option "xkb_model" "pc105"
[    33.064] (**) Option "xkb_layout" "es"
[    34.352] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    34.352] (II) RADEON(0): Using hsync ranges from config file
[    34.352] (II) RADEON(0): Using vrefresh ranges from config file
[    34.352] (II) RADEON(0): Printing DDC gathered Modelines:
[    34.352] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.352] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.352] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.352] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.352] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.352] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.352] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.352] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.352] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.352] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.352] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.352] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.352] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.352] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.491] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    34.491] (II) RADEON(0): Using hsync ranges from config file
[    34.491] (II) RADEON(0): Using vrefresh ranges from config file
[    34.492] (II) RADEON(0): Printing DDC gathered Modelines:
[    34.492] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.492] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.492] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.492] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.492] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.492] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.492] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.492] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.492] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.492] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.492] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.492] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.492] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.492] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.632] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    34.632] (II) RADEON(0): Using hsync ranges from config file
[    34.632] (II) RADEON(0): Using vrefresh ranges from config file
[    34.632] (II) RADEON(0): Printing DDC gathered Modelines:
[    34.632] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.632] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.632] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.632] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.632] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.632] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.632] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.632] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.632] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.632] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.632] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.632] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.632] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.632] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.765] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    34.765] (II) RADEON(0): Using hsync ranges from config file
[    34.765] (II) RADEON(0): Using vrefresh ranges from config file
[    34.765] (II) RADEON(0): Printing DDC gathered Modelines:
[    34.765] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.765] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.765] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.765] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.765] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.766] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.766] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.766] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.766] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.766] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.766] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.766] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.766] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.766] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    36.397] (II) config/udev: Adding input device i2c IR (HVR 1110) (/dev/input/event6)
[    36.483] (**) i2c IR (HVR 1110): Applying InputClass "evdev keyboard catchall"
[    36.483] (II) Using input driver 'evdev' for 'i2c IR (HVR 1110)'
[    36.483] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.483] (**) i2c IR (HVR 1110): always reports core events
[    36.483] (**) i2c IR (HVR 1110): Device: "/dev/input/event6"
[    36.531] (--) i2c IR (HVR 1110): Found keys
[    36.531] (II) i2c IR (HVR 1110): Configuring as keyboard
[    36.531] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input6/event6"
[    36.531] (II) XINPUT: Adding extended input device "i2c IR (HVR 1110)" (type: KEYBOARD)
[    36.531] (**) Option "xkb_rules" "evdev"
[    36.531] (**) Option "xkb_model" "pc105"
[    36.531] (**) Option "xkb_layout" "es"
[    45.890] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    45.890] (II) RADEON(0): Using hsync ranges from config file
[    45.890] (II) RADEON(0): Using vrefresh ranges from config file
[    45.891] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.891] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    45.891] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    45.891] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    45.891] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    45.891] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    45.891] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    45.891] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    45.891] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    45.891] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    45.891] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    45.891] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.891] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    45.891] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    45.891] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    46.026] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    46.026] (II) RADEON(0): Using hsync ranges from config file
[    46.026] (II) RADEON(0): Using vrefresh ranges from config file
[    46.026] (II) RADEON(0): Printing DDC gathered Modelines:
[    46.026] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    46.026] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    46.026] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    46.026] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    46.026] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    46.026] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    46.026] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    46.026] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    46.026] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    46.026] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    46.026] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    46.026] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    46.026] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    46.026] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    46.156] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    46.157] (II) RADEON(0): Using hsync ranges from config file
[    46.157] (II) RADEON(0): Using vrefresh ranges from config file
[    46.157] (II) RADEON(0): Printing DDC gathered Modelines:
[    46.157] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    46.157] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    46.157] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    46.157] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    46.157] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    46.157] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    46.157] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    46.157] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    46.157] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    46.157] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    46.157] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    46.157] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    46.157] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    46.157] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    46.286] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    46.286] (II) RADEON(0): Using hsync ranges from config file
[    46.286] (II) RADEON(0): Using vrefresh ranges from config file
[    46.286] (II) RADEON(0): Printing DDC gathered Modelines:
[    46.286] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    46.286] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    46.286] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    46.286] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    46.286] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    46.286] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    46.286] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    46.286] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    46.286] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    46.286] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    46.286] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    46.286] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    46.286] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    46.286] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    52.341] (II) RADEON(0): EDID vendor "HKC", prod id 2440
[    52.341] (II) RADEON(0): Using hsync ranges from config file
[    52.341] (II) RADEON(0): Using vrefresh ranges from config file
[    52.341] (II) RADEON(0): Printing DDC gathered Modelines:
[    52.341] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    52.341] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    52.341] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    52.341] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    52.341] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    52.341] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    52.341] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    52.341] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    52.341] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    52.341] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    52.341] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    52.341] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    52.341] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    52.341] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
```

Any ideas about what could be wrong?

---

