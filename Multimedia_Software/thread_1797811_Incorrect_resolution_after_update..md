---
title: "Incorrect resolution after update."
date: 2011-07-05
forum: Multimedia Software
---

### Post by grindboy on 2011-07-05
Hey Guys,

I recently ran the update manager on my Ubuntu 11.04 box then shutdown and went to bed. When I booted the pc back up the next day my resolution is stuck at 1024x768 when I normally run at 1366x768.

I'm using the default open source drivers since the AMD ones are useless with my hardware (specs in the signature)

I've tried changing the resolution through the "monitors" GUI and directly through xrandr.

xrandr output:
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
```

I have no xorg.conf but I've seen the xorg.0.log asked for in other threads so I'll provide that as well:
```
[    17.412] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    17.412] X Protocol Version 11, Revision 0
[    17.412] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    17.412] Current Operating System: Linux michael-desktop 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    17.412] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=2928d2b2-e5f7-4c87-a391-263d9986f500 ro quiet splash vt.handoff=7
[    17.412] Build Date: 21 May 2011  11:38:35AM
[    17.412] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    17.412] Current version of pixman: 0.20.2
[    17.412] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.412] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.413] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  5 16:42:18 2011
[    17.425] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.426] (==) No Layout section.  Using the first Screen section.
[    17.426] (==) No screen section available. Using defaults.
[    17.426] (**) |-->Screen "Default Screen Section" (0)
[    17.426] (**) |   |-->Monitor "<default monitor>"
[    17.426] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.426] (==) Automatically adding devices
[    17.426] (==) Automatically enabling devices
[    17.426] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.426] 	Entry deleted from font path.
[    17.426] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.426] 	Entry deleted from font path.
[    17.426] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.426] 	Entry deleted from font path.
[    17.426] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.426] 	Entry deleted from font path.
[    17.426] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.426] 	Entry deleted from font path.
[    17.426] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.426] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.426] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.426] (II) Loader magic: 0x81ffde0
[    17.426] (II) Module ABI versions:
[    17.426] 	X.Org ANSI C Emulation: 0.4
[    17.426] 	X.Org Video Driver: 10.0
[    17.426] 	X.Org XInput driver : 12.3
[    17.426] 	X.Org Server Extension : 5.0
[    17.426] (--) PCI:*(0:2:0:0) 1002:689e:174b:e177 rev 0, Mem @ 0xd0000000/268435456, 0xfddc0000/131072, I/O @ 0x0000ac00/256, BIOS @ 0x????????/131072
[    17.426] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    17.426] (II) LoadModule: "extmod"
[    17.440] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.440] (II) Module extmod: vendor="X.Org Foundation"
[    17.440] 	compiled for 1.10.1, module version = 1.0.0
[    17.440] 	Module class: X.Org Server Extension
[    17.440] 	ABI class: X.Org Server Extension, version 5.0
[    17.440] (II) Loading extension MIT-SCREEN-SAVER
[    17.440] (II) Loading extension XFree86-VidModeExtension
[    17.440] (II) Loading extension XFree86-DGA
[    17.440] (II) Loading extension DPMS
[    17.440] (II) Loading extension XVideo
[    17.440] (II) Loading extension XVideo-MotionCompensation
[    17.440] (II) Loading extension X-Resource
[    17.440] (II) LoadModule: "dbe"
[    17.440] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.440] (II) Module dbe: vendor="X.Org Foundation"
[    17.440] 	compiled for 1.10.1, module version = 1.0.0
[    17.440] 	Module class: X.Org Server Extension
[    17.440] 	ABI class: X.Org Server Extension, version 5.0
[    17.440] (II) Loading extension DOUBLE-BUFFER
[    17.440] (II) LoadModule: "glx"
[    17.440] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.440] (II) Module glx: vendor="X.Org Foundation"
[    17.440] 	compiled for 1.10.1, module version = 1.0.0
[    17.440] 	ABI class: X.Org Server Extension, version 5.0
[    17.440] (==) AIGLX enabled
[    17.440] (II) Loading extension GLX
[    17.440] (II) LoadModule: "record"
[    17.441] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.441] (II) Module record: vendor="X.Org Foundation"
[    17.441] 	compiled for 1.10.1, module version = 1.13.0
[    17.441] 	Module class: X.Org Server Extension
[    17.441] 	ABI class: X.Org Server Extension, version 5.0
[    17.441] (II) Loading extension RECORD
[    17.441] (II) LoadModule: "dri"
[    17.441] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.441] (II) Module dri: vendor="X.Org Foundation"
[    17.441] 	compiled for 1.10.1, module version = 1.0.0
[    17.441] 	ABI class: X.Org Server Extension, version 5.0
[    17.441] (II) Loading extension XFree86-DRI
[    17.441] (II) LoadModule: "dri2"
[    17.441] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.441] (II) Module dri2: vendor="X.Org Foundation"
[    17.441] 	compiled for 1.10.1, module version = 1.2.0
[    17.441] 	ABI class: X.Org Server Extension, version 5.0
[    17.441] (II) Loading extension DRI2
[    17.441] (==) Matched fglrx as autoconfigured driver 0
[    17.441] (==) Matched ati as autoconfigured driver 1
[    17.441] (==) Matched vesa as autoconfigured driver 2
[    17.441] (==) Matched fbdev as autoconfigured driver 3
[    17.441] (==) Assigned the driver to the xf86ConfigLayout
[    17.441] (II) LoadModule: "fglrx"
[    17.448] (WW) Warning, couldn't open module fglrx
[    17.448] (II) UnloadModule: "fglrx"
[    17.448] (II) Unloading fglrx
[    17.448] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.448] (II) LoadModule: "ati"
[    17.448] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.448] (II) Module ati: vendor="X.Org Foundation"
[    17.448] 	compiled for 1.10.0, module version = 6.14.0
[    17.448] 	Module class: X.Org Video Driver
[    17.448] 	ABI class: X.Org Video Driver, version 10.0
[    17.448] (II) LoadModule: "radeon"
[    17.448] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.448] (II) Module radeon: vendor="X.Org Foundation"
[    17.448] 	compiled for 1.10.0, module version = 6.14.0
[    17.448] 	Module class: X.Org Video Driver
[    17.448] 	ABI class: X.Org Video Driver, version 10.0
[    17.448] (II) LoadModule: "vesa"
[    17.449] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.449] (II) Module vesa: vendor="X.Org Foundation"
[    17.449] 	compiled for 1.10.0, module version = 2.3.0
[    17.449] 	Module class: X.Org Video Driver
[    17.449] 	ABI class: X.Org Video Driver, version 10.0
[    17.449] (II) LoadModule: "fbdev"
[    17.449] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.449] (II) Module fbdev: vendor="X.Org Foundation"
[    17.449] 	compiled for 1.10.0, module version = 0.4.2
[    17.449] 	ABI class: X.Org Video Driver, version 10.0
[    17.449] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    17.452] (II) VESA: driver for VESA chipsets: vesa
[    17.452] (II) FBDEV: driver for framebuffer: fbdev
[    17.452] (++) using VT number 7

[    17.452] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.453] (II) [KMS] Kernel modesetting enabled.
[    17.453] (WW) Falling back to old probe method for vesa
[    17.453] (WW) Falling back to old probe method for fbdev
[    17.453] (II) Loading sub module "fbdevhw"
[    17.453] (II) LoadModule: "fbdevhw"
[    17.453] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.453] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.453] 	compiled for 1.10.1, module version = 0.0.2
[    17.453] 	ABI class: X.Org Video Driver, version 10.0
[    17.453] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    17.453] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    17.453] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.453] (==) RADEON(0): Default visual is TrueColor
[    17.453] (==) RADEON(0): RGB weight 888
[    17.453] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.453] (--) RADEON(0): Chipset: "ATI Radeon HD 5800 Series" (ChipID = 0x689e)
[    17.453] (II) RADEON(0): PCIE card detected
[    17.453] drmOpenDevice: node name is /dev/dri/card0
[    17.453] drmOpenDevice: open result is 8, (OK)
[    17.453] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    17.453] drmOpenDevice: node name is /dev/dri/card0
[    17.453] drmOpenDevice: open result is 8, (OK)
[    17.453] drmOpenByBusid: drmOpenMinor returns 8
[    17.453] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    17.453] (II) RADEON(0): KMS Color Tiling: disabled
[    17.453] (II) RADEON(0): KMS Pageflipping: enabled
[    17.453] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    17.460] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[    17.464] (II) RADEON(0): Output HDMI-0 has no monitor section
[    17.887] (II) RADEON(0): Output DVI-0 has no monitor section
[    17.892] (II) RADEON(0): EDID for output DisplayPort-0
[    17.896] (II) RADEON(0): EDID for output HDMI-0
[    18.312] (II) RADEON(0): EDID for output DVI-0
[    18.312] (II) RADEON(0): Printing probed modes for output DVI-0
[    18.312] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.312] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.312] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.312] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    18.312] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    18.312] (II) RADEON(0): Output DisplayPort-0 disconnected
[    18.312] (II) RADEON(0): Output HDMI-0 disconnected
[    18.312] (II) RADEON(0): Output DVI-0 connected
[    18.312] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    18.312] (II) RADEON(0): Output DVI-0 using initial mode 1024x768
[    18.312] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.312] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:40000000 visible:fcc0000
[    18.312] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    18.312] (==) RADEON(0): DPI set to (96, 96)
[    18.312] (II) Loading sub module "fb"
[    18.312] (II) LoadModule: "fb"
[    18.312] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.312] (II) Module fb: vendor="X.Org Foundation"
[    18.312] 	compiled for 1.10.1, module version = 1.0.0
[    18.312] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.312] (II) Loading sub module "ramdac"
[    18.312] (II) LoadModule: "ramdac"
[    18.312] (II) Module "ramdac" already built-in
[    18.312] (II) Loading sub module "exa"
[    18.312] (II) LoadModule: "exa"
[    18.313] (II) Loading /usr/lib/xorg/modules/libexa.so
[    18.313] (II) Module exa: vendor="X.Org Foundation"
[    18.313] 	compiled for 1.10.1, module version = 2.5.0
[    18.313] 	ABI class: X.Org Video Driver, version 10.0
[    18.313] (II) UnloadModule: "vesa"
[    18.313] (II) Unloading vesa
[    18.313] (II) UnloadModule: "fbdev"
[    18.313] (II) Unloading fbdev
[    18.313] (II) UnloadModule: "fbdevhw"
[    18.313] (II) Unloading fbdevhw
[    18.313] (--) Depth 24 pixmap format is 32 bpp
[    18.313] (II) RADEON(0): [DRI2] Setup complete
[    18.313] (II) RADEON(0): [DRI2]   DRI driver: r600
[    18.313] (II) RADEON(0): Front buffer size: 3072K
[    18.313] (II) RADEON(0): VRAM usage limit set to 230169K
[    18.313] (==) RADEON(0): Backing store disabled
[    18.313] (II) RADEON(0): Direct rendering enabled
[    18.313] (II) RADEON(0): Setting EXA maxPitchBytes
[    18.313] (II) EXA(0): Driver allocated offscreen pixmaps
[    18.313] (II) EXA(0): Driver registered support for the following operations:
[    18.313] (II)         Solid
[    18.313] (II)         Copy
[    18.313] (II)         Composite (RENDER acceleration)
[    18.313] (II)         UploadToScreen
[    18.313] (II)         DownloadFromScreen
[    18.313] (II) RADEON(0): Acceleration enabled
[    18.313] (==) RADEON(0): DPMS enabled
[    18.313] (==) RADEON(0): Silken mouse enabled
[    18.313] (II) RADEON(0): Set up textured video
[    18.313] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.313] (--) RandR disabled
[    18.313] (II) Initializing built-in extension Generic Event Extension
[    18.313] (II) Initializing built-in extension SHAPE
[    18.313] (II) Initializing built-in extension MIT-SHM
[    18.313] (II) Initializing built-in extension XInputExtension
[    18.313] (II) Initializing built-in extension XTEST
[    18.313] (II) Initializing built-in extension BIG-REQUESTS
[    18.313] (II) Initializing built-in extension SYNC
[    18.313] (II) Initializing built-in extension XKEYBOARD
[    18.313] (II) Initializing built-in extension XC-MISC
[    18.313] (II) Initializing built-in extension SECURITY
[    18.313] (II) Initializing built-in extension XINERAMA
[    18.313] (II) Initializing built-in extension XFIXES
[    18.313] (II) Initializing built-in extension RENDER
[    18.313] (II) Initializing built-in extension RANDR
[    18.313] (II) Initializing built-in extension COMPOSITE
[    18.313] (II) Initializing built-in extension DAMAGE
[    18.313] (II) Initializing built-in extension GESTURE
[    18.320] (II) AIGLX: Trying DRI driver /usr/lib/dri/r600_dri.so
[    18.354] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.354] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.354] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.354] (II) AIGLX: enabled GLX_SGI_make_current_read
[    18.354] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.354] (II) AIGLX: Loaded and initialized r600
[    18.354] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.355] (II) RADEON(0): Setting screen physical size to 270 x 203
[    18.364] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.372] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.372] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.372] (II) LoadModule: "evdev"
[    18.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.373] (II) Module evdev: vendor="X.Org Foundation"
[    18.373] 	compiled for 1.10.0.902, module version = 2.6.0
[    18.373] 	Module class: X.Org XInput Driver
[    18.373] 	ABI class: X.Org XInput driver, version 12.3
[    18.373] (II) Using input driver 'evdev' for 'Power Button'
[    18.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.373] (**) Power Button: always reports core events
[    18.373] (**) Power Button: Device: "/dev/input/event1"
[    18.392] (--) Power Button: Found keys
[    18.392] (II) Power Button: Configuring as keyboard
[    18.392] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    18.392] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.392] (**) Option "xkb_rules" "evdev"
[    18.392] (**) Option "xkb_model" "pc105"
[    18.392] (**) Option "xkb_layout" "gb"
[    18.393] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    18.396] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.396] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.396] (II) Using input driver 'evdev' for 'Power Button'
[    18.396] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.396] (**) Power Button: always reports core events
[    18.396] (**) Power Button: Device: "/dev/input/event0"
[    18.416] (--) Power Button: Found keys
[    18.416] (II) Power Button: Configuring as keyboard
[    18.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.416] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.416] (**) Option "xkb_rules" "evdev"
[    18.416] (**) Option "xkb_model" "pc105"
[    18.416] (**) Option "xkb_layout" "gb"
[    18.417] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    18.417] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    18.417] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    18.417] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.417] (**) Logitech USB Receiver: always reports core events
[    18.417] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    18.436] (--) Logitech USB Receiver: Found keys
[    18.436] (II) Logitech USB Receiver: Configuring as keyboard
[    18.436] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2/event2"
[    18.436] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    18.436] (**) Option "xkb_rules" "evdev"
[    18.436] (**) Option "xkb_model" "pc105"
[    18.436] (**) Option "xkb_layout" "gb"
[    18.436] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    18.436] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    18.436] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    18.436] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    18.436] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.436] (**) Logitech USB Receiver: always reports core events
[    18.436] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    18.472] (--) Logitech USB Receiver: Found 12 mouse buttons
[    18.472] (--) Logitech USB Receiver: Found scroll wheel(s)
[    18.472] (--) Logitech USB Receiver: Found relative axes
[    18.472] (--) Logitech USB Receiver: Found x and y relative axes
[    18.472] (--) Logitech USB Receiver: Found absolute axes
[    18.472] (II) evdev-grail: failed to open grail, no gesture support
[    18.472] (--) Logitech USB Receiver: Found keys
[    18.472] (II) Logitech USB Receiver: Configuring as mouse
[    18.472] (II) Logitech USB Receiver: Configuring as keyboard
[    18.472] (II) Logitech USB Receiver: Adding scrollwheel support
[    18.472] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    18.472] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.472] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input3/event3"
[    18.472] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    18.472] (**) Option "xkb_rules" "evdev"
[    18.472] (**) Option "xkb_model" "pc105"
[    18.472] (**) Option "xkb_layout" "gb"
[    18.472] (II) Logitech USB Receiver: initialized for relative axes.
[    18.472] (WW) Logitech USB Receiver: ignoring absolute axes.
[    18.472] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    18.472] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    18.472] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    18.472] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    18.472] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    18.472] (II) No input driver/identifier specified (ignoring)
```

Hope someone can help. I've had nothing but trouble from this graphics card in Ubuntu. Next thing I'm going to try is the FLGRX drivers from AMD since these were updated to 11.6 the other day.

Cheers

Grindboy

[edit] sorry forgot to mention I'm hooked up to a 32inch LCD via a DVI-VGA adapter. I think this causes problems for auto-detecting the monitor. Hooking up over HDMI works in Ubuntu but then breaks Windows 7 where I do all my gaming.

[edit2] OK I was unable to install the proprietory drivers. (I've purged everything from the failed attempt) I found a tutorial here: [http://www.grenage.com/xorg.html]("http://www.grenage.com/xorg.html")

To write my own xorg.conf but it hasn't worked. Here's what I've got now:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Polaroid"
	ModelName "32inch"
	HorizSync 47.79
	VertRefresh 59.88
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "radeon"
	VendorName "RadeonHD 5830"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Depth 24
		Modes "1366x768"
	EndSubSection
EndSection
```

Any Ideas?

---

### Post by Toz on 2011-07-05
Can we see the Xorg.0.log file from when you used the xorg.conf file?
How did you get the modeline? cvt?

Also, your xorg.conf file has an error in it. In the screen section, Display subsection, you specify:> Modes "1366x768"
I think it should read:```
Modes "136[COLOR="Red"]8[/COLOR]x768"
```

Make the change to the xorg.conf file, try again, if its still a problem, post back your Xorg.0.log file.

Also, if you wanted to try manually installing the catalyst drivers, have a look at this HOWTO: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually")

---

### Post by grindboy on 2011-07-06
Hey Toz,

Thanks for replying. 1366x768 is definitely the native resolution of the monitor. 1360x768 is the VESA standard, I've never heard of using 1368x768 before.

Here is the Xorg.0.log file:
```
[    18.099] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    18.099] X Protocol Version 11, Revision 0
[    18.099] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    18.099] Current Operating System: Linux michael-desktop 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    18.099] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=2928d2b2-e5f7-4c87-a391-263d9986f500 ro quiet splash vt.handoff=7
[    18.099] Build Date: 21 May 2011  11:38:35AM
[    18.099] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    18.099] Current version of pixman: 0.20.2
[    18.099] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.099] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.100] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  6 12:42:54 2011
[    18.100] (==) Using config file: "/etc/X11/xorg.conf"
[    18.100] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.116] (==) No Layout section.  Using the first Screen section.
[    18.116] (**) |-->Screen "Screen0" (0)
[    18.116] (**) |   |-->Monitor "Monitor0"
[    18.116] (**) |   |-->Device "Device0"
[    18.116] (==) Automatically adding devices
[    18.116] (==) Automatically enabling devices
[    18.116] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.116] 	Entry deleted from font path.
[    18.116] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.116] 	Entry deleted from font path.
[    18.116] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.116] 	Entry deleted from font path.
[    18.116] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.116] 	Entry deleted from font path.
[    18.116] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.116] 	Entry deleted from font path.
[    18.116] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.116] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.116] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.116] (II) Loader magic: 0x81ffde0
[    18.116] (II) Module ABI versions:
[    18.116] 	X.Org ANSI C Emulation: 0.4
[    18.116] 	X.Org Video Driver: 10.0
[    18.116] 	X.Org XInput driver : 12.3
[    18.116] 	X.Org Server Extension : 5.0
[    18.116] (--) PCI:*(0:2:0:0) 1002:689e:174b:e177 rev 0, Mem @ 0xd0000000/268435456, 0xfddc0000/131072, I/O @ 0x0000ac00/256, BIOS @ 0x????????/131072
[    18.117] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    18.117] (II) LoadModule: "extmod"
[    18.127] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.127] (II) Module extmod: vendor="X.Org Foundation"
[    18.127] 	compiled for 1.10.1, module version = 1.0.0
[    18.127] 	Module class: X.Org Server Extension
[    18.127] 	ABI class: X.Org Server Extension, version 5.0
[    18.127] (II) Loading extension MIT-SCREEN-SAVER
[    18.127] (II) Loading extension XFree86-VidModeExtension
[    18.127] (II) Loading extension XFree86-DGA
[    18.127] (II) Loading extension DPMS
[    18.127] (II) Loading extension XVideo
[    18.127] (II) Loading extension XVideo-MotionCompensation
[    18.127] (II) Loading extension X-Resource
[    18.127] (II) LoadModule: "dbe"
[    18.127] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.127] (II) Module dbe: vendor="X.Org Foundation"
[    18.127] 	compiled for 1.10.1, module version = 1.0.0
[    18.127] 	Module class: X.Org Server Extension
[    18.127] 	ABI class: X.Org Server Extension, version 5.0
[    18.127] (II) Loading extension DOUBLE-BUFFER
[    18.127] (II) LoadModule: "glx"
[    18.127] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.128] (II) Module glx: vendor="X.Org Foundation"
[    18.128] 	compiled for 1.10.1, module version = 1.0.0
[    18.128] 	ABI class: X.Org Server Extension, version 5.0
[    18.128] (==) AIGLX enabled
[    18.128] (II) Loading extension GLX
[    18.128] (II) LoadModule: "record"
[    18.128] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.128] (II) Module record: vendor="X.Org Foundation"
[    18.128] 	compiled for 1.10.1, module version = 1.13.0
[    18.128] 	Module class: X.Org Server Extension
[    18.128] 	ABI class: X.Org Server Extension, version 5.0
[    18.128] (II) Loading extension RECORD
[    18.128] (II) LoadModule: "dri"
[    18.128] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.128] (II) Module dri: vendor="X.Org Foundation"
[    18.128] 	compiled for 1.10.1, module version = 1.0.0
[    18.128] 	ABI class: X.Org Server Extension, version 5.0
[    18.128] (II) Loading extension XFree86-DRI
[    18.128] (II) LoadModule: "dri2"
[    18.128] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.128] (II) Module dri2: vendor="X.Org Foundation"
[    18.128] 	compiled for 1.10.1, module version = 1.2.0
[    18.128] 	ABI class: X.Org Server Extension, version 5.0
[    18.128] (II) Loading extension DRI2
[    18.128] (II) LoadModule: "radeon"
[    18.128] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.129] (II) Module radeon: vendor="X.Org Foundation"
[    18.129] 	compiled for 1.10.0, module version = 6.14.0
[    18.129] 	Module class: X.Org Video Driver
[    18.129] 	ABI class: X.Org Video Driver, version 10.0
[    18.129] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    18.132] (++) using VT number 7

[    18.132] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.132] (II) [KMS] Kernel modesetting enabled.
[    18.132] (II) RADEON(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 16/16
[    18.132] (**) RADEON(0): Depth 16, (--) framebuffer bpp 16
[    18.132] (II) RADEON(0): Pixel depth = 16 bits stored in 2 bytes (16 bpp pixmaps)
[    18.132] (==) RADEON(0): Default visual is TrueColor
[    18.132] (==) RADEON(0): RGB weight 565
[    18.132] (II) RADEON(0): Using 6 bits per RGB (8 bit DAC)
[    18.132] (--) RADEON(0): Chipset: "ATI Radeon HD 5800 Series" (ChipID = 0x689e)
[    18.133] (II) RADEON(0): PCIE card detected
[    18.133] drmOpenDevice: node name is /dev/dri/card0
[    18.133] drmOpenDevice: open result is 8, (OK)
[    18.133] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    18.133] drmOpenDevice: node name is /dev/dri/card0
[    18.133] drmOpenDevice: open result is 8, (OK)
[    18.133] drmOpenByBusid: drmOpenMinor returns 8
[    18.133] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    18.133] (II) RADEON(0): KMS Color Tiling: disabled
[    18.133] (II) RADEON(0): KMS Pageflipping: enabled
[    18.133] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    18.140] (II) RADEON(0): Output DisplayPort-0 using monitor section Monitor0
[    18.144] (II) RADEON(0): Output HDMI-0 has no monitor section
[    18.566] (II) RADEON(0): Output DVI-0 has no monitor section
[    18.572] (II) RADEON(0): EDID for output DisplayPort-0
[    18.576] (II) RADEON(0): EDID for output HDMI-0
[    18.991] (II) RADEON(0): EDID for output DVI-0
[    18.991] (II) RADEON(0): Printing probed modes for output DVI-0
[    18.991] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.991] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.991] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.991] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    18.991] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    18.991] (II) RADEON(0): Output DisplayPort-0 disconnected
[    18.991] (II) RADEON(0): Output HDMI-0 disconnected
[    18.991] (II) RADEON(0): Output DVI-0 connected
[    18.991] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    18.991] (II) RADEON(0): Output DVI-0 using initial mode 1024x768
[    18.991] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.992] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:40000000 visible:fcc0000
[    18.992] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    18.992] (==) RADEON(0): DPI set to (96, 96)
[    18.992] (II) Loading sub module "fb"
[    18.992] (II) LoadModule: "fb"
[    18.992] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.992] (II) Module fb: vendor="X.Org Foundation"
[    18.992] 	compiled for 1.10.1, module version = 1.0.0
[    18.992] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.992] (II) Loading sub module "ramdac"
[    18.992] (II) LoadModule: "ramdac"
[    18.992] (II) Module "ramdac" already built-in
[    18.992] (II) Loading sub module "exa"
[    18.992] (II) LoadModule: "exa"
[    18.992] (II) Loading /usr/lib/xorg/modules/libexa.so
[    18.992] (II) Module exa: vendor="X.Org Foundation"
[    18.992] 	compiled for 1.10.1, module version = 2.5.0
[    18.992] 	ABI class: X.Org Video Driver, version 10.0
[    18.992] (II) RADEON(0): [DRI2] Setup complete
[    18.992] (II) RADEON(0): [DRI2]   DRI driver: r600
[    18.992] (II) RADEON(0): Front buffer size: 1536K
[    18.992] (II) RADEON(0): VRAM usage limit set to 231552K
[    18.992] (==) RADEON(0): Backing store disabled
[    18.992] (II) RADEON(0): Direct rendering enabled
[    18.992] (II) RADEON(0): Setting EXA maxPitchBytes
[    18.993] (II) EXA(0): Driver allocated offscreen pixmaps
[    18.993] (II) EXA(0): Driver registered support for the following operations:
[    18.993] (II)         Solid
[    18.993] (II)         Copy
[    18.993] (II)         Composite (RENDER acceleration)
[    18.993] (II)         UploadToScreen
[    18.993] (II)         DownloadFromScreen
[    18.993] (II) RADEON(0): Acceleration enabled
[    18.993] (==) RADEON(0): DPMS enabled
[    18.993] (==) RADEON(0): Silken mouse enabled
[    18.993] (II) RADEON(0): Set up textured video
[    18.993] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.993] (--) RandR disabled
[    18.993] (II) Initializing built-in extension Generic Event Extension
[    18.993] (II) Initializing built-in extension SHAPE
[    18.993] (II) Initializing built-in extension MIT-SHM
[    18.993] (II) Initializing built-in extension XInputExtension
[    18.993] (II) Initializing built-in extension XTEST
[    18.993] (II) Initializing built-in extension BIG-REQUESTS
[    18.993] (II) Initializing built-in extension SYNC
[    18.993] (II) Initializing built-in extension XKEYBOARD
[    18.993] (II) Initializing built-in extension XC-MISC
[    18.993] (II) Initializing built-in extension SECURITY
[    18.993] (II) Initializing built-in extension XINERAMA
[    18.993] (II) Initializing built-in extension XFIXES
[    18.993] (II) Initializing built-in extension RENDER
[    18.993] (II) Initializing built-in extension RANDR
[    18.993] (II) Initializing built-in extension COMPOSITE
[    18.993] (II) Initializing built-in extension DAMAGE
[    18.993] (II) Initializing built-in extension GESTURE
[    18.999] (II) AIGLX: Trying DRI driver /usr/lib/dri/r600_dri.so
[    19.008] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.008] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.008] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.008] (II) AIGLX: enabled GLX_SGI_make_current_read
[    19.008] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.008] (II) AIGLX: Loaded and initialized r600
[    19.008] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.009] (II) RADEON(0): Setting screen physical size to 270 x 203
[    19.017] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.024] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.024] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.024] (II) LoadModule: "evdev"
[    19.024] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.024] (II) Module evdev: vendor="X.Org Foundation"
[    19.024] 	compiled for 1.10.0.902, module version = 2.6.0
[    19.024] 	Module class: X.Org XInput Driver
[    19.024] 	ABI class: X.Org XInput driver, version 12.3
[    19.024] (II) Using input driver 'evdev' for 'Power Button'
[    19.024] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.025] (**) Power Button: always reports core events
[    19.025] (**) Power Button: Device: "/dev/input/event1"
[    19.040] (--) Power Button: Found keys
[    19.040] (II) Power Button: Configuring as keyboard
[    19.040] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.040] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.040] (**) Option "xkb_rules" "evdev"
[    19.040] (**) Option "xkb_model" "pc105"
[    19.040] (**) Option "xkb_layout" "gb"
[    19.042] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    19.044] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.044] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.044] (II) Using input driver 'evdev' for 'Power Button'
[    19.044] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.044] (**) Power Button: always reports core events
[    19.044] (**) Power Button: Device: "/dev/input/event0"
[    19.072] (--) Power Button: Found keys
[    19.072] (II) Power Button: Configuring as keyboard
[    19.072] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.072] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.072] (**) Option "xkb_rules" "evdev"
[    19.072] (**) Option "xkb_model" "pc105"
[    19.072] (**) Option "xkb_layout" "gb"
[    19.073] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    19.073] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    19.073] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    19.073] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.073] (**) Logitech USB Receiver: always reports core events
[    19.073] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    19.092] (--) Logitech USB Receiver: Found keys
[    19.092] (II) Logitech USB Receiver: Configuring as keyboard
[    19.092] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2/event2"
[    19.092] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    19.092] (**) Option "xkb_rules" "evdev"
[    19.092] (**) Option "xkb_model" "pc105"
[    19.092] (**) Option "xkb_layout" "gb"
[    19.092] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    19.092] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    19.092] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    19.092] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    19.092] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.092] (**) Logitech USB Receiver: always reports core events
[    19.092] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    19.092] (--) Logitech USB Receiver: Found 12 mouse buttons
[    19.093] (--) Logitech USB Receiver: Found scroll wheel(s)
[    19.093] (--) Logitech USB Receiver: Found relative axes
[    19.093] (--) Logitech USB Receiver: Found x and y relative axes
[    19.093] (--) Logitech USB Receiver: Found absolute axes
[    19.093] (II) evdev-grail: failed to open grail, no gesture support
[    19.093] (--) Logitech USB Receiver: Found keys
[    19.093] (II) Logitech USB Receiver: Configuring as mouse
[    19.093] (II) Logitech USB Receiver: Configuring as keyboard
[    19.093] (II) Logitech USB Receiver: Adding scrollwheel support
[    19.093] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    19.093] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.093] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input3/event3"
[    19.093] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    19.093] (**) Option "xkb_rules" "evdev"
[    19.093] (**) Option "xkb_model" "pc105"
[    19.093] (**) Option "xkb_layout" "gb"
[    19.093] (II) Logitech USB Receiver: initialized for relative axes.
[    19.093] (WW) Logitech USB Receiver: ignoring absolute axes.
[    19.093] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    19.093] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    19.093] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    19.093] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    19.093] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    19.093] (II) No input driver/identifier specified (ignoring)
```

I'm wondering now if something is borked in the driver since I'm getting some graphical glitching. Since all my data is on a separate drive and it's no hassle to do so I might try a fresh install. I'm thinking that all the messing around with drivers might have broken something. I'll wait for your response first though.

Cheers

Grindboy

[edit] Sorry, yes I used cvt to get the modeline.

---

### Post by Grenage on 2011-07-06
> **grindboy said:**
> sorry forgot to mention I'm hooked up to a 32inch LCD via a DVI-VGA adapter. I think this causes problems for auto-detecting the monitor.

That is most likely the cause; does the monitor/TV use a DVI connection or a VGA connection?  I'm surprised that Windows had an issue with the HDMI output, was the resolution just incorrect?

Does setting the mode with xrandr help, if you've looked at that?  If not, could you post the output of the following:

```
xrandr -q
```

---

### Post by grindboy on 2011-07-06
Hi Grenage,

The TV is a fairly old flat panel (probably getting on for 5 years old now) It's only got a VGA port for PC connections.

I tried using xrandr before to no avail. xranr -q is listed below:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
```

Windows 7 could only output at the standard HD resolutions (720p/1080i/1080p etc) I'm looking at forcing the resolution with registry edits but I'm loathed to do this since I've been running Linux for so long that I'm no longer familiar with Windows.

---

### Post by Toz on 2011-07-06
Okay, then the modeline entry in xorg.conf is wrong - it specifies 1368x768.

---

### Post by Grenage on 2011-07-06
> **grindboy said:**
> Hi Grenage,

The TV is a fairly old flat panel (probably getting on for 5 years old now) It's only got a VGA port for PC connections.

I tried using xrandr before to no avail. xranr -q is listed below:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
```

Windows 7 could only output at the standard HD resolutions (720p/1080i/1080p etc) I'm looking at forcing the resolution with registry edits but I'm loathed to do this since I've been running Linux for so long that I'm no longer familiar with Windows.

It may just be a driver issue in Windows, I've seen that plenty of times;  you could try updating them.

Anyhow, try this in Linux:

```
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode DVI-0 1368x768
xrandr --output DVI-0 --mode 1368x768
```

It basically adds a new resolution (mode), associates that mode with the output (DVI-0), then tells that output to use the mode.

---

### Post by grindboy on 2011-07-06
OK after the command:
xrandr --addmode DVI-0 1368x768

I get the response:
xrandr: cannot find mode "1368x768"

---

### Post by Grenage on 2011-07-06
> **grindboy said:**
> OK after the command:
xrandr --addmode DVI-0 1368x768

I get the response:
xrandr: cannot find mode "1368x768"

Oops, typo on my part; it should be:

```
xrandr --addmode DVI-0 1368x768_60.00
```

We declared the name as such when we added the resolution, so the same will be true of the third command.

---

### Post by grindboy on 2011-07-06
OK That's worked but I'm still getting some graphical glitching. Also 1368x768 is definitely not the correct resolution. [s]What would the commands be for 1366x768?[/s]

Thanks

[edit] OK I figured out the command for 1360x768 and everything is looking perfect again. How do I make these changes permanent?

[edit2] Found that solution here: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Going to reboot and see if that fixes the graphical glitches. BRB

OK the Glitching is still hanging around which I'm not happy with. I get the old digital noise (a bit like this: [http://www.thedirective.com/images/corrupt_01o.jpg]("http://www.thedirective.com/images/corrupt_01o.jpg") Between the end of the ubuntu logo and the login screen. Also changing from workspace to workspace causes my wallpaper to be black until something locally refreshes it like conky updating or opening a right click menu.

---

### Post by Grenage on 2011-07-06
> **grindboy said:**
> OK That's worked but I'm still getting some graphical glitching. Also 1368x768 is definitely not the correct resolution. [s]What would the commands be for 1366x768?[/s]

Thanks

[edit] OK I figured out the command for 1360x768 and everything is looking perfect again. How do I make these changes permanent?

I was going to suggest that; the resolution should always be divisible by 8, hence cvt's adjustment - it's so forgiving. ;)

I've never had to do this on my machines, but the general advice is to add the commands to the default init file:

```
gksudo gedit /etc/gdm/Init/Default
```

Underneath the line **OLD_IFS=$IFS, which should be near the top, add your three commands.  First the newmode, then the addmode, then the output.

---

### Post by grindboy on 2011-07-06
Sorry didn't see your reply had gone over to the second page.

I made it permanant and rebooted but the Glitching is still hanging around which I'm not happy with. I get the old digital noise (a bit like this: [http://www.thedirective.com/images/corrupt_01o.jpg]("http://www.thedirective.com/images/corrupt_01o.jpg") Between the end of the ubuntu logo and the login screen. Also changing from workspace to workspace causes my wallpaper to be black until something locally refreshes it like conky updating or opening a right click menu.

---

### Post by Grenage on 2011-07-06
> **grindboy said:**
> OK That's worked but I'm still getting some graphical glitching. Also 1368x768 is definitely not the correct resolution. [s]What would the commands be for 1366x768?[/s]

Thanks

[edit] OK I figured out the command for 1360x768 and everything is looking perfect again. How do I make these changes permanent?

[edit2] Found that solution here: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Going to reboot and see if that fixes the graphical glitches. BRB

OK the Glitching is still hanging around which I'm not happy with. I get the old digital noise (a bit like this: [http://www.thedirective.com/images/corrupt_01o.jpg]("http://www.thedirective.com/images/corrupt_01o.jpg") Between the end of the ubuntu logo and the login screen. Also changing from workspace to workspace causes my wallpaper to be black until something locally refreshes it like conky updating or opening a right click menu.

This sounds like a driver issue to me, and I'd try the flgrx drivers.  I abandoned all ATI cards some time ago due to the proprietary and open drivers not being particularly reliable.  They're apparently much better now, but obviously not perfect.  I'm off for some lunch now, but I'll check back in a bit.

---

### Post by h3nning94 on 2011-07-06
Hey,

I'm having a similar problem. I've got Ubuntu on my laptop and I run 1366x768 on it, but when I try to connect it to my TV with an HDMI-cable, it says "Monitor: Unknown" when I go to Monitors in Preferences. Before I updated my graphics card, I could at least get 1024x768 resolution when I connected it.

---

### Post by grindboy on 2011-07-06
Yeh when I built my current pc I foolishly forgot that ATI/AMD support was pants. I'll try the FLGRX driver.

OK I'm having real difficulties installing the FGLRX driver from the AMD website. I'm going to try a fresh install as I have a feeling there is more broken than meets the eye.

---

### Post by Grenage on 2011-07-06
> **h3nning94 said:**
> Hey,

I'm having a similar problem. I've got Ubuntu on my laptop and I run 1366x768 on it, but when I try to connect it to my TV with an HDMI-cable, it says "Monitor: Unknown" when I go to Monitors in Preferences. Before I updated my graphics card, I could at least get 1024x768 resolution when I connected it.

You could add the monitor in an xorg.conf, which should then be used for the settings when you plug the monitor in.  You can also (and this might be easier) configure the monitor with xrandr, as grindboy has done.

> **grindboy said:**
> Yeh when I built my current pc I foolishly forgot that ATI/AMD support was pants. I'll try the FLGRX driver.

OK I'm having real difficulties installing the FGLRX driver from the AMD website. I'm going to try a fresh install as I have a feeling there is more broken than meets the eye.

I take it the ones available through Ubuntu's *Additional Drivers* didn't work?

---

### Post by grindboy on 2011-07-06
No the ubuntu additional drivers are a mess and the AMD one is a horrible mass of pain and anguish.

As I suspected there was more broken under the bonnet than I thought since I've reinstalled ubuntu from scratch and updated to the latest opensource drivers which can be found here from the Swat-X PPA:
[https://launchpad.net/~ubuntu-x-swat]("https://launchpad.net/~ubuntu-x-swat")

Since I did that everything has been working fine.

Thanks for all the help.

Grindboy

---

### Post by Grenage on 2011-07-06
> **grindboy said:**
> No the ubuntu additional drivers are a mess and the AMD one is a horrible mass of pain and anguish.

As I suspected there was more broken under the bonnet than I thought since I've reinstalled ubuntu from scratch and updated to the latest opensource drivers which can be found here from the Swat-X PPA:
[https://launchpad.net/~ubuntu-x-swat]("https://launchpad.net/~ubuntu-x-swat")

Since I did that everything has been working fine.

Thanks for all the help.

Grindboy

Great stuff, well played.

---

