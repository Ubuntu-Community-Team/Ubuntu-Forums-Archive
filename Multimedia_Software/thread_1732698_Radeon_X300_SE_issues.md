---
title: "Radeon X300 SE issues"
date: 2011-04-18
forum: Multimedia Software
---

### Post by Drakmor on 2011-04-18
So, I've recently set up kubuntu 10.10 on my parents' computer and its working pretty well. They love the speed and applications, but the graphics are having issues. I somehow missed that there was an ATI card in the computer, which explained why I needed to turn off desktop effects. Also, when I try to run a program using 3D graphics, it crashed after a couple of minutes. I tried some new drivers, and got an issue like this:
[http://flic.kr/p/9zBBwT](http://flic.kr/p/9zBBwT)

When I reverted it back to how it previously was (or at least close), the screen was fixed but any program using 3d graphics wouldn't run at all. Now, I've tried to fix it by using the instructions from these pages:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

[http://ubuntuforums.org/showthread.php?t=777318](http://ubuntuforums.org/showthread.php?t=777318)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

But I ended up with a 300xsomething screen in recovery mode. I removed the xorg drivers and reinstalled the fglrx ones (which I'm pretty sure is what was there in the first place) and the screen works now, but any 3d (openGL?) applications give me
 ```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14

```
Also, if I use fglrxinfo I get a "segmentation fault," and jockey doesn't detect that I'm using proprietary drivers.

Anyone know how to fix this?

---

### Post by Yellow Pasque on 2011-04-18
fglrx/Catalyst is not the original driver and hasn't supported the chip in the past two years. Remove it and reinstall open-source driver: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

That should get basic 3D working again. Better 3D performance can be had with newer X drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Drakmor on 2011-04-18
One of the pages I mentioned gave me the same thing as the maverick update thing you linked to, but it didn't work. I've tried xorg-edgers as well, and I'm pretty sure I got the same results. I'll try later today though.

---

### Post by Yellow Pasque on 2011-04-18
If it still doesn't work, then post your /var/log/Xorg.0.log

---

### Post by Drakmor on 2011-04-18
Okay, when I got home today something had happened after a shutdown. and it kept booting into recovery mode. I just installed                 xserver-xorg-video-ati from xorg-edgers, so I'll see if that works.

Update: Neither -ati or -radeon works... I'll try the stable ones.

In the meantime, my xorg.0.log:
```
[    14.666] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[    14.677] X Protocol Version 11, Revision 0
[    14.677] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    14.677] Current Operating System: Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[    14.677] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=87409393-5fcc-45bd-ac4a-c9a7ccd0e1c3 ro quiet splash
[    14.677] Build Date: 29 November 2010  03:29:38PM
[    14.677] xorg-server 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick (For technical support please see http://www.ubuntu.com/support) 
[    14.677] Current version of pixman: 0.21.4
[    14.677] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.677] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.677] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 18 22:46:00 2011
[    14.696] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.697] (==) No Layout section.  Using the first Screen section.
[    14.697] (==) No screen section available. Using defaults.
[    14.697] (**) |-->Screen "Default Screen Section" (0)
[    14.697] (**) |   |-->Monitor "<default monitor>"
[    14.697] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.697] (==) Automatically adding devices
[    14.697] (==) Automatically enabling devices
[    14.697] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.697] 	Entry deleted from font path.
[    14.697] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.697] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.697] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.697] (II) Loader magic: 0x81fa7c0
[    14.697] (II) Module ABI versions:
[    14.697] 	X.Org ANSI C Emulation: 0.4
[    14.697] 	X.Org Video Driver: 8.0
[    14.697] 	X.Org XInput driver : 11.0
[    14.697] 	X.Org Server Extension : 4.0
[    14.699] (--) PCI:*(0:1:0:0) 1002:5b60:1002:0602 rev 0, Mem @ 0xec000000/33554432, 0xefde0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
[    14.699] (--) PCI: (0:1:0:1) 1002:5b70:1002:0603 rev 0, Mem @ 0xefdf0000/65536
[    14.699] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.699] (II) LoadModule: "extmod"
[    14.714] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.714] (II) Module extmod: vendor="X.Org Foundation"
[    14.714] 	compiled for 1.9.2.901, module version = 1.0.0
[    14.715] 	Module class: X.Org Server Extension
[    14.715] 	ABI class: X.Org Server Extension, version 4.0
[    14.715] (II) Loading extension MIT-SCREEN-SAVER
[    14.715] (II) Loading extension XFree86-VidModeExtension
[    14.715] (II) Loading extension XFree86-DGA
[    14.715] (II) Loading extension DPMS
[    14.715] (II) Loading extension XVideo
[    14.715] (II) Loading extension XVideo-MotionCompensation
[    14.715] (II) Loading extension X-Resource
[    14.715] (II) LoadModule: "dbe"
[    14.715] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.715] (II) Module dbe: vendor="X.Org Foundation"
[    14.715] 	compiled for 1.9.2.901, module version = 1.0.0
[    14.715] 	Module class: X.Org Server Extension
[    14.715] 	ABI class: X.Org Server Extension, version 4.0
[    14.715] (II) Loading extension DOUBLE-BUFFER
[    14.715] (II) LoadModule: "glx"
[    14.716] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.716] (II) Module glx: vendor="X.Org Foundation"
[    14.716] 	compiled for 1.9.2.901, module version = 1.0.0
[    14.716] 	ABI class: X.Org Server Extension, version 4.0
[    14.716] (==) AIGLX enabled
[    14.716] (II) Loading extension GLX
[    14.716] (II) LoadModule: "record"
[    14.717] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.717] (II) Module record: vendor="X.Org Foundation"
[    14.717] 	compiled for 1.9.2.901, module version = 1.13.0
[    14.717] 	Module class: X.Org Server Extension
[    14.717] 	ABI class: X.Org Server Extension, version 4.0
[    14.717] (II) Loading extension RECORD
[    14.717] (II) LoadModule: "dri"
[    14.718] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.718] (II) Module dri: vendor="X.Org Foundation"
[    14.718] 	compiled for 1.9.2.901, module version = 1.0.0
[    14.718] 	ABI class: X.Org Server Extension, version 4.0
[    14.718] (II) Loading extension XFree86-DRI
[    14.718] (II) LoadModule: "dri2"
[    14.719] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.719] (II) Module dri2: vendor="X.Org Foundation"
[    14.719] 	compiled for 1.9.2.901, module version = 1.2.0
[    14.719] 	ABI class: X.Org Server Extension, version 4.0
[    14.719] (II) Loading extension DRI2
[    14.719] (==) Matched fglrx as autoconfigured driver 0
[    14.719] (==) Matched ati as autoconfigured driver 1
[    14.719] (==) Matched vesa as autoconfigured driver 2
[    14.719] (==) Matched fbdev as autoconfigured driver 3
[    14.719] (==) Assigned the driver to the xf86ConfigLayout
[    14.719] (II) LoadModule: "fglrx"
[    14.720] (WW) Warning, couldn't open module fglrx
[    14.721] (II) UnloadModule: "fglrx"
[    14.721] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    14.721] (II) LoadModule: "ati"
[    14.721] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    14.722] (II) Module ati: vendor="X.Org Foundation"
[    14.722] 	compiled for 1.9.2.901, module version = 6.14.99
[    14.722] 	Module class: X.Org Video Driver
[    14.722] 	ABI class: X.Org Video Driver, version 8.0
[    14.722] (II) LoadModule: "radeon"
[    14.722] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.723] (II) Module radeon: vendor="X.Org Foundation"
[    14.723] 	compiled for 1.9.2.901, module version = 6.14.99
[    14.723] 	Module class: X.Org Video Driver
[    14.723] 	ABI class: X.Org Video Driver, version 8.0
[    14.723] (II) LoadModule: "vesa"
[    14.723] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.723] (II) Module vesa: vendor="X.Org Foundation"
[    14.723] 	compiled for 1.9.2.901, module version = 2.3.0
[    14.723] 	Module class: X.Org Video Driver
[    14.723] 	ABI class: X.Org Video Driver, version 8.0
[    14.723] (II) LoadModule: "fbdev"
[    14.724] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.724] (II) Module fbdev: vendor="X.Org Foundation"
[    14.724] 	compiled for 1.8.99.904, module version = 0.4.2
[    14.724] 	ABI class: X.Org Video Driver, version 8.0
[    14.724] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS
[    14.733] (II) VESA: driver for VESA chipsets: vesa
[    14.733] (II) FBDEV: driver for framebuffer: fbdev
[    14.733] (++) using VT number 7

[    14.733] (II) [KMS] Kernel modesetting enabled.
[    14.733] (WW) Falling back to old probe method for vesa
[    14.733] (WW) Falling back to old probe method for fbdev
[    14.733] (II) Loading sub module "fbdevhw"
[    14.733] (II) LoadModule: "fbdevhw"
[    14.734] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.734] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.734] 	compiled for 1.9.2.901, module version = 0.0.2
[    14.734] 	ABI class: X.Org Video Driver, version 8.0
[    14.734] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.734] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    14.734] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.734] (==) RADEON(0): Default visual is TrueColor
[    14.734] (==) RADEON(0): RGB weight 888
[    14.734] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    14.734] (--) RADEON(0): Chipset: "ATI Radeon X300 (RV370) 5B60 (PCIE)" (ChipID = 0x5b60)
[    14.734] (II) RADEON(0): PCIE card detected
[    14.734] drmOpenDevice: node name is /dev/dri/card0
[    14.734] drmOpenDevice: open result is 9, (OK)
[    14.734] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    14.734] drmOpenDevice: node name is /dev/dri/card0
[    14.735] drmOpenDevice: open result is 9, (OK)
[    14.735] drmOpenByBusid: drmOpenMinor returns 9
[    14.735] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    14.735] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    14.735] (II) Loading sub module "exa"
[    14.735] (II) LoadModule: "exa"
[    14.735] (II) Loading /usr/lib/xorg/modules/libexa.so
[    14.735] (II) Module exa: vendor="X.Org Foundation"
[    14.735] 	compiled for 1.9.2.901, module version = 2.5.0
[    14.735] 	ABI class: X.Org Video Driver, version 8.0
[    14.735] (II) RADEON(0): KMS Color Tiling: enabled
[    14.735] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    14.791] (II) RADEON(0): Output VGA-0 has no monitor section
[    14.847] (II) RADEON(0): Output DVI-0 has no monitor section
[    14.857] (II) RADEON(0): Output S-video has no monitor section
[    14.913] (II) RADEON(0): EDID for output VGA-0
[    14.913] (II) RADEON(0): Manufacturer: DEL  Model: a06d  Serial#: 826688853
[    14.913] (II) RADEON(0): Year: 2010  Week: 50
[    14.913] (II) RADEON(0): EDID Version: 1.3
[    14.913] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    14.914] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    14.914] (II) RADEON(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    14.914] (II) RADEON(0): Gamma: 2.20
[    14.914] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    14.914] (II) RADEON(0): First detailed timing is preferred mode
[    14.914] (II) RADEON(0): redX: 0.631 redY: 0.351   greenX: 0.334 greenY: 0.620
[    14.914] (II) RADEON(0): blueX: 0.156 blueY: 0.051   whiteX: 0.313 whiteY: 0.328
[    14.914] (II) RADEON(0): Supported established timings:
[    14.914] (II) RADEON(0): 720x400@70Hz
[    14.914] (II) RADEON(0): 640x480@60Hz
[    14.914] (II) RADEON(0): 640x480@75Hz
[    14.914] (II) RADEON(0): 800x600@60Hz
[    14.914] (II) RADEON(0): 800x600@75Hz
[    14.914] (II) RADEON(0): 1024x768@60Hz
[    14.914] (II) RADEON(0): 1024x768@75Hz
[    14.914] (II) RADEON(0): 1280x1024@75Hz
[    14.914] (II) RADEON(0): Manufacturer's mask: 0
[    14.914] (II) RADEON(0): Supported standard timings:
[    14.914] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    14.914] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    14.914] (II) RADEON(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    14.914] (II) RADEON(0): Supported detailed timing:
[    14.914] (II) RADEON(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    14.914] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    14.914] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    14.914] (II) RADEON(0): Serial No: F8NDP0C91FEU
[    14.914] (II) RADEON(0): Monitor name: DELL P2411H
[    14.914] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    14.914] (II) RADEON(0): EDID (in hex):
[    14.914] (II) RADEON(0): 	00ffffffffffff0010ac6da055454631
[    14.914] (II) RADEON(0): 	321401030e351e78eabb04a159559e28
[    14.914] (II) RADEON(0): 	0d5054a54b00714f8180d1c001010101
[    14.914] (II) RADEON(0): 	010101010101023a801871382d40582c
[    14.914] (II) RADEON(0): 	4500132b2100001e000000ff0046384e
[    14.914] (II) RADEON(0): 	4450304339314645550a000000fc0044
[    14.914] (II) RADEON(0): 	454c4c205032343131480a20000000fd
[    14.914] (II) RADEON(0): 	00384c1e5311000a2020202020200064
[    14.914] (II) RADEON(0): EDID vendor "DEL", prod id 41069
[    14.914] (II) RADEON(0): Using EDID range info for horizontal sync
[    14.914] (II) RADEON(0): Using EDID range info for vertical refresh
[    14.914] (II) RADEON(0): Printing DDC gathered Modelines:
[    14.915] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    14.915] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.915] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.915] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.915] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.915] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.915] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.915] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.915] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.915] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.915] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.915] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    14.915] (II) RADEON(0): Printing probed modes for output VGA-0
[    14.915] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    14.915] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.915] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.915] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.915] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    14.915] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.915] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.915] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.915] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.915] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.915] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.972] (II) RADEON(0): EDID for output DVI-0
[    14.972] (II) RADEON(0): Manufacturer: DEL  Model: 4005  Serial#: 1095120180
[    14.972] (II) RADEON(0): Year: 2005  Week: 39
[    14.972] (II) RADEON(0): EDID Version: 1.3
[    14.972] (II) RADEON(0): Digital Display Input
[    14.972] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    14.972] (II) RADEON(0): Gamma: 2.20
[    14.972] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    14.972] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.972] (II) RADEON(0): Default color space is primary color space
[    14.972] (II) RADEON(0): First detailed timing is preferred mode
[    14.972] (II) RADEON(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
[    14.972] (II) RADEON(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
[    14.972] (II) RADEON(0): Supported established timings:
[    14.972] (II) RADEON(0): 720x400@70Hz
[    14.972] (II) RADEON(0): 640x480@60Hz
[    14.972] (II) RADEON(0): 640x480@75Hz
[    14.972] (II) RADEON(0): 800x600@60Hz
[    14.972] (II) RADEON(0): 800x600@75Hz
[    14.972] (II) RADEON(0): 1024x768@60Hz
[    14.972] (II) RADEON(0): 1024x768@75Hz
[    14.972] (II) RADEON(0): 1280x1024@75Hz
[    14.972] (II) RADEON(0): Manufacturer's mask: 0
[    14.972] (II) RADEON(0): Supported standard timings:
[    14.972] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    14.972] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    14.973] (II) RADEON(0): Supported detailed timing:
[    14.973] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    14.973] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    14.973] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    14.973] (II) RADEON(0): Serial No: Y429959LAF54
[    14.973] (II) RADEON(0): Monitor name: DELL 1704FPT
[    14.973] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    14.973] (II) RADEON(0): EDID (in hex):
[    14.973] (II) RADEON(0): 	00ffffffffffff0010ac054034354641
[    14.973] (II) RADEON(0): 	270f010380221b78eeaea5a6544c9926
[    14.973] (II) RADEON(0): 	145054a54b00714f8180010101010101
[    14.973] (II) RADEON(0): 	010101010101302a009851002a403070
[    14.973] (II) RADEON(0): 	1300520e1100001e000000ff00593432
[    14.973] (II) RADEON(0): 	393935394c414635340a000000fc0044
[    14.973] (II) RADEON(0): 	454c4c20313730344650540a000000fd
[    14.973] (II) RADEON(0): 	00384c1e510e000a2020202020200053
[    14.973] (II) RADEON(0): Printing probed modes for output DVI-0
[    14.973] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.973] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.973] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.973] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    14.973] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.973] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.973] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.973] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.973] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.973] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.983] (II) RADEON(0): EDID for output S-video
[    14.983] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    14.983] (II) RADEON(0): Not using default mode "320x175" (vrefresh out of range)
[    14.983] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    14.983] (II) RADEON(0): Not using default mode "320x200" (vrefresh out of range)
[    14.983] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    14.983] (II) RADEON(0): Not using default mode "360x200" (vrefresh out of range)
[    14.983] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "400x300" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1024x768i" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "512x384i" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "512x384" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x480" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x512" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    14.984] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "896x672" (hsync out of range)
[    14.984] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "896x672" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "928x696" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "928x696" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "960x720" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "416x312" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "576x432" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1360x768" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "680x384" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1360x768" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "680x384" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "700x525" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "720x450" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "800x512" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    14.985] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "960x540" (hsync out of range)
[    14.985] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    14.986] (II) RADEON(0): Not using default mode "960x600" (hsync out of range)
[    14.986] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    14.986] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    14.986] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    14.986] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    14.986] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    14.986] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.986] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    14.986] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.986] (II) RADEON(0): Printing probed modes for output S-video
[    14.986] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    14.986] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.986] (II) RADEON(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    14.986] (II) RADEON(0): Output VGA-0 connected
[    14.986] (II) RADEON(0): Output DVI-0 connected
[    14.986] (II) RADEON(0): Output S-video connected
[    14.986] (II) RADEON(0): Using exact sizes for initial modes
[    14.986] (II) RADEON(0): Output VGA-0 using initial mode 800x600
[    14.986] (II) RADEON(0): Output DVI-0 using initial mode 800x600
[    14.986] (II) RADEON(0): Output S-video using initial mode 800x600
[    14.986] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.986] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:2000000 visible:1e80000
[    14.986] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    14.986] (**) RADEON(0): Display dimensions: (530, 300) mm
[    14.986] (**) RADEON(0): DPI set to (38, 50)
[    14.986] (II) Loading sub module "fb"
[    14.986] (II) LoadModule: "fb"
[    14.987] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.987] (II) Module fb: vendor="X.Org Foundation"
[    14.987] 	compiled for 1.9.2.901, module version = 1.0.0
[    14.987] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.987] (II) Loading sub module "ramdac"
[    14.987] (II) LoadModule: "ramdac"
[    14.987] (II) Module "ramdac" already built-in
[    14.987] (II) UnloadModule: "vesa"
[    14.987] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.987] (II) UnloadModule: "fbdev"
[    14.987] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.987] (II) UnloadModule: "fbdevhw"
[    14.987] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    14.987] (--) Depth 24 pixmap format is 32 bpp
[    14.987] (II) RADEON(0): [DRI2] Setup complete
[    14.987] (II) RADEON(0): [DRI2]   DRI driver: r300
[    14.988] (II) RADEON(0): Front buffer size: 1976K
[    14.988] (II) RADEON(0): VRAM usage limit set to 26330K
[    14.988] (==) RADEON(0): Backing store disabled
[    14.988] (II) RADEON(0): Direct rendering enabled
[    14.988] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    14.988] (II) RADEON(0): Setting EXA maxPitchBytes
[    14.988] (II) EXA(0): Driver allocated offscreen pixmaps
[    14.988] (II) EXA(0): Driver registered support for the following operations:
[    14.988] (II)         Solid
[    14.988] (II)         Copy
[    14.988] (II)         Composite (RENDER acceleration)
[    14.988] (II)         UploadToScreen
[    14.988] (II)         DownloadFromScreen
[    14.988] (II) RADEON(0): Acceleration enabled
[    14.988] (==) RADEON(0): DPMS enabled
[    14.988] (==) RADEON(0): Silken mouse enabled
[    14.988] (II) RADEON(0): Set up textured video
[    14.988] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.135] (--) RandR disabled
[    15.135] (II) Initializing built-in extension Generic Event Extension
[    15.135] (II) Initializing built-in extension SHAPE
[    15.135] (II) Initializing built-in extension MIT-SHM
[    15.135] (II) Initializing built-in extension XInputExtension
[    15.135] (II) Initializing built-in extension XTEST
[    15.136] (II) Initializing built-in extension BIG-REQUESTS
[    15.136] (II) Initializing built-in extension SYNC
[    15.136] (II) Initializing built-in extension XKEYBOARD
[    15.136] (II) Initializing built-in extension XC-MISC
[    15.136] (II) Initializing built-in extension SECURITY
[    15.136] (II) Initializing built-in extension XINERAMA
[    15.136] (II) Initializing built-in extension XFIXES
[    15.136] (II) Initializing built-in extension RENDER
[    15.136] (II) Initializing built-in extension RANDR
[    15.136] (II) Initializing built-in extension COMPOSITE
[    15.136] (II) Initializing built-in extension DAMAGE
[    15.136] (II) Initializing built-in extension GESTURE
[    15.160] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    15.160] (II) AIGLX: enabled GLX_INTEL_swap_event
[    15.160] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    15.160] (II) AIGLX: enabled GLX_SGI_make_current_read
[    15.160] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    15.160] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    15.160] (II) GLX: Initialized DRI2 GL provider for screen 0
[    15.211] (II) RADEON(0): Setting screen physical size to 211 x 158
[    15.256] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.268] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.268] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.268] (II) LoadModule: "evdev"
[    15.268] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.269] (II) Module evdev: vendor="X.Org Foundation"
[    15.269] 	compiled for 1.9.2.901, module version = 2.5.99
[    15.269] 	Module class: X.Org XInput Driver
[    15.269] 	ABI class: X.Org XInput driver, version 11.0
[    15.269] (**) Power Button: always reports core events
[    15.269] (**) Power Button: Device: "/dev/input/event1"
[    15.280] (--) Power Button: Found keys
[    15.280] (II) Power Button: Configuring as keyboard
[    15.280] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.280] (**) Option "xkb_rules" "evdev"
[    15.280] (**) Option "xkb_model" "pc105"
[    15.280] (**) Option "xkb_layout" "us"
[    15.281] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.281] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.281] (**) Power Button: always reports core events
[    15.281] (**) Power Button: Device: "/dev/input/event0"
[    15.292] (--) Power Button: Found keys
[    15.292] (II) Power Button: Configuring as keyboard
[    15.292] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.292] (**) Option "xkb_rules" "evdev"
[    15.292] (**) Option "xkb_model" "pc105"
[    15.292] (**) Option "xkb_layout" "us"
[    15.293] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event10)
[    15.293] (II) No input driver/identifier specified (ignoring)
[    15.294] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event4)
[    15.294] (II) No input driver/identifier specified (ignoring)
[    15.294] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event5)
[    15.294] (II) No input driver/identifier specified (ignoring)
[    15.294] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event6)
[    15.294] (II) No input driver/identifier specified (ignoring)
[    15.295] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event7)
[    15.295] (II) No input driver/identifier specified (ignoring)
[    15.295] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
[    15.295] (II) No input driver/identifier specified (ignoring)
[    15.296] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9)
[    15.296] (II) No input driver/identifier specified (ignoring)
[    15.297] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    15.297] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    15.297] (**) Dell Dell USB Keyboard: always reports core events
[    15.297] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    15.312] (--) Dell Dell USB Keyboard: Found keys
[    15.312] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    15.312] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    15.312] (**) Option "xkb_rules" "evdev"
[    15.312] (**) Option "xkb_model" "pc105"
[    15.312] (**) Option "xkb_layout" "us"
[    15.313] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event3)
[    15.313] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    15.313] (**) Logitech USB Trackball: always reports core events
[    15.313] (**) Logitech USB Trackball: Device: "/dev/input/event3"
[    15.332] (--) Logitech USB Trackball: Found 9 mouse buttons
[    15.332] (--) Logitech USB Trackball: Found relative axes
[    15.332] (--) Logitech USB Trackball: Found x and y relative axes
[    15.332] (II) Logitech USB Trackball: Configuring as mouse
[    15.332] (**) Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    15.332] (**) Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.332] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE)
[    15.332] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    15.332] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    15.332] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    15.332] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    15.332] (II) Logitech USB Trackball: initialized for relative axes.
[    15.333] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    15.333] (II) No input driver/identifier specified (ignoring)
[    21.828] (II) Power Button: Close
[    21.828] (II) UnloadModule: "evdev"
[    21.852] (II) Power Button: Close
[    21.852] (II) UnloadModule: "evdev"
[    21.876] (II) Dell Dell USB Keyboard: Close
[    21.876] (II) UnloadModule: "evdev"
[    21.900] (II) Logitech USB Trackball: Close
[    21.900] (II) UnloadModule: "evdev"
[    21.952]  ddxSigGiveUp: Closing log

```

---

