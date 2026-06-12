---
title: "monitor wrongly recognised, id my graphics card"
date: 2011-01-07
forum: Multimedia Software
---

### Post by surfmonkee on 2011-01-07
i have installed 10.10 studio on a 1.7ghz desktop machine.

this connected via dvi output on the graphics card via hdmi to a 32" LG lcd tv.

last time i ran ubuntu live was 9.4 on the same machine and it recognised my tv as an LG 32"

ubuntu studio tells me i have a goldstar 52" tv connected!


atm i can only get it 1360x768 which is rubbish, in xp i was running at 1080 x 1920

---

### Post by surfmonkee on 2011-01-07
i managed to find this about my graphics card if thats a help

 *-display
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller      bus_mastercap_list

---

### Post by Yellow Pasque on 2011-01-07
Post your /var/log/Xorg.0.log

---

### Post by surfmonkee on 2011-01-07
typing 

/var/log/Xorg.0.log 

in to the terminal produces 'permission denied'

---

### Post by Yellow Pasque on 2011-01-07
How about:
```
gedit /var/log/Xorg.0.log
```

Remember to use [ code ][ /code ] when you paste it.

---

### Post by surfmonkee on 2011-01-07
[    35.000] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    35.001] X Protocol Version 11, Revision 0
[    35.001] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    35.001] Current Operating System: Linux unknown000ae6611e24 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    35.001] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=17cbcaaa-6987-4410-ba45-621c53287645 ro quiet splash
[    35.001] Build Date: 16 September 2010  05:39:22PM
[    35.001] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    35.001] Current version of pixman: 0.18.4
[    35.001] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    35.002] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    35.002] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  7 17:44:28 2011
[    35.048] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    35.049] (==) No Layout section.  Using the first Screen section.
[    35.050] (==) No screen section available. Using defaults.
[    35.050] (**) |-->Screen "Default Screen Section" (0)
[    35.050] (**) |   |-->Monitor "<default monitor>"
[    35.050] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    35.051] (==) Automatically adding devices
[    35.051] (==) Automatically enabling devices
[    35.051] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    35.051] 	Entry deleted from font path.
[    35.052] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    35.052] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    35.052] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    35.052] (II) Loader magic: 0x81f8e00
[    35.052] (II) Module ABI versions:
[    35.052] 	X.Org ANSI C Emulation: 0.4
[    35.052] 	X.Org Video Driver: 8.0
[    35.052] 	X.Org XInput driver : 11.0
[    35.053] 	X.Org Server Extension : 4.0
[    35.055] (--) PCI:*(0:1:0:0) 1002:5159:174b:0280 rev 0, Mem @ 0xd0000000/134217728, 0xdfef0000/65536, I/O @ 0x0000c800/256, BIOS @ 0x????????/131072
[    35.058] (II) Open ACPI successful (/var/run/acpid.socket)
[    35.058] (II) LoadModule: "extmod"
[    35.095] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    35.096] (II) Module extmod: vendor="X.Org Foundation"
[    35.096] 	compiled for 1.9.0, module version = 1.0.0
[    35.096] 	Module class: X.Org Server Extension
[    35.096] 	ABI class: X.Org Server Extension, version 4.0
[    35.097] (II) Loading extension MIT-SCREEN-SAVER
[    35.097] (II) Loading extension XFree86-VidModeExtension
[    35.097] (II) Loading extension XFree86-DGA
[    35.097] (II) Loading extension DPMS
[    35.097] (II) Loading extension XVideo
[    35.097] (II) Loading extension XVideo-MotionCompensation
[    35.097] (II) Loading extension X-Resource
[    35.097] (II) LoadModule: "dbe"
[    35.098] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    35.099] (II) Module dbe: vendor="X.Org Foundation"
[    35.099] 	compiled for 1.9.0, module version = 1.0.0
[    35.099] 	Module class: X.Org Server Extension
[    35.099] 	ABI class: X.Org Server Extension, version 4.0
[    35.099] (II) Loading extension DOUBLE-BUFFER
[    35.099] (II) LoadModule: "glx"
[    35.115] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    35.116] (II) Module glx: vendor="X.Org Foundation"
[    35.116] 	compiled for 1.9.0, module version = 1.0.0
[    35.116] 	ABI class: X.Org Server Extension, version 4.0
[    35.116] (==) AIGLX enabled
[    35.116] (II) Loading extension GLX
[    35.117] (II) LoadModule: "record"
[    35.118] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    35.119] (II) Module record: vendor="X.Org Foundation"
[    35.119] 	compiled for 1.9.0, module version = 1.13.0
[    35.119] 	Module class: X.Org Server Extension
[    35.119] 	ABI class: X.Org Server Extension, version 4.0
[    35.119] (II) Loading extension RECORD
[    35.119] (II) LoadModule: "dri"
[    35.128] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.130] (II) Module dri: vendor="X.Org Foundation"
[    35.130] 	compiled for 1.9.0, module version = 1.0.0
[    35.130] 	ABI class: X.Org Server Extension, version 4.0
[    35.130] (II) Loading extension XFree86-DRI
[    35.130] (II) LoadModule: "dri2"
[    35.131] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.149] (II) Module dri2: vendor="X.Org Foundation"
[    35.149] 	compiled for 1.9.0, module version = 1.2.0
[    35.149] 	ABI class: X.Org Server Extension, version 4.0
[    35.149] (II) Loading extension DRI2
[    35.149] (==) Matched ati as autoconfigured driver 0
[    35.149] (==) Matched vesa as autoconfigured driver 1
[    35.149] (==) Matched fbdev as autoconfigured driver 2
[    35.149] (==) Assigned the driver to the xf86ConfigLayout
[    35.150] (II) LoadModule: "ati"
[    35.151] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    35.151] (II) Module ati: vendor="X.Org Foundation"
[    35.151] 	compiled for 1.9.0, module version = 6.13.1
[    35.151] 	Module class: X.Org Video Driver
[    35.152] 	ABI class: X.Org Video Driver, version 8.0
[    35.156] (II) LoadModule: "radeon"
[    35.157] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    35.159] (II) Module radeon: vendor="X.Org Foundation"
[    35.159] 	compiled for 1.9.0, module version = 6.13.1
[    35.159] 	Module class: X.Org Video Driver
[    35.159] 	ABI class: X.Org Video Driver, version 8.0
[    35.159] (II) LoadModule: "vesa"
[    35.166] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.167] (II) Module vesa: vendor="X.Org Foundation"
[    35.173] 	compiled for 1.8.99.905, module version = 2.3.0
[    35.173] 	Module class: X.Org Video Driver
[    35.173] 	ABI class: X.Org Video Driver, version 8.0
[    35.173] (II) LoadModule: "fbdev"
[    35.174] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.175] (II) Module fbdev: vendor="X.Org Foundation"
[    35.175] 	compiled for 1.8.99.905, module version = 0.4.2
[    35.175] 	ABI class: X.Org Video Driver, version 8.0
[    35.176] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    35.243] (II) VESA: driver for VESA chipsets: vesa
[    35.243] (II) FBDEV: driver for framebuffer: fbdev
[    35.243] (++) using VT number 7

[    35.244] (II) [KMS] Kernel modesetting enabled.
[    35.244] (WW) Falling back to old probe method for vesa
[    35.245] (WW) Falling back to old probe method for fbdev
[    35.245] (II) Loading sub module "fbdevhw"
[    35.245] (II) LoadModule: "fbdevhw"
[    35.247] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    35.247] (II) Module fbdevhw: vendor="X.Org Foundation"
[    35.247] 	compiled for 1.9.0, module version = 0.0.2
[    35.248] 	ABI class: X.Org Video Driver, version 8.0
[    35.248] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    35.248] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    35.248] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    35.249] (==) RADEON(0): Default visual is TrueColor
[    35.249] (==) RADEON(0): RGB weight 888
[    35.249] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    35.249] (--) RADEON(0): Chipset: "ATI Radeon VE/7000 QY (AGP/PCI)" (ChipID = 0x5159)
[    35.249] (II) RADEON(0): AGP card detected
[    35.250] (II) RADEON(0): KMS Color Tiling: disabled
[    35.251] drmOpenDevice: node name is /dev/dri/card0
[    35.252] drmOpenDevice: open result is 9, (OK)
[    35.252] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    35.252] drmOpenDevice: node name is /dev/dri/card0
[    35.252] drmOpenDevice: open result is 9, (OK)
[    35.252] drmOpenByBusid: drmOpenMinor returns 9
[    35.252] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    35.293] (II) RADEON(0): Output VGA-0 has no monitor section
[    35.407] (II) RADEON(0): Output DVI-0 has no monitor section
[    35.414] (II) RADEON(0): Output S-video has no monitor section
[    35.452] (II) RADEON(0): EDID for output VGA-0
[    35.558] (II) RADEON(0): EDID for output DVI-0
[    35.558] (II) RADEON(0): Manufacturer: GSM  Model: 1  Serial#: 16843009
[    35.558] (II) RADEON(0): Year: 2009  Week: 2
[    35.558] (II) RADEON(0): EDID Version: 1.3
[    35.558] (II) RADEON(0): Digital Display Input
[    35.559] (II) RADEON(0): Max Image Size [cm]: horiz.: 115  vert.: 65
[    35.559] (II) RADEON(0): Gamma: 2.20
[    35.559] (II) RADEON(0): No DPMS capabilities specified
[    35.559] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    35.559] (II) RADEON(0): First detailed timing is preferred mode
[    35.559] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.300 greenY: 0.690
[    35.559] (II) RADEON(0): blueX: 0.138 blueY: 0.038   whiteX: 0.282 whiteY: 0.297
[    35.560] (II) RADEON(0): Supported established timings:
[    35.560] (II) RADEON(0): 720x400@70Hz
[    35.560] (II) RADEON(0): 640x480@60Hz
[    35.560] (II) RADEON(0): 800x600@60Hz
[    35.560] (II) RADEON(0): 1024x768@60Hz
[    35.560] (II) RADEON(0): Manufacturer's mask: 0
[    35.560] (II) RADEON(0): Supported standard timings:
[    35.560] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    35.560] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    35.560] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    35.561] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 60  vid: 16433
[    35.561] (II) RADEON(0): Supported detailed timing:
[    35.561] (II) RADEON(0): clock: 148.5 MHz   Image Size:  1150 x 650 mm
[    35.561] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    35.561] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    35.561] (II) RADEON(0): Supported detailed timing:
[    35.561] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1150 x 650 mm
[    35.561] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    35.561] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    35.562] (II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 83 kHz, PixClock max 165 MHz
[    35.562] (II) RADEON(0): Monitor name: LG TV
[    35.562] (II) RADEON(0): Supported detailed timing:
[    35.562] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1150 x 650 mm
[    35.562] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    35.562] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    35.562] (II) RADEON(0): Supported detailed timing:
[    35.562] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1150 x 650 mm
[    35.562] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
[    35.563] (II) RADEON(0): v_active: 720  v_sync: 723  v_sync_end 728 v_blanking: 732 v_border: 0
[    35.563] (II) RADEON(0): Supported detailed timing:
[    35.563] (II) RADEON(0): clock: 148.5 MHz   Image Size:  1150 x 650 mm
[    35.563] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    35.563] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    35.563] (II) RADEON(0): Supported detailed timing:
[    35.563] (II) RADEON(0): clock: 85.5 MHz   Image Size:  1150 x 650 mm
[    35.563] (II) RADEON(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[    35.563] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[    35.564] (II) RADEON(0): Number of EDID sections to follow: 1
[    35.564] (II) RADEON(0): EDID (in hex):
[    35.564] (II) RADEON(0): 	00ffffffffffff001e6d010001010101
[    35.564] (II) RADEON(0): 	02130103807341780acf74a3574cb023
[    35.564] (II) RADEON(0): 	09484ca1080081806140454031400101
[    35.564] (II) RADEON(0): 	010101010101023a801871382d40582c
[    35.564] (II) RADEON(0): 	45007e8a4200001e011d007251d01e20
[    35.564] (II) RADEON(0): 	6e2855007e8a4200001e000000fd003a
[    35.564] (II) RADEON(0): 	3e1e5310000a202020202020000000fc
[    35.565] (II) RADEON(0): 	004c472054560a202020202020200104
[    35.565] (II) RADEON(0): Printing probed modes for output DVI-0
[    35.565] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.565] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    35.565] (II) RADEON(0): Modeline "1280x720"x61.0   74.25  1280 1344 1472 1664  720 723 728 732 +hsync +vsync (44.6 kHz)
[    35.565] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    35.565] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.565] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.566] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.566] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    35.566] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.572] (II) RADEON(0): EDID for output S-video
[    35.572] (II) RADEON(0): Output VGA-0 disconnected
[    35.572] (II) RADEON(0): Output DVI-0 connected
[    35.572] (II) RADEON(0): Output S-video disconnected
[    35.573] (II) RADEON(0): Using exact sizes for initial modes
[    35.573] (II) RADEON(0): Output DVI-0 using initial mode 1360x768
[    35.573] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.573] (II) RADEON(0): mem size init: gart size :3dff000 vram size: s:2000000 visible:1e80000
[    35.573] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    35.573] (==) RADEON(0): DPI set to (96, 96)
[    35.573] (II) Loading sub module "fb"
[    35.573] (II) LoadModule: "fb"
[    35.575] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.576] (II) Module fb: vendor="X.Org Foundation"
[    35.576] 	compiled for 1.9.0, module version = 1.0.0
[    35.576] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.576] (II) Loading sub module "ramdac"
[    35.576] (II) LoadModule: "ramdac"
[    35.576] (II) Module "ramdac" already built-in
[    35.577] (II) Loading sub module "exa"
[    35.577] (II) LoadModule: "exa"
[    35.578] (II) Loading /usr/lib/xorg/modules/libexa.so
[    35.579] (II) Module exa: vendor="X.Org Foundation"
[    35.579] 	compiled for 1.9.0, module version = 2.5.0
[    35.579] 	ABI class: X.Org Video Driver, version 8.0
[    35.579] (II) UnloadModule: "vesa"
[    35.579] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.579] (II) UnloadModule: "fbdev"
[    35.579] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.579] (II) UnloadModule: "fbdevhw"
[    35.579] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    35.580] (--) Depth 24 pixmap format is 32 bpp
[    35.580] (II) RADEON(0): [DRI2] Setup complete
[    35.580] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    35.581] (II) RADEON(0): Front buffer size: 4080K
[    35.581] (II) RADEON(0): VRAM usage limit set to 24436K
[    35.582] (==) RADEON(0): Backing store disabled
[    35.582] (II) RADEON(0): Direct rendering enabled
[    35.582] (II) RADEON(0): Render acceleration enabled for R100 type cards.
[    35.582] (II) RADEON(0): Setting EXA maxPitchBytes
[    35.582] (II) EXA(0): Driver allocated offscreen pixmaps
[    35.582] (II) EXA(0): Driver registered support for the following operations:
[    35.583] (II)         Solid
[    35.583] (II)         Copy
[    35.583] (II)         Composite (RENDER acceleration)
[    35.583] (II)         UploadToScreen
[    35.583] (II)         DownloadFromScreen
[    35.583] (II) RADEON(0): Acceleration enabled
[    35.583] (==) RADEON(0): DPMS enabled
[    35.583] (==) RADEON(0): Silken mouse enabled
[    35.584] (II) RADEON(0): Set up textured video
[    35.584] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.585] (--) RandR disabled
[    35.585] (II) Initializing built-in extension Generic Event Extension
[    35.585] (II) Initializing built-in extension SHAPE
[    35.585] (II) Initializing built-in extension MIT-SHM
[    35.585] (II) Initializing built-in extension XInputExtension
[    35.585] (II) Initializing built-in extension XTEST
[    35.585] (II) Initializing built-in extension BIG-REQUESTS
[    35.586] (II) Initializing built-in extension SYNC
[    35.586] (II) Initializing built-in extension XKEYBOARD
[    35.586] (II) Initializing built-in extension XC-MISC
[    35.586] (II) Initializing built-in extension SECURITY
[    35.586] (II) Initializing built-in extension XINERAMA
[    35.586] (II) Initializing built-in extension XFIXES
[    35.586] (II) Initializing built-in extension RENDER
[    35.586] (II) Initializing built-in extension RANDR
[    35.586] (II) Initializing built-in extension COMPOSITE
[    35.586] (II) Initializing built-in extension DAMAGE
[    35.586] (II) Initializing built-in extension GESTURE
[    35.626] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.626] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.626] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.626] (II) AIGLX: enabled GLX_SGI_make_current_read
[    35.626] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.627] (II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
[    35.627] (II) GLX: Initialized DRI2 GL provider for screen 0
[    35.790] (II) RADEON(0): Setting screen physical size to 359 x 203
[    35.858] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    35.900] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    35.900] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.901] (II) LoadModule: "evdev"
[    35.902] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.904] (II) Module evdev: vendor="X.Org Foundation"
[    35.904] 	compiled for 1.9.0, module version = 2.3.2
[    35.904] 	Module class: X.Org XInput Driver
[    35.904] 	ABI class: X.Org XInput driver, version 11.0
[    35.904] (**) Power Button: always reports core events
[    35.905] (**) Power Button: Device: "/dev/input/event2"
[    35.905] (II) Power Button: Found keys
[    35.905] (II) Power Button: Configuring as keyboard
[    35.905] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    35.905] (**) Option "xkb_rules" "evdev"
[    35.905] (**) Option "xkb_model" "pc105"
[    35.906] (**) Option "xkb_layout" "us"
[    35.906] (**) Option "xkb_options" "lv3:ralt_switch"
[    35.913] (II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
[    35.920] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    35.920] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.920] (**) Power Button: always reports core events
[    35.920] (**) Power Button: Device: "/dev/input/event0"
[    35.920] (II) Power Button: Found keys
[    35.920] (II) Power Button: Configuring as keyboard
[    35.921] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    35.921] (**) Option "xkb_rules" "evdev"
[    35.921] (**) Option "xkb_model" "pc105"
[    35.921] (**) Option "xkb_layout" "us"
[    35.921] (**) Option "xkb_options" "lv3:ralt_switch"
[    35.923] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    35.923] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    35.924] (**) Sleep Button: always reports core events
[    35.924] (**) Sleep Button: Device: "/dev/input/event1"
[    35.924] (II) Sleep Button: Found keys
[    35.924] (II) Sleep Button: Configuring as keyboard
[    35.925] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    35.925] (**) Option "xkb_rules" "evdev"
[    35.925] (**) Option "xkb_model" "pc105"
[    35.925] (**) Option "xkb_layout" "us"
[    35.925] (**) Option "xkb_options" "lv3:ralt_switch"
[    35.958] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    35.959] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.959] (**) AT Translated Set 2 keyboard: always reports core events
[    35.959] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    35.959] (II) AT Translated Set 2 keyboard: Found keys
[    35.959] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    35.960] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    35.960] (**) Option "xkb_rules" "evdev"
[    35.960] (**) Option "xkb_model" "pc105"
[    35.960] (**) Option "xkb_layout" "us"
[    35.960] (**) Option "xkb_options" "lv3:ralt_switch"
[    35.963] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[    35.963] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    35.963] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    35.963] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[    35.963] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    35.964] (II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    35.964] (II) ImPS/2 Generic Wheel Mouse: Found relative axes
[    35.964] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    35.964] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    35.964] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    35.964] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.964] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    35.965] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    35.966] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    35.967] (II) No input driver/identifier specified (ignoring)
[    39.055] (II) RADEON(0): EDID vendor "GSM", prod id 1
[    39.055] (II) RADEON(0): Using EDID range info for horizontal sync
[    39.060] (II) RADEON(0): Using EDID range info for vertical refresh
[    39.060] (II) RADEON(0): Printing DDC gathered Modelines:
[    39.060] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    39.060] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    39.060] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    39.060] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1344 1472 1664  720 723 728 732 +hsync +vsync (44.6 kHz)
[    39.061] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    39.061] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    39.061] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    39.061] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    39.061] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.061] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    39.061] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    39.061] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    39.061] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    39.062] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    39.062] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    39.062] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.062] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    39.062] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    39.062] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz)
[    39.062] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.575] (II) RADEON(0): EDID vendor "GSM", prod id 1
[    39.576] (II) RADEON(0): Using hsync ranges from config file
[    39.576] (II) RADEON(0): Using vrefresh ranges from config file
[    39.576] (II) RADEON(0): Printing DDC gathered Modelines:
[    39.576] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    39.576] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    39.576] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    39.577] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1344 1472 1664  720 723 728 732 +hsync +vsync (44.6 kHz)
[    39.577] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    39.577] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    39.577] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    39.577] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    39.577] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.577] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    39.578] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    39.578] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    39.578] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    39.578] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    39.578] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    39.578] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.578] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    39.578] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    39.579] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz)
[    39.579] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.860] (II) RADEON(0): EDID vendor "GSM", prod id 1
[    39.860] (II) RADEON(0): Using hsync ranges from config file
[    39.860] (II) RADEON(0): Using vrefresh ranges from config file
[    39.860] (II) RADEON(0): Printing DDC gathered Modelines:
[    39.860] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    39.861] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    39.861] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    39.861] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1344 1472 1664  720 723 728 732 +hsync +vsync (44.6 kHz)
[    39.861] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    39.861] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    39.861] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    39.861] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    39.861] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.862] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    39.862] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    39.862] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    39.862] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    39.862] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    39.862] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    39.862] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.862] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    39.863] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    39.863] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz)
[    39.863] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    47.847] (II) RADEON(0): EDID vendor "GSM", prod id 1
[    47.847] (II) RADEON(0): Using hsync ranges from config file
[    47.852] (II) RADEON(0): Using vrefresh ranges from config file
[    47.852] (II) RADEON(0): Printing DDC gathered Modelines:
[    47.852] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    47.852] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    47.852] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    47.852] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1344 1472 1664  720 723 728 732 +hsync +vsync (44.6 kHz)
[    47.853] (II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    47.853] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.853] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.853] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    47.853] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.853] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    47.853] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    47.853] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    47.854] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    47.854] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    47.854] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    47.854] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    47.854] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    47.854] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    47.854] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz)
[    47.854] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)

---

### Post by BicyclerBoy on 2011-01-07
You can try to take the LG out of Goldstar but you can't take the Goldstar out of LG.

LG is/was Goldstar Electronics.
Some of their products are very Goldstar.

---

### Post by surfmonkee on 2011-01-07
> **BicyclerBoy said:**
> You can try to take the LG out of Goldstar but you can't take the Goldstar out of LG.

LG is/was Goldstar Electronics.
Some of their products are very Goldstar.

omg, well i never knew that... but i do know that manufacturers drop stuff out in different names.

that does not however , resolve the point of ubuntu 9.2 seeing an LG 32" and meerkat seeing a 52" goldstar.

windows saw a 32" 1080 1924 panel and did it out of the box.  i know i can not expect out of the box in linux. thats cool. but i do not expect to see in google that the manufacturer of my graphics card decides to stop supporting a product and i get **** graphics in vlc player :)

twats. .

have a nice evening.


and looking at that terminal ouput above something can see 1080 1924 in radeon talk, so why i can't my telly see it. damnit.

---

### Post by BicyclerBoy on 2011-01-07
sorry about the goldstar comment.

I have no experience of the radeon things..

AFAIK your monitor reports EDID modes and they include 1080.
But the mode validation by the video card seems to exclude them.

I would find out what driver you are using now & what was working before.
The ATI radeon driver situation is a complete mess.
You need to find out what supports AGP cards with your GPU.

Not really Ubuntu's fault that the proprietary drivers are so hit & miss.

With nvidia X server you can force EDID validation off in xorg.conf and output what you want.
I don't know the correct keywords for radeon driver.

(Buy a nvidia GPU & enjoy...)

---

### Post by Yellow Pasque on 2011-01-07
Radeon 7000 is really old.
You could try to boot with radeon.nomodeset=1 and see if that helps.

---

### Post by tjones00 on 2011-01-07
Wasn't it sometime during Ubuntu 9 that the upgraded x server and proprietary ati driver dropped support for the older cards?

I know they still work on hardy with ati prop driver. Whenever ati catalyst >= 9.4 became standard. I can't remember what version of x it corresponds to.

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

Posted 05/09 right after 9.04 was released. So 9.04 should still work with Catalyst < 9.4 well a fresh install at least as long as you don't upgrade the x server. 

Perhaps he was using the ati prop driver with that card the last time it worked.

---

### Post by Yellow Pasque on 2011-01-08
> **tjones00 said:**
> Wasn't it sometime during Ubuntu 9 that the upgraded x server and proprietary ati driver dropped support for the older cards?

ATI dropped proprietary support for this card long before they dropped support for the lot of cards you're thinking of.

---

