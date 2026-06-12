---
title: "ATI Video Driver no OpenGL 3D"
date: 2011-04-08
forum: Multimedia Software
---

### Post by ZigBlazer on 2011-04-08
I'm trying to run Sweet Home 3D, but it won't open.  I get a fatal error in 3D rendering system.  It says "please update the DirectX/OpenGL drivers of your computer graphics card".

ATI/AMD directs me to the IBM website to get the driver.  My Thinkpad uses a Radeon Xpress 200M video card.  I got the windows driver from there, but I don't know that it would work with Ubuntu 10.10.  I believe the video is controlled using KMS, but when I try and view the OpenGL info it appears not to be working.

Here is the info I get. 

zigblazer@Zigblazer-ThinkPad:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:17 memory:c0000000-cfffffff ioport:9000(size=256) memory:a0100000-a010ffff memory:a0120000-a013ffff

zigblazer@Zigblazer-ThinkPad:~$ dmesg | grep drm
[   18.260000] [drm] Initialized drm 1.1.0 20060810
[   18.885734] [drm] radeon defaulting to kernel modesetting.
[   18.885742] [drm] radeon kernel modesetting enabled.
[   18.905010] [drm] initializing kernel modesetting (RS400 0x1002:0x5A62).
[   19.087739] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0

zigblazer@Zigblazer-ThinkPad:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I'm still new to Ubuntu and learning, so I need a little extra explination.

Anyone have any ideas where I go from here?  How do I fix the OpenGL or extension GLX missing thing?

---

### Post by Yellow Pasque on 2011-04-08
Run all 6 commands in this section: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
Then update vid drivers here: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
The r300g driver should bring you to OpenGL 2.1 support, though 3D might not be the fastest on Xpress200..

If you're wondering why Windows driver doesn't work, see big, red warning here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

---

### Post by ZigBlazer on 2011-04-08
Thank you very much.  I understood the windows driver wouldn't work, just couldn't find the right one.  Where do I go on that second page?  I don't know which package to download.

---

### Post by Yellow Pasque on 2011-04-08
You add the PPA to your sources, update your sources, and update packages:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by ZigBlazer on 2011-04-08
Ok. I got it done.  The program still doesn't work, and glxinfo still comes up blank.

I'm thinking that the 3D just isn't going to work with Ubuntu on this old laptop.

---

### Post by Yellow Pasque on 2011-04-08
You did restart, right? If so, post content of /var/log/Xorg.0.log

---

### Post by ZigBlazer on 2011-04-08
Yep, restarted after everything was done.

zigblazer@Zigblazer-ThinkPad:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
zigblazer@Zigblazer-ThinkPad:~$ sudo /var/log/Xorg.0.log
[sudo] password for zigblazer: 
sudo: /var/log/Xorg.0.log: command not found


Thanks again for the help.

---

### Post by ZigBlazer on 2011-04-08
Sorry I was kind of on autopilot.  Here is what was in the log.

[    21.156] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[    21.156] X Protocol Version 11, Revision 0
[    21.156] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    21.156] Current Operating System: Linux Zigblazer-ThinkPad 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686
[    21.156] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=a0eb5e4c-3c76-4456-b469-1b87bb1adadb ro quiet splash acpi_skip_timer_override
[    21.156] Build Date: 29 November 2010  03:29:38PM
[    21.156] xorg-server 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.156] Current version of pixman: 0.21.4
[    21.156]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    21.156] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.157] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr  8 20:17:47 2011
[    21.245] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.301] (==) No Layout section.  Using the first Screen section.
[    21.301] (==) No screen section available. Using defaults.
[    21.301] (**) |-->Screen "Default Screen Section" (0)
[    21.301] (**) |   |-->Monitor "<default monitor>"
[    21.302] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.302] (==) Automatically adding devices
[    21.302] (==) Automatically enabling devices
[    21.347] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.347]     Entry deleted from font path.
[    21.383] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.383] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.383] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.383] (II) Loader magic: 0x81fa7c0
[    21.383] (II) Module ABI versions:
[    21.383]     X.Org ANSI C Emulation: 0.4
[    21.383]     X.Org Video Driver: 8.0
[    21.383]     X.Org XInput driver : 11.0
[    21.383]     X.Org Server Extension : 4.0
[    21.385] (--) PCI:*(0:1:5:0) 1002:5a62:1014:059d rev 0, Mem @ 0xc0000000/268435456, 0xa0100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    21.385] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.385] (II) LoadModule: "extmod"
[    21.509] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.522] (II) Module extmod: vendor="X.Org Foundation"
[    21.522]     compiled for 1.9.2.901, module version = 1.0.0
[    21.522]     Module class: X.Org Server Extension
[    21.522]     ABI class: X.Org Server Extension, version 4.0
[    21.522] (II) Loading extension MIT-SCREEN-SAVER
[    21.522] (II) Loading extension XFree86-VidModeExtension
[    21.522] (II) Loading extension XFree86-DGA
[    21.522] (II) Loading extension DPMS
[    21.522] (II) Loading extension XVideo
[    21.522] (II) Loading extension XVideo-MotionCompensation
[    21.522] (II) Loading extension X-Resource
[    21.522] (II) LoadModule: "dbe"
[    21.522] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.525] (II) Module dbe: vendor="X.Org Foundation"
[    21.525]     compiled for 1.9.2.901, module version = 1.0.0
[    21.525]     Module class: X.Org Server Extension
[    21.525]     ABI class: X.Org Server Extension, version 4.0
[    21.525] (II) Loading extension DOUBLE-BUFFER
[    21.525] (II) LoadModule: "glx"
[    21.525] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    24.049] (II) Module glx: vendor="NVIDIA Corporation"
[    24.049]     compiled for 4.0.2, module version = 1.0.0
[    24.049]     Module class: X.Org Server Extension
[    24.049] (II) NVIDIA GLX Module  270.29  Wed Feb 23 16:34:38 PST 2011
[    24.049] (II) Loading extension GLX
[    24.049] (II) LoadModule: "record"
[    24.050] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.072] (II) Module record: vendor="X.Org Foundation"
[    24.072]     compiled for 1.9.2.901, module version = 1.13.0
[    24.072]     Module class: X.Org Server Extension
[    24.072]     ABI class: X.Org Server Extension, version 4.0
[    24.072] (II) Loading extension RECORD
[    24.072] (II) LoadModule: "dri"
[    24.073] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.091] (II) Module dri: vendor="X.Org Foundation"
[    24.091]     compiled for 1.9.2.901, module version = 1.0.0
[    24.091]     ABI class: X.Org Server Extension, version 4.0
[    24.091] (II) Loading extension XFree86-DRI
[    24.091] (II) LoadModule: "dri2"
[    24.091] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.100] (II) Module dri2: vendor="X.Org Foundation"
[    24.100]     compiled for 1.9.2.901, module version = 1.2.0
[    24.100]     ABI class: X.Org Server Extension, version 4.0
[    24.100] (II) Loading extension DRI2
[    24.100] (==) Matched fglrx as autoconfigured driver 0
[    24.100] (==) Matched ati as autoconfigured driver 1
[    24.100] (==) Matched vesa as autoconfigured driver 2
[    24.100] (==) Matched fbdev as autoconfigured driver 3
[    24.100] (==) Assigned the driver to the xf86ConfigLayout
[    24.100] (II) LoadModule: "fglrx"
[    24.131] (WW) Warning, couldn't open module fglrx
[    24.131] (II) UnloadModule: "fglrx"
[    24.131] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.131] (II) LoadModule: "ati"
[    24.132] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.143] (II) Module ati: vendor="X.Org Foundation"
[    24.143]     compiled for 1.9.2.901, module version = 6.14.99
[    24.143]     Module class: X.Org Video Driver
[    24.143]     ABI class: X.Org Video Driver, version 8.0
[    24.143] (II) LoadModule: "radeon"
[    24.143] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.221] (II) Module radeon: vendor="X.Org Foundation"
[    24.221]     compiled for 1.9.2.901, module version = 6.14.99
[    24.221]     Module class: X.Org Video Driver
[    24.221]     ABI class: X.Org Video Driver, version 8.0
[    24.229] (II) LoadModule: "vesa"
[    24.230] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.257] (II) Module vesa: vendor="X.Org Foundation"
[    24.257]     compiled for 1.9.2.901, module version = 2.3.0
[    24.257]     Module class: X.Org Video Driver
[    24.257]     ABI class: X.Org Video Driver, version 8.0
[    24.257] (II) LoadModule: "fbdev"
[    24.258] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.282] (II) Module fbdev: vendor="X.Org Foundation"
[    24.282]     compiled for 1.8.99.904, module version = 0.4.2
[    24.283]     ABI class: X.Org Video Driver, version 8.0
[    24.283] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    24.298] (II) VESA: driver for VESA chipsets: vesa
[    24.298] (II) FBDEV: driver for framebuffer: fbdev
[    24.298] (++) using VT number 7

[    24.298] (II) [KMS] Kernel modesetting enabled.
[    24.298] (WW) Falling back to old probe method for vesa
[    24.298] (WW) Falling back to old probe method for fbdev
[    24.298] (II) Loading sub module "fbdevhw"
[    24.298] (II) LoadModule: "fbdevhw"
[    24.299] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.315] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.315]     compiled for 1.9.2.901, module version = 0.0.2
[    24.315]     ABI class: X.Org Video Driver, version 8.0
[    24.317] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.317] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.317] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.317] (==) RADEON(0): Default visual is TrueColor
[    24.317] (==) RADEON(0): RGB weight 888
[    24.317] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.317] (--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5A62 (PCIE)" (ChipID = 0x5a62)
[    24.317] (II) RADEON(0): PCI card detected
[    24.317] drmOpenDevice: node name is /dev/dri/card0
[    24.317] drmOpenDevice: open result is 8, (OK)
[    24.317] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    24.317] drmOpenDevice: node name is /dev/dri/card0
[    24.317] drmOpenDevice: open result is 8, (OK)
[    24.317] drmOpenByBusid: drmOpenMinor returns 8
[    24.317] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    24.317] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    24.317] (II) Loading sub module "exa"
[    24.317] (II) LoadModule: "exa"
[    24.318] (II) Loading /usr/lib/xorg/modules/libexa.so
[    24.336] (II) Module exa: vendor="X.Org Foundation"
[    24.336]     compiled for 1.9.2.901, module version = 2.5.0
[    24.336]     ABI class: X.Org Video Driver, version 8.0
[    24.336] (II) RADEON(0): KMS Color Tiling: enabled
[    24.336] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    24.386] (II) RADEON(0): Output VGA-0 has no monitor section
[    24.387] (II) RADEON(0): Output LVDS has no monitor section
[    24.411] (II) RADEON(0): EDID for output VGA-0
[    24.411] (II) RADEON(0): EDID for output LVDS
[    24.412] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "320x175" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "320x200" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "360x200" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    24.412] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1024x768i" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "512x384i" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "640x480" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "640x512" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "800x600" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "896x672" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "896x672" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "928x696" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "928x696" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "960x720" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "416x312" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "576x432" (hsync out of range)
[    24.413] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    24.413] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    24.414] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "700x525" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "720x450" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "800x512" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "960x540" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "960x600" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    24.414] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    24.414] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    24.414] (II) RADEON(0): Printing probed modes for output LVDS
[    24.414] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 770 776 806 (48.4 kHz)
[    24.414] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.414] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.414] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.414] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    24.415] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    24.415] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    24.415] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.415] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    24.415] (II) RADEON(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    24.415] (II) RADEON(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    24.415] (II) RADEON(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    24.415] (II) RADEON(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    24.415] (II) RADEON(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    24.415] (II) RADEON(0): Output VGA-0 disconnected
[    24.415] (II) RADEON(0): Output LVDS connected
[    24.415] (II) RADEON(0): Using exact sizes for initial modes
[    24.415] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    24.415] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.415] (II) RADEON(0): mem size init: gart size :1dff000 vram size: s:8000000 visible:7cc0000
[    24.415] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    24.415] (==) RADEON(0): DPI set to (96, 96)
[    24.415] (II) Loading sub module "fb"
[    24.415] (II) LoadModule: "fb"
[    24.416] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.466] (II) Module fb: vendor="X.Org Foundation"
[    24.466]     compiled for 1.9.2.901, module version = 1.0.0
[    24.466]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.466] (II) Loading sub module "ramdac"
[    24.466] (II) LoadModule: "ramdac"
[    24.466] (II) Module "ramdac" already built-in
[    24.466] (II) UnloadModule: "vesa"
[    24.466] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.466] (II) UnloadModule: "fbdev"
[    24.466] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.466] (II) UnloadModule: "fbdevhw"
[    24.466] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    24.466] (--) Depth 24 pixmap format is 32 bpp
[    24.467] (II) RADEON(0): [DRI2] Setup complete
[    24.467] (II) RADEON(0): [DRI2]   DRI driver: r300
[    24.467] (II) RADEON(0): Front buffer size: 3072K
[    24.467] (II) RADEON(0): VRAM usage limit set to 112204K
[    24.552] (==) RADEON(0): Backing store disabled
[    24.567] (II) RADEON(0): Direct rendering enabled
[    24.681] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    24.681] (II) RADEON(0): Setting EXA maxPitchBytes
[    24.681] (II) EXA(0): Driver allocated offscreen pixmaps
[    24.681] (II) EXA(0): Driver registered support for the following operations:
[    24.681] (II)         Solid
[    24.681] (II)         Copy
[    24.681] (II)         Composite (RENDER acceleration)
[    24.681] (II)         UploadToScreen
[    24.681] (II)         DownloadFromScreen
[    24.681] (II) RADEON(0): Acceleration enabled
[    24.681] (==) RADEON(0): DPMS enabled
[    24.681] (==) RADEON(0): Silken mouse enabled
[    24.683] (II) RADEON(0): Set up textured video
[    24.684] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.684] (--) RandR disabled
[    24.684] (II) Initializing built-in extension Generic Event Extension
[    24.684] (II) Initializing built-in extension SHAPE
[    24.684] (II) Initializing built-in extension MIT-SHM
[    24.684] (II) Initializing built-in extension XInputExtension
[    24.684] (II) Initializing built-in extension XTEST
[    24.684] (II) Initializing built-in extension BIG-REQUESTS
[    24.684] (II) Initializing built-in extension SYNC
[    24.684] (II) Initializing built-in extension XKEYBOARD
[    24.684] (II) Initializing built-in extension XC-MISC
[    24.684] (II) Initializing built-in extension SECURITY
[    24.684] (II) Initializing built-in extension XINERAMA
[    24.684] (II) Initializing built-in extension XFIXES
[    24.684] (II) Initializing built-in extension RENDER
[    24.684] (II) Initializing built-in extension RANDR
[    24.684] (II) Initializing built-in extension COMPOSITE
[    24.684] (II) Initializing built-in extension DAMAGE
[    24.684] (II) Initializing built-in extension GESTURE
[    24.713] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    24.735] (II) RADEON(0): Setting screen physical size to 270 x 203
[    25.217] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.240] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    25.240] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.240] (II) LoadModule: "evdev"
[    25.241] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.368] (II) Module evdev: vendor="X.Org Foundation"
[    25.368]     compiled for 1.9.2.901, module version = 2.5.99
[    25.368]     Module class: X.Org XInput Driver
[    25.368]     ABI class: X.Org XInput driver, version 11.0
[    25.368] (**) Power Button: always reports core events
[    25.368] (**) Power Button: Device: "/dev/input/event2"
[    25.368] (--) Power Button: Found keys
[    25.368] (II) Power Button: Configuring as keyboard
[    25.368] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.369] (**) Option "xkb_rules" "evdev"
[    25.369] (**) Option "xkb_model" "pc105"
[    25.369] (**) Option "xkb_layout" "us"
[    25.371] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    25.371] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.371] (**) Video Bus: always reports core events
[    25.371] (**) Video Bus: Device: "/dev/input/event6"
[    25.371] (--) Video Bus: Found keys
[    25.371] (II) Video Bus: Configuring as keyboard
[    25.371] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.371] (**) Option "xkb_rules" "evdev"
[    25.371] (**) Option "xkb_model" "pc105"
[    25.371] (**) Option "xkb_layout" "us"
[    25.372] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.372] (II) No input driver/identifier specified (ignoring)
[    25.373] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    25.373] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.373] (**) Sleep Button: always reports core events
[    25.373] (**) Sleep Button: Device: "/dev/input/event1"
[    25.373] (--) Sleep Button: Found keys
[    25.373] (II) Sleep Button: Configuring as keyboard
[    25.373] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.373] (**) Option "xkb_rules" "evdev"
[    25.373] (**) Option "xkb_model" "pc105"
[    25.373] (**) Option "xkb_layout" "us"
[    25.375] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    25.375] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    25.375] (**) Logitech USB Receiver: always reports core events
[    25.375] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    25.375] (--) Logitech USB Receiver: Found keys
[    25.375] (II) Logitech USB Receiver: Configuring as keyboard
[    25.375] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    25.375] (**) Option "xkb_rules" "evdev"
[    25.376] (**) Option "xkb_model" "pc105"
[    25.376] (**) Option "xkb_layout" "us"
[    25.377] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    25.377] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    25.377] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    25.377] (**) Logitech USB Receiver: always reports core events
[    25.377] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    25.377] (--) Logitech USB Receiver: Found 12 mouse buttons
[    25.377] (--) Logitech USB Receiver: Found scroll wheel(s)
[    25.377] (--) Logitech USB Receiver: Found relative axes
[    25.377] (--) Logitech USB Receiver: Found x and y relative axes
[    25.377] (--) Logitech USB Receiver: Found absolute axes
[    25.377] (--) Logitech USB Receiver: Found keys
[    25.377] (II) Logitech USB Receiver: Configuring as mouse
[    25.377] (II) Logitech USB Receiver: Configuring as keyboard
[    25.377] (II) Logitech USB Receiver: Adding scrollwheel support
[    25.377] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    25.377] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.377] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    25.377] (**) Option "xkb_rules" "evdev"
[    25.377] (**) Option "xkb_model" "pc105"
[    25.377] (**) Option "xkb_layout" "us"
[    25.378] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    25.378] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    25.378] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    25.378] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    25.378] (II) Logitech USB Receiver: initialized for relative axes.
[    25.378] (WW) Logitech USB Receiver: ignoring absolute axes.
[    25.378] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    25.378] (II) No input driver/identifier specified (ignoring)
[    25.384] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.384] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.384] (**) AT Translated Set 2 keyboard: always reports core events
[    25.384] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.384] (--) AT Translated Set 2 keyboard: Found keys
[    25.384] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.384] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.384] (**) Option "xkb_rules" "evdev"
[    25.384] (**) Option "xkb_model" "pc105"
[    25.384] (**) Option "xkb_layout" "us"
[    25.387] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[    25.387] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    25.387] (**) TPPS/2 IBM TrackPoint: always reports core events
[    25.387] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[    25.387] (--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    25.387] (--) TPPS/2 IBM TrackPoint: Found relative axes
[    25.387] (--) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    25.387] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    25.387] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    25.387] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.387] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    25.387] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    25.387] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    25.387] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    25.387] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    25.387] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    25.388] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    25.388] (II) No input driver/identifier specified (ignoring)
[    25.389] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event8)
[    25.390] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    25.390] (**) ThinkPad Extra Buttons: always reports core events
[    25.390] (**) ThinkPad Extra Buttons: Device: "/dev/input/event8"
[    25.390] (--) ThinkPad Extra Buttons: Found keys
[    25.390] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    25.390] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    25.390] (**) Option "xkb_rules" "evdev"
[    25.390] (**) Option "xkb_model" "pc105"
[    25.390] (**) Option "xkb_layout" "us"

---

### Post by Yellow Pasque on 2011-04-08
You installed the nvidia driver (it amazes me how many intel and ati users do this and I'd really like to figure out where they get this idea :\ ) and the fglrx driver. Anyway..
```
sudo apt-get remove --purge nvidia*
sudo sh /usr/share/ati/fglrx-uninstall.sh #don't worry if this command fails
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

---

### Post by ZigBlazer on 2011-04-09
Don't ask me how the nvidia driver got installed.  I don't remember using anything that said nvidia.

Anyway, that was it.  The program is working.  It also seems to have fixed a few other minor problems I was having.

Thank you again, excellent job.  It's good to know some people actually know what they are doing.

---

### Post by chkneater on 2011-04-27
I ran across this thread trying to diagnose my ATI RadeonHD4350 after I THOT I had everything fixed.  Sure enough I still had Nvidia modaliases hanging on that needed purging.  

Thanks for bringing this to my attention!!

---

### Post by toey on 2011-07-04
> **Temüjin said:**
> You installed the nvidia driver (it amazes me how many intel and ati users do this and I'd really like to figure out where they get this idea :\ ) and the fglrx driver. Anyway..
```
sudo apt-get remove --purge nvidia*
sudo sh /usr/share/ati/fglrx-uninstall.sh #don't worry if this command fails
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Temüjin you a hero! this was doin my head in...

---

### Post by Ant0n on 2011-07-11
This solved everything, you win several cups of Ubuntu :D

---

### Post by superkikim on 2012-01-12
FFS Why the hell are the damn NV drivers installed ?!? I wonder !

Anyway. I followed the proposed solution up there and it works. However, if I try to install again the ATI proprietary drivers (11.12) it fails again. VMWare Workstation 8 doesn't work because of OpenGL.

Therefore I quit on the damn ATI drivers. I don't use 3D anyway on this computer. It's for work. But that sucks. 

It has been years now that I try to use linux to replace Windows. But the damn multi-monitor thing is still the reason why I always end up coming back to windows. And that really sucks !

---

### Post by joemilx on 2012-02-28
Used your script to purge my Nvidia garbage when replacing video card with a Radeon HD 8650.  Worked like a champ!  Thanks.

---

