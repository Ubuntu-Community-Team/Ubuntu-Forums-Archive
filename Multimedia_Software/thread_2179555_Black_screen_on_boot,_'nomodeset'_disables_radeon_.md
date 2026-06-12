---
title: "Black screen on boot, 'nomodeset' disables radeon driver"
date: 2013-10-08
forum: Multimedia Software
---

### Post by Methodize on 2013-10-08
Hello,

    I have been trying to get my ati radeon hd 4650 card to work on boot up as it did when I inserted the liveCD.
    Currently, it's booting to a black screen after grub selection. I found that using the 'nomodeset' option with grub allows me to boot normally, but uses vesa drivers instead of the radeon driver that was previously used during install. Vesa drivers don't output my screens native resolution, so I would like to try and use the radeon drivers that were working perfectly.
    After looking at the Xorg.0.log log I found that the nomodeset option was forcing vesa instead of radeon. So what i would like to know is if there's another solution to the black screen it boots to when i choose to leave the 'quiet splash' option in place and boot normally.

I am running lubuntu 13.04.

Thank You.

---

### Post by Bashing-om on 2013-10-08
Methodize; Hi !

There is the utility "Additional Drivers", that will seek and install an appropriate driver.
I have not seen the desk top of a standard 13.04 install .. so these directions may not be accurate for location of the utility.
Maybe:
Launcher -> Software Sources -> menu in tool bar (top of screen) ->software sources ->(tab) Additional Drivers.
And install the recommended driver.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Methodize on 2013-10-08
Hello Bashing-om, thanks for your help.
The drivers I need are already installed in the system, I'm just trying to get around the issue of the black screen. I'm also wondering how it functions with the liveCD boot but not the regular boot.

I don't want to use 'nomodeset' in grub because it disables KMS and falls back to vesa driver.

---

### Post by Bashing-om on 2013-10-08
Methodize; Hey;

Boot with "nomeodset", install the recommended driver, remove the "nomodeset" option from the grub config file (with your favorite text editor) .. and I expect that you are set to go.
To see the results: Terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

[INDENT][INDENT]all good now ?
[/INDENT][/INDENT]

---

### Post by Methodize on 2013-10-08
ok this is odd, the normal boot with the standard 'splash quiet'  option woks only some of the time.
I tried the normal boot just to see if by chance something went right, and it booted with the right resolution for my monitor. I tried to repeat the process by just rebooting and the black screen was back!
unable to accept defeat i restarted a few times and on the 4th  or 5th one it worked.

It seems that perhaps the kernel is at some point booting things in the right order perhaps. I don't know too much about kernel related topics.

here is my Xorg.0.log file when my computer boots normally just incase it's any good:
```

[    17.736] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    17.736] X Protocol Version 11, Revision 0
[    17.736] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    17.736] Current Operating System: Linux Dim 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686
[    17.736] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=4e51ff8a-234d-4f51-b0bd-2011f75aeda8 ro quiet splash
[    17.736] Build Date: 17 April 2013  10:42:56PM
[    17.736] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    17.737] Current version of pixman: 0.28.2
[    17.737] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.737] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.737] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  8 19:38:34 2013
[    17.746] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.746] (==) No Layout section.  Using the first Screen section.
[    17.747] (==) No screen section available. Using defaults.
[    17.747] (**) |-->Screen "Default Screen Section" (0)
[    17.747] (**) |   |-->Monitor "<default monitor>"
[    17.747] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.747] (==) Automatically adding devices
[    17.747] (==) Automatically enabling devices
[    17.747] (==) Automatically adding GPU devices
[    17.747] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.747] 	Entry deleted from font path.
[    17.747] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	built-ins
[    17.747] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.747] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.747] (II) Loader magic: 0xb77f66a0
[    17.747] (II) Module ABI versions:
[    17.747] 	X.Org ANSI C Emulation: 0.4
[    17.747] 	X.Org Video Driver: 13.1
[    17.747] 	X.Org XInput driver : 18.0
[    17.747] 	X.Org Server Extension : 7.0
[    17.748] (II) config/udev: Adding drm device (/dev/dri/card0)
[    17.750] (--) PCI:*(0:1:0:0) 1002:9495:1092:0028 rev 0, Mem @ 0xe0000000/268435456, 0xfe9f0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[    17.750] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    17.750] Initializing built-in extension Generic Event Extension
[    17.750] Initializing built-in extension SHAPE
[    17.750] Initializing built-in extension MIT-SHM
[    17.751] Initializing built-in extension XInputExtension
[    17.751] Initializing built-in extension XTEST
[    17.751] Initializing built-in extension BIG-REQUESTS
[    17.751] Initializing built-in extension SYNC
[    17.751] Initializing built-in extension XKEYBOARD
[    17.751] Initializing built-in extension XC-MISC
[    17.751] Initializing built-in extension SECURITY
[    17.751] Initializing built-in extension XINERAMA
[    17.751] Initializing built-in extension XFIXES
[    17.751] Initializing built-in extension RENDER
[    17.751] Initializing built-in extension RANDR
[    17.751] Initializing built-in extension COMPOSITE
[    17.751] Initializing built-in extension DAMAGE
[    17.751] Initializing built-in extension MIT-SCREEN-SAVER
[    17.751] Initializing built-in extension DOUBLE-BUFFER
[    17.751] Initializing built-in extension RECORD
[    17.751] Initializing built-in extension DPMS
[    17.751] Initializing built-in extension X-Resource
[    17.751] Initializing built-in extension XVideo
[    17.751] Initializing built-in extension XVideo-MotionCompensation
[    17.751] Initializing built-in extension SELinux
[    17.751] Initializing built-in extension XFree86-VidModeExtension
[    17.751] Initializing built-in extension XFree86-DGA
[    17.751] Initializing built-in extension XFree86-DRI
[    17.751] Initializing built-in extension DRI2
[    17.751] (II) LoadModule: "glx"
[    17.770] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.771] (II) Module glx: vendor="X.Org Foundation"
[    17.771] 	compiled for 1.13.3, module version = 1.0.0
[    17.771] 	ABI class: X.Org Server Extension, version 7.0
[    17.771] (==) AIGLX enabled
[    17.771] Loading extension GLX
[    17.771] (==) Matched fglrx as autoconfigured driver 0
[    17.771] (==) Matched ati as autoconfigured driver 1
[    17.771] (==) Matched fglrx as autoconfigured driver 2
[    17.771] (==) Matched ati as autoconfigured driver 3
[    17.771] (==) Matched vesa as autoconfigured driver 4
[    17.771] (==) Matched modesetting as autoconfigured driver 5
[    17.771] (==) Matched fbdev as autoconfigured driver 6
[    17.771] (==) Assigned the driver to the xf86ConfigLayout
[    17.771] (II) LoadModule: "fglrx"
[    17.772] (WW) Warning, couldn't open module fglrx
[    17.772] (II) UnloadModule: "fglrx"
[    17.772] (II) Unloading fglrx
[    17.772] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.772] (II) LoadModule: "ati"
[    17.773] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.773] (II) Module ati: vendor="X.Org Foundation"
[    17.773] 	compiled for 1.13.3, module version = 7.1.0
[    17.773] 	Module class: X.Org Video Driver
[    17.773] 	ABI class: X.Org Video Driver, version 13.1
[    17.773] (II) LoadModule: "radeon"
[    17.773] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.782] (II) Module radeon: vendor="X.Org Foundation"
[    17.782] 	compiled for 1.13.3, module version = 7.1.0
[    17.782] 	Module class: X.Org Video Driver
[    17.782] 	ABI class: X.Org Video Driver, version 13.1
[    17.782] (II) LoadModule: "vesa"
[    17.783] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.783] (II) Module vesa: vendor="X.Org Foundation"
[    17.783] 	compiled for 1.12.99.902, module version = 2.3.2
[    17.783] 	Module class: X.Org Video Driver
[    17.783] 	ABI class: X.Org Video Driver, version 13.0
[    17.783] (II) LoadModule: "modesetting"
[    17.783] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.784] (II) Module modesetting: vendor="X.Org Foundation"
[    17.784] 	compiled for 1.13.3, module version = 0.7.0
[    17.784] 	Module class: X.Org Video Driver
[    17.784] 	ABI class: X.Org Video Driver, version 13.1
[    17.784] (II) LoadModule: "fbdev"
[    17.784] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.784] (II) Module fbdev: vendor="X.Org Foundation"
[    17.784] 	compiled for 1.12.99.902, module version = 0.4.3
[    17.784] 	Module class: X.Org Video Driver
[    17.784] 	ABI class: X.Org Video Driver, version 13.0
[    17.784] (==) Matched fglrx as autoconfigured driver 0
[    17.784] (==) Matched ati as autoconfigured driver 1
[    17.784] (==) Matched fglrx as autoconfigured driver 2
[    17.784] (==) Matched ati as autoconfigured driver 3
[    17.785] (==) Matched vesa as autoconfigured driver 4
[    17.785] (==) Matched modesetting as autoconfigured driver 5
[    17.785] (==) Matched fbdev as autoconfigured driver 6
[    17.785] (==) Assigned the driver to the xf86ConfigLayout
[    17.785] (II) LoadModule: "fglrx"
[    17.786] (WW) Warning, couldn't open module fglrx
[    17.786] (II) UnloadModule: "fglrx"
[    17.786] (II) Unloading fglrx
[    17.786] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.786] (II) LoadModule: "ati"
[    17.786] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.786] (II) Module ati: vendor="X.Org Foundation"
[    17.786] 	compiled for 1.13.3, module version = 7.1.0
[    17.786] 	Module class: X.Org Video Driver
[    17.786] 	ABI class: X.Org Video Driver, version 13.1
[    17.786] (II) LoadModule: "vesa"
[    17.787] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.787] (II) Module vesa: vendor="X.Org Foundation"
[    17.787] 	compiled for 1.12.99.902, module version = 2.3.2
[    17.787] 	Module class: X.Org Video Driver
[    17.787] 	ABI class: X.Org Video Driver, version 13.0
[    17.787] (II) UnloadModule: "vesa"
[    17.787] (II) Unloading vesa
[    17.787] (II) Failed to load module "vesa" (already loaded, 0)
[    17.787] (II) LoadModule: "modesetting"
[    17.787] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.787] (II) Module modesetting: vendor="X.Org Foundation"
[    17.787] 	compiled for 1.13.3, module version = 0.7.0
[    17.787] 	Module class: X.Org Video Driver
[    17.787] 	ABI class: X.Org Video Driver, version 13.1
[    17.787] (II) UnloadModule: "modesetting"
[    17.787] (II) Unloading modesetting
[    17.787] (II) Failed to load module "modesetting" (already loaded, 0)
[    17.787] (II) LoadModule: "fbdev"
[    17.788] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.788] (II) Module fbdev: vendor="X.Org Foundation"
[    17.788] 	compiled for 1.12.99.902, module version = 0.4.3
[    17.788] 	Module class: X.Org Video Driver
[    17.788] 	ABI class: X.Org Video Driver, version 13.0
[    17.788] (II) UnloadModule: "fbdev"
[    17.788] (II) Unloading fbdev
[    17.788] (II) Failed to load module "fbdev" (already loaded, 0)
[    17.788] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
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
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[    17.801] (II) VESA: driver for VESA chipsets: vesa
[    17.801] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    17.801] (II) FBDEV: driver for framebuffer: fbdev
[    17.801] (++) using VT number 7

[    17.801] (II) [KMS] Kernel modesetting enabled.
[    17.801] (WW) Falling back to old probe method for vesa
[    17.801] (WW) Falling back to old probe method for modesetting
[    17.801] (WW) Falling back to old probe method for fbdev
[    17.801] (II) Loading sub module "fbdevhw"
[    17.801] (II) LoadModule: "fbdevhw"
[    17.802] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.802] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.802] 	compiled for 1.13.3, module version = 0.0.2
[    17.802] 	ABI class: X.Org Video Driver, version 13.1
[    17.802] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    17.802] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    17.802] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.802] (==) RADEON(0): Default visual is TrueColor
[    17.802] (==) RADEON(0): RGB weight 888
[    17.802] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.802] (--) RADEON(0): Chipset: "ATI Radeon HD 4600 Series" (ChipID = 0x9495)
[    17.802] (II) Loading sub module "dri2"
[    17.802] (II) LoadModule: "dri2"
[    17.802] (II) Module "dri2" already built-in
[    17.802] (II) Loading sub module "exa"
[    17.802] (II) LoadModule: "exa"
[    17.803] (II) Loading /usr/lib/xorg/modules/libexa.so
[    17.803] (II) Module exa: vendor="X.Org Foundation"
[    17.803] 	compiled for 1.13.3, module version = 2.6.0
[    17.803] 	ABI class: X.Org Video Driver, version 13.1
[    17.803] (II) RADEON(0): KMS Color Tiling: enabled
[    17.803] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    17.803] (II) RADEON(0): KMS Pageflipping: enabled
[    17.803] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    17.837] (II) RADEON(0): Output DVI-0 has no monitor section
[    17.860] (II) RADEON(0): Output DVI-1 has no monitor section
[    17.884] (II) RADEON(0): Output DIN has no monitor section
[    17.918] (II) RADEON(0): EDID for output DVI-0
[    17.918] (II) RADEON(0): Manufacturer: VSC  Model: 5f21  Serial#: 1253
[    17.918] (II) RADEON(0): Year: 2007  Week: 47
[    17.918] (II) RADEON(0): EDID Version: 1.3
[    17.918] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    17.918] (II) RADEON(0): Signal levels configurable
[    17.918] (II) RADEON(0): Sync:  Separate
[    17.918] (II) RADEON(0): Max Image Size [cm]: horiz.: 46  vert.: 29
[    17.918] (II) RADEON(0): Gamma: 2.20
[    17.918] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    17.918] (II) RADEON(0): First detailed timing is preferred mode
[    17.918] (II) RADEON(0): redX: 0.651 redY: 0.303   greenX: 0.267 greenY: 0.630
[    17.919] (II) RADEON(0): blueX: 0.145 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
[    17.919] (II) RADEON(0): Supported established timings:
[    17.919] (II) RADEON(0): 720x400@70Hz
[    17.919] (II) RADEON(0): 640x480@60Hz
[    17.919] (II) RADEON(0): 640x480@72Hz
[    17.919] (II) RADEON(0): 640x480@75Hz
[    17.919] (II) RADEON(0): 800x600@56Hz
[    17.919] (II) RADEON(0): 800x600@60Hz
[    17.919] (II) RADEON(0): 800x600@72Hz
[    17.919] (II) RADEON(0): 800x600@75Hz
[    17.919] (II) RADEON(0): 1024x768@60Hz
[    17.919] (II) RADEON(0): 1024x768@70Hz
[    17.919] (II) RADEON(0): 1024x768@75Hz
[    17.919] (II) RADEON(0): Manufacturer's mask: 0
[    17.919] (II) RADEON(0): Supported standard timings:
[    17.919] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    17.919] (II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    17.919] (II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    17.919] (II) RADEON(0): #3: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    17.919] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 75  vid: 3969
[    17.919] (II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    17.919] (II) RADEON(0): Supported detailed timing:
[    17.919] (II) RADEON(0): clock: 146.2 MHz   Image Size:  465 x 291 mm
[    17.919] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    17.919] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    17.919] (II) RADEON(0): Serial No: QY7074701253
[    17.919] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 155 MHz
[    17.919] (II) RADEON(0): Monitor name: Q2162WB
[    17.919] (II) RADEON(0): EDID (in hex):
[    17.919] (II) RADEON(0): 	00ffffffffffff005a63215fe5040000
[    17.919] (II) RADEON(0): 	2f110103182e1d782ae525a64d44a125
[    17.919] (II) RADEON(0): 	145054afce00b3009500950f8100810f
[    17.919] (II) RADEON(0): 	a9400101010121399030621a274068b0
[    17.919] (II) RADEON(0): 	3600d1231100001c000000ff00515937
[    17.919] (II) RADEON(0): 	3037343730313235330a000000fd0037
[    17.919] (II) RADEON(0): 	4b1e500f000a202020202020000000fc
[    17.919] (II) RADEON(0): 	00513231363257420a2020202020002d
[    17.919] (II) RADEON(0): Not using mode "1600x1200" (bad mode clock/interlace/doublescan)
[    17.919] (II) RADEON(0): Printing probed modes for output DVI-0
[    17.919] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    17.919] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    17.920] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    17.920] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    17.920] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[    17.920] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    17.920] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    17.920] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    17.920] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    17.920] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    17.920] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    17.920] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    17.920] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    17.920] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    17.920] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    17.920] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    17.944] (II) RADEON(0): EDID for output DVI-1
[    17.968] (II) RADEON(0): EDID for output DIN
[    17.968] (II) RADEON(0): Output DVI-0 connected
[    17.968] (II) RADEON(0): Output DVI-1 disconnected
[    17.968] (II) RADEON(0): Output DIN disconnected
[    17.968] (II) RADEON(0): Using exact sizes for initial modes
[    17.968] (II) RADEON(0): Output DVI-0 using initial mode 1680x1050
[    17.968] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.968] (II) RADEON(0): mem size init: gart size :fdef000 vram size: s:20000000 visible:1f8ca000
[    17.968] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    17.968] (==) RADEON(0): DPI set to (96, 96)
[    17.968] (II) Loading sub module "fb"
[    17.968] (II) LoadModule: "fb"
[    17.969] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.969] (II) Module fb: vendor="X.Org Foundation"
[    17.969] 	compiled for 1.13.3, module version = 1.0.0
[    17.969] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.969] (II) Loading sub module "ramdac"
[    17.969] (II) LoadModule: "ramdac"
[    17.969] (II) Module "ramdac" already built-in
[    17.969] (II) UnloadModule: "vesa"
[    17.969] (II) Unloading vesa
[    17.969] (II) UnloadModule: "modesetting"
[    17.969] (II) Unloading modesetting
[    17.969] (II) UnloadModule: "fbdev"
[    17.969] (II) Unloading fbdev
[    17.969] (II) UnloadSubModule: "fbdevhw"
[    17.969] (II) Unloading fbdevhw
[    17.969] (--) Depth 24 pixmap format is 32 bpp
[    17.969] (II) RADEON(0): [DRI2] Setup complete
[    17.969] (II) RADEON(0): [DRI2]   DRI driver: r600
[    17.969] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    17.970] (II) RADEON(0): Front buffer size: 7128K
[    17.970] (II) RADEON(0): VRAM usage limit set to 458769K
[    17.970] (==) RADEON(0): Backing store disabled
[    17.970] (II) RADEON(0): Direct rendering enabled
[    17.970] (II) EXA(0): Driver allocated offscreen pixmaps
[    17.970] (II) EXA(0): Driver registered support for the following operations:
[    17.970] (II)         Solid
[    17.970] (II)         Copy
[    17.970] (II)         Composite (RENDER acceleration)
[    17.970] (II)         UploadToScreen
[    17.970] (II)         DownloadFromScreen
[    17.970] (II) RADEON(0): Acceleration enabled
[    17.970] (==) RADEON(0): DPMS enabled
[    17.970] (==) RADEON(0): Silken mouse enabled
[    17.970] (II) RADEON(0): Set up textured video
[    17.970] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    17.970] (II) RADEON(0): [XvMC] Extension initialized.
[    17.970] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.172] (--) RandR disabled
[    18.210] (II) SELinux: Disabled on system
[    18.378] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.378] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.378] (II) AIGLX: enabled GLX_ARB_create_context
[    18.378] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    18.378] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    18.378] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.378] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.379] (II) AIGLX: Loaded and initialized r600
[    18.379] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.381] (II) RADEON(0): Setting screen physical size to 444 x 277
[    18.401] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.407] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.407] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.407] (II) LoadModule: "evdev"
[    18.407] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.414] (II) Module evdev: vendor="X.Org Foundation"
[    18.414] 	compiled for 1.13.3, module version = 2.7.3
[    18.414] 	Module class: X.Org XInput Driver
[    18.414] 	ABI class: X.Org XInput driver, version 18.0
[    18.414] (II) Using input driver 'evdev' for 'Power Button'
[    18.414] (**) Power Button: always reports core events
[    18.414] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.415] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.415] (--) evdev: Power Button: Found keys
[    18.415] (II) evdev: Power Button: Configuring as keyboard
[    18.415] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    18.415] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.415] (**) Option "xkb_rules" "evdev"
[    18.415] (**) Option "xkb_model" "pc105"
[    18.415] (**) Option "xkb_layout" "us"
[    18.416] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.416] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.416] (II) Using input driver 'evdev' for 'Power Button'
[    18.416] (**) Power Button: always reports core events
[    18.416] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.416] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.416] (--) evdev: Power Button: Found keys
[    18.416] (II) evdev: Power Button: Configuring as keyboard
[    18.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    18.416] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    18.416] (**) Option "xkb_rules" "evdev"
[    18.416] (**) Option "xkb_model" "pc105"
[    18.416] (**) Option "xkb_layout" "us"
[    18.417] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[    18.417] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    18.418] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event3)
[    18.418] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    18.418] (II) Using input driver 'evdev' for 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'
[    18.418] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    18.418] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event3"
[    18.418] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Vendor 0x45e Product 0x40
[    18.418] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    18.418] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    18.418] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    18.418] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    18.418] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    18.419] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    18.419] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    18.419] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.419] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    18.419] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 8)
[    18.419] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    18.419] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    18.419] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    18.419] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    18.419] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    18.420] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    18.420] (II) No input driver specified, ignoring this device.
[    18.420] (II) This device may have been added with another device file.
[    18.421] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    18.421] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.421] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.421] (**) AT Translated Set 2 keyboard: always reports core events
[    18.421] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    18.421] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.421] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.421] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.421] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    18.421] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    18.421] (**) Option "xkb_rules" "evdev"
[    18.421] (**) Option "xkb_model" "pc105"
[    18.421] (**) Option "xkb_layout" "us"
[    20.252] (II) RADEON(0): EDID vendor "VSC", prod id 24353
[    20.253] (II) RADEON(0): Using EDID range info for horizontal sync
[    20.253] (II) RADEON(0): Using EDID range info for vertical refresh
[    20.253] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.253] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    20.253] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    20.253] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    20.253] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    20.253] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    20.253] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    20.253] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    20.253] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    20.253] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    20.253] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    20.253] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    20.253] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    20.253] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    20.253] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    20.253] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    20.253] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    20.253] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    20.344] (II) RADEON(0): EDID vendor "VSC", prod id 24353
[    20.344] (II) RADEON(0): Using hsync ranges from config file
[    20.344] (II) RADEON(0): Using vrefresh ranges from config file
[    20.344] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.344] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    20.344] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    20.344] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    20.344] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    20.344] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    20.344] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    20.344] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    20.344] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    20.345] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    20.345] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    20.345] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    20.345] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    20.345] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    20.345] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    20.345] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    20.345] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    20.345] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)

```

And just now i kept track of the number of reboots between good boots and there are 3 black screened boots between every 1 good boot. could it be a kernel issue?

---

### Post by Bashing-om on 2013-10-09
Methodize; Hey.

I also run an ATI graphic card (older), and I see little difference between your Xorg file and mine that is working.
Now I am aware that there does exist in some instances race conditions, as to how to isolate this to a race condition, I presently do not know.
But let's do this and see if it does seem to point in that direction.
Boot to the grub menu, and in the boot line replace the term "quiet splash" with "text". - ctl+x to continue the boot process - You should now boot to a command line terminal interface.
Login -username and password -password has no response to the screen for security reasons. Terminal code:
```

sudo service lightdm start

```
Can you reliably start the GUI desktop each and every time (several attempts) ?
key combo ctl+alt+f1 returns to the tty1 terminal, ctl+alt+f7 back to the GUI.

At least this will give an idea as to what is not going on !

Edit: To shutdown the system from CLI:
```

sudo shutdown -P now ##Will power the system down and off immediately 
sudo shutdown -r now ##Will reboot the system, like right now !

```

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by Methodize on 2013-10-09
I tried using the 'text' option but it just went straight to the black screen again.  tty1 won't show either.
I'm afraid I might have to dive into trying to make sense of race conditions, and they seem like a whole other ballgame.

UPDATE:
I have found this bug that has been submitted some time ago and it seems to dive into this issue.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

---

### Post by Bashing-om on 2013-10-09
Methodize; Not Good !

As you can not boot to the tty1 console, That indicates to me either/or/and file system corruption/hard drive hardware problems/grub files not found.
If you can not boot to tty that rules out a lightdm problem in loading.
Let's try:
boot the liveDVD, as soon as the bios screen clears, depress and hold the shift key -> language screen, escape key to accept defaults -> boot options screen:
a) Boot from 1st hard disk - assumming ubuntu is installed on the sda drive - results in what ?
b) Check disk results in what ?
c) Try ubuntu mode, does ubuntu perform well in this environment ? 

Just try'n to narrow things down and point us in a direction.

[INDENT][INDENT]searching every which way
[/INDENT][/INDENT]

---

### Post by Methodize on 2013-10-09
I've pretty much a narrowed it down to what i believe to be race conditions within the kernel. Now i just have to look into that, any ideas?

---

