---
title: "No Display"
date: 2011-02-06
forum: Mythbuntu
---

### Post by TheMiz on 2011-02-06
I have this thread going on the myth-users list, but I am still searching for answers or advice:

I am having a major problem with a new TV I just purchased.  I cannot get the TV to display any video over the HDMI input unless there is audio playing as well.  When I have audio with it, the video switches on, and then it switches right back off when the audio ends.

The TV is an LG 37inch LED LCD TV with 1080p and 120 Hz refresh capable (model 37LE5300).

Things I have tried:
-Changing the resolution.
-Changing the configuration in the NVIDIA panel (although I'm not sure I know EXACTLY what I was doing in there).
-Changing my theme.
-Changing my HDMI cable to 1.3 compliant
-Changing the HDMI input jack
-Opening Mythtfrontend while a VLC window is playing (this is the closest to success I have come... I can see the desktop and enter mythtv, but once that VLC window closes, I get the "No Signal"message.
-Changing the Audio Output to the Stereo jack. (that will give me audio through the speakers I have set up, but no video - so it seems the HDMI detection is dependent on the sound)

Here is my Xorg log:
```
[    20.953] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.953] X Protocol Version 11, Revision 0
[    20.953] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    20.953] Current Operating System: Linux MythTV-Exercise 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    20.953] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=fc67910e-fcab-4bb4-93e5-d74269d81bd8 ro quiet splash
[    20.954] Build Date: 09 January 2011  12:14:58PM
[    20.954] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    20.954] Current version of pixman: 0.18.4
[    20.954] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.954] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.954] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  6 08:50:14 2011
[    20.955] (==) Using config file: "/etc/X11/xorg.conf"
[    20.955] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.964] (==) No Layout section.  Using the first Screen section.
[    20.964] (**) |-->Screen "Default Screen" (0)
[    20.965] (**) |   |-->Monitor "<default monitor>"
[    20.965] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    20.966] (**) |   |-->Device "Default Device"
[    20.966] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    20.966] (==) Automatically adding devices
[    20.966] (==) Automatically enabling devices
[    20.966] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.966] 	Entry deleted from font path.
[    20.967] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.967] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.967] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.967] (II) Loader magic: 0x81f9b00
[    20.967] (II) Module ABI versions:
[    20.967] 	X.Org ANSI C Emulation: 0.4
[    20.967] 	X.Org Video Driver: 8.0
[    20.967] 	X.Org XInput driver : 11.0
[    20.967] 	X.Org Server Extension : 4.0
[    20.970] (--) PCI:*(0:3:0:0) 10de:087e:1025:0222 rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    20.971] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.971] (II) LoadModule: "extmod"
[    20.988] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.988] (II) Module extmod: vendor="X.Org Foundation"
[    20.988] 	compiled for 1.9.0, module version = 1.0.0
[    20.989] 	Module class: X.Org Server Extension
[    20.989] 	ABI class: X.Org Server Extension, version 4.0
[    20.989] (II) Loading extension MIT-SCREEN-SAVER
[    20.989] (II) Loading extension XFree86-VidModeExtension
[    20.989] (II) Loading extension XFree86-DGA
[    20.989] (II) Loading extension DPMS
[    20.989] (II) Loading extension XVideo
[    20.989] (II) Loading extension XVideo-MotionCompensation
[    20.989] (II) Loading extension X-Resource
[    20.989] (II) LoadModule: "dbe"
[    20.990] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.990] (II) Module dbe: vendor="X.Org Foundation"
[    20.990] 	compiled for 1.9.0, module version = 1.0.0
[    20.990] 	Module class: X.Org Server Extension
[    20.990] 	ABI class: X.Org Server Extension, version 4.0
[    20.991] (II) Loading extension DOUBLE-BUFFER
[    20.991] (II) LoadModule: "glx"
[    20.991] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.079] (II) Module glx: vendor="NVIDIA Corporation"
[    21.079] 	compiled for 4.0.2, module version = 1.0.0
[    21.079] 	Module class: X.Org Server Extension
[    21.079] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    21.079] (II) Loading extension GLX
[    21.079] (II) LoadModule: "record"
[    21.080] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.081] (II) Module record: vendor="X.Org Foundation"
[    21.081] 	compiled for 1.9.0, module version = 1.13.0
[    21.081] 	Module class: X.Org Server Extension
[    21.081] 	ABI class: X.Org Server Extension, version 4.0
[    21.081] (II) Loading extension RECORD
[    21.081] (II) LoadModule: "dri"
[    21.082] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.083] (II) Module dri: vendor="X.Org Foundation"
[    21.083] 	compiled for 1.9.0, module version = 1.0.0
[    21.083] 	ABI class: X.Org Server Extension, version 4.0
[    21.083] (II) Loading extension XFree86-DRI
[    21.083] (II) LoadModule: "dri2"
[    21.084] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.088] (II) Module dri2: vendor="X.Org Foundation"
[    21.088] 	compiled for 1.9.0, module version = 1.2.0
[    21.088] 	ABI class: X.Org Server Extension, version 4.0
[    21.088] (II) Loading extension DRI2
[    21.088] (II) LoadModule: "nvidia"
[    21.089] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.090] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.090] 	compiled for 4.0.2, module version = 1.0.0
[    21.090] 	Module class: X.Org Video Driver
[    21.090] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    21.090] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.091] (++) using VT number 7

[    21.093] (II) Loading sub module "fb"
[    21.093] (II) LoadModule: "fb"
[    21.098] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.098] (II) Module fb: vendor="X.Org Foundation"
[    21.098] 	compiled for 1.9.0, module version = 1.0.0
[    21.099] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.099] (II) Loading sub module "wfb"
[    21.099] (II) LoadModule: "wfb"
[    21.099] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.100] (II) Module wfb: vendor="X.Org Foundation"
[    21.100] 	compiled for 1.9.0, module version = 1.0.0
[    21.100] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.100] (II) Loading sub module "ramdac"
[    21.100] (II) LoadModule: "ramdac"
[    21.100] (II) Module "ramdac" already built-in
[    21.101] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    21.101] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.101] (==) NVIDIA(0): RGB weight 888
[    21.101] (==) NVIDIA(0): Default visual is TrueColor
[    21.101] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.101] (**) NVIDIA(0): Option "NoLogo" "1"
[    21.102] (**) NVIDIA(0): Option "DPI" "100x100"
[    21.102] (**) NVIDIA(0): Option "ModeDebug" "yes"
[    21.102] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.102] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.102] (II) NVIDIA(0):     enabled.
[    22.026] (II) NVIDIA(GPU-0): Display (LG Electronics LG TV (DFP-0)) supports NVIDIA 3D
[    22.026] (II) NVIDIA(GPU-0):     Vision stereo.
[    22.030] (II) NVIDIA(0): NVIDIA GPU ION LE (C79) at PCI:3:0:0 (GPU-0)
[    22.030] (--) NVIDIA(0): Memory: 524288 kBytes
[    22.030] (--) NVIDIA(0): VideoBIOS: 62.79.6c.00.01
[    22.031] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.031] (--) NVIDIA(0): Connected display device(s) on ION LE at PCI:3:0:0
[    22.031] (--) NVIDIA(0):     LG Electronics LG TV (DFP-0)
[    22.031] (--) NVIDIA(0): LG Electronics LG TV (DFP-0): 165.0 MHz maximum pixel clock
[    22.031] (--) NVIDIA(0): LG Electronics LG TV (DFP-0): Internal Single Link TMDS
[    22.031] (--) NVIDIA(0): 
[    22.031] (--) NVIDIA(0): --- EDID for LG Electronics LG TV (DFP-0) ---
[    22.031] (--) NVIDIA(0): EDID Version                 : 1.3
[    22.031] (--) NVIDIA(0): Manufacturer                 : GSM
[    22.031] (--) NVIDIA(0): Monitor Name                 : LG Electronics LG TV
[    22.031] (--) NVIDIA(0): Product ID                   : 1
[    22.031] (--) NVIDIA(0): 32-bit Serial Number         : 16843009
[    22.031] (--) NVIDIA(0): Serial Number String         : 
[    22.031] (--) NVIDIA(0): Manufacture Date             : 2010, week 1
[    22.032] (--) NVIDIA(0): DPMS Capabilities            :
[    22.032] (--) NVIDIA(0): Prefer first detailed timing : Yes
[    22.032] (--) NVIDIA(0): Supports GTF                 : No
[    22.032] (--) NVIDIA(0): Maximum Image Size           : 160mm x 90mm
[    22.032] (--) NVIDIA(0): Valid HSync Range            : 31.0 kHz - 82.0 kHz
[    22.032] (--) NVIDIA(0): Valid VRefresh Range         : 57 Hz - 63 Hz
[    22.032] (--) NVIDIA(0): EDID maximum pixel clock     : 160.0 MHz
[    22.032] (--) NVIDIA(0): 
[    22.032] (--) NVIDIA(0): Standard Timings:
[    22.032] (--) NVIDIA(0):   1280 x 1024 @ 60 Hz
[    22.033] (--) NVIDIA(0):   1024 x 768  @ 60 Hz
[    22.033] (--) NVIDIA(0):   800  x 600  @ 60 Hz
[    22.033] (--) NVIDIA(0):   640  x 480  @ 60 Hz
[    22.033] (--) NVIDIA(0): 
[    22.033] (--) NVIDIA(0): Detailed Timings:
[    22.033] (--) NVIDIA(0):   1920 x 1080 @ 60 Hz
[    22.033] (--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
[    22.033] (--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
[    22.033] (--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
[    22.033] (--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
[    22.033] (--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
[    22.033] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.033] (--) NVIDIA(0):   1280 x 720  @ 60 Hz
[    22.033] (--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
[    22.033] (--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
[    22.034] (--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
[    22.034] (--) NVIDIA(0):     VRes, VSyncStart : 720, 725
[    22.034] (--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
[    22.034] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.034] (--) NVIDIA(0):   720  x 480  @ 60 Hz
[    22.034] (--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
[    22.034] (--) NVIDIA(0):     HRes, HSyncStart : 720, 736
[    22.034] (--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
[    22.034] (--) NVIDIA(0):     VRes, VSyncStart : 480, 489
[    22.034] (--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
[    22.034] (--) NVIDIA(0):     H/V Polarity     : -/-
[    22.034] (--) NVIDIA(0): 
[    22.034] (--) NVIDIA(0): CEA-861B Timings:
[    22.034] (--) NVIDIA(0):   1920 x 1080 @ 60 Hz
[    22.034] (--) NVIDIA(0):     Pixel Clock      : 148.35 MHz
[    22.034] (--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
[    22.034] (--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
[    22.035] (--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
[    22.035] (--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
[    22.035] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.035] (--) NVIDIA(0):     CEA Format       : 16
[    22.035] (--) NVIDIA(0):   1920 x 1080 @ 30 Hz
[    22.035] (--) NVIDIA(0):     Pixel Clock      : 89.01 MHz
[    22.035] (--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
[    22.035] (--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
[    22.035] (--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
[    22.035] (--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
[    22.035] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.035] (--) NVIDIA(0):     CEA Format       : 34
[    22.035] (--) NVIDIA(0):   1920 x 1080 @ 24 Hz
[    22.035] (--) NVIDIA(0):     Pixel Clock      : 74.16 MHz
[    22.035] (--) NVIDIA(0):     HRes, HSyncStart : 1920, 2558
[    22.036] (--) NVIDIA(0):     HSyncEnd, HTotal : 2602, 2750
[    22.036] (--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
[    22.036] (--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
[    22.036] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.036] (--) NVIDIA(0):     CEA Format       : 32
[    22.036] (--) NVIDIA(0):   1920 x 1080 @ 60 Hz
[    22.036] (--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
[    22.036] (--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
[    22.036] (--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
[    22.036] (--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
[    22.036] (--) NVIDIA(0):     VSyncEnd, VTotal : 1094, 1124
[    22.036] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.036] (--) NVIDIA(0):     Extra            : Interlaced
[    22.037] (--) NVIDIA(0):     CEA Format       : 5
[    22.037] (--) NVIDIA(0):   1280 x 720  @ 60 Hz
[    22.037] (--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
[    22.037] (--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
[    22.037] (--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
[    22.037] (--) NVIDIA(0):     VRes, VSyncStart : 720, 725
[    22.037] (--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
[    22.037] (--) NVIDIA(0):     H/V Polarity     : +/+
[    22.037] (--) NVIDIA(0):     CEA Format       : 4
[    22.037] (--) NVIDIA(0):   720  x 480  @ 60 Hz
[    22.037] (--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
[    22.037] (--) NVIDIA(0):     HRes, HSyncStart : 720, 736
[    22.037] (--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
[    22.037] (--) NVIDIA(0):     VRes, VSyncStart : 480, 489
[    22.037] (--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
[    22.038] (--) NVIDIA(0):     H/V Polarity     : -/-
[    22.038] (--) NVIDIA(0):     CEA Format       : 3
[    22.038] (--) NVIDIA(0):   720  x 480  @ 60 Hz
[    22.038] (--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
[    22.038] (--) NVIDIA(0):     HRes, HSyncStart : 720, 736
[    22.038] (--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
[    22.038] (--) NVIDIA(0):     VRes, VSyncStart : 480, 489
[    22.038] (--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
[    22.038] (--) NVIDIA(0):     H/V Polarity     : -/-
[    22.038] (--) NVIDIA(0):     CEA Format       : 2
[    22.038] (--) NVIDIA(0): 
[    22.038] (--) NVIDIA(0): 
[    22.038] (--) NVIDIA(0): Raw EDID bytes:
[    22.038] (--) NVIDIA(0): 
[    22.038] (--) NVIDIA(0):   00 ff ff ff ff ff ff 00  1e 6d 01 00 01 01 01 01
[    22.039] (--) NVIDIA(0):   01 14 01 03 80 10 09 78  0a ee 91 a3 54 4c 99 26
[    22.039] (--) NVIDIA(0):   0f 50 54 a1 08 00 81 80  61 40 45 40 31 40 01 01
[    22.039] (--) NVIDIA(0):   01 01 01 01 01 01 02 3a  80 18 71 38 2d 40 58 2c
[    22.039] (--) NVIDIA(0):   45 00 a0 5a 00 00 00 1e  01 1d 00 72 51 d0 1e 20
[    22.039] (--) NVIDIA(0):   6e 28 55 00 a0 5a 00 00  00 1e 00 00 00 fd 00 39
[    22.039] (--) NVIDIA(0):   3f 1f 52 10 00 0a 20 20  20 20 20 20 00 00 00 fc
[    22.039] (--) NVIDIA(0):   00 4c 47 20 54 56 0a 20  20 20 20 20 20 20 01 04
[    22.039] (--) NVIDIA(0):   02 03 1c f1 47 10 22 20  05 84 03 02 23 09 07 07
[    22.039] (--) NVIDIA(0):   67 03 0c 00 10 00 b8 2d  e3 05 03 01 02 3a 80 18
[    22.039] (--) NVIDIA(0):   71 38 2d 40 58 2c 04 05  a0 5a 00 00 00 1e 01 1d
[    22.039] (--) NVIDIA(0):   80 18 71 1c 16 20 58 2c  25 00 a0 5a 00 00 00 9e
[    22.039] (--) NVIDIA(0):   01 1d 00 72 51 d0 1e 20  6e 28 55 00 a0 5a 00 00
[    22.039] (--) NVIDIA(0):   00 1e 8c 0a d0 8a 20 e0  2d 10 10 3e 96 00 a0 5a
[    22.039] (--) NVIDIA(0):   00 00 00 18 26 36 80 a0  70 38 1f 40 30 20 25 00
[    22.039] (--) NVIDIA(0):   a0 5a 00 00 00 1a 00 00  00 00 00 00 00 00 00 cc
[    22.040] (--) NVIDIA(0): 
[    22.040] (--) NVIDIA(0): --- End of EDID for LG Electronics LG TV (DFP-0) ---
[    22.040] (--) NVIDIA(0): 
[    22.043] (II) NVIDIA(0): Frequency information for LG Electronics LG TV (DFP-0):
[    22.043] (II) NVIDIA(0):   HorizSync   : 31.000-82.000 kHz
[    22.043] (II) NVIDIA(0):   VertRefresh : 57.000-63.000 Hz
[    22.043] (II) NVIDIA(0):     (HorizSync from EDID)
[    22.043] (II) NVIDIA(0):     (VertRefresh from EDID)
[    22.044] (II) NVIDIA(0): 
[    22.044] (II) NVIDIA(0): --- Building ModePool for LG Electronics LG TV (DFP-0) ---
[    22.044] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.044] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.044] (II) NVIDIA(0):     For use as DFP backend.
[    22.044] (II) NVIDIA(0):     Mode Source: EDID
[    22.044] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    22.044] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
[    22.044] (II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
[    22.044] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.044] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.044] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.044] (II) NVIDIA(0):     Mode is valid.
[    22.045] (II) NVIDIA(0): 
[    22.045] (II) NVIDIA(0):   Validating Mode "1280x720":
[    22.045] (II) NVIDIA(0):     1280 x 720 @ 60 Hz
[    22.045] (II) NVIDIA(0):     For use as DFP backend.
[    22.045] (II) NVIDIA(0):     Mode Source: EDID
[    22.045] (II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
[    22.045] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
[    22.045] (II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
[    22.045] (II) NVIDIA(0):       VRes, VSyncStart :  720,  725
[    22.045] (II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
[    22.045] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.045] (II) NVIDIA(0):     Mode is valid.
[    22.045] (II) NVIDIA(0): 
[    22.045] (II) NVIDIA(0):   Validating Mode "720x480":
[    22.045] (II) NVIDIA(0):     720 x 480 @ 60 Hz
[    22.046] (II) NVIDIA(0):     For use as DFP backend.
[    22.046] (II) NVIDIA(0):     Mode Source: EDID
[    22.046] (II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
[    22.046] (II) NVIDIA(0):       HRes, HSyncStart :  720,  736
[    22.046] (II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
[    22.046] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.046] (II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
[    22.046] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.046] (II) NVIDIA(0):     Mode is valid.
[    22.046] (II) NVIDIA(0): 
[    22.046] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.046] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.046] (II) NVIDIA(0):     For use as DFP backend.
[    22.046] (II) NVIDIA(0):     Mode Source: EDID
[    22.047] (II) NVIDIA(0):       Pixel Clock      : 148.35 MHz
[    22.047] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
[    22.047] (II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
[    22.047] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.047] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.047] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.047] (II) NVIDIA(0):     Mode is valid.
[    22.047] (II) NVIDIA(0): 
[    22.047] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.047] (II) NVIDIA(0):     1920 x 1080 @ 30 Hz
[    22.047] (II) NVIDIA(0):     For use as DFP backend.
[    22.047] (II) NVIDIA(0):     Mode Source: EDID
[    22.047] (II) NVIDIA(0):       Pixel Clock      : 89.01 MHz
[    22.047] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
[    22.047] (II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
[    22.048] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.048] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.048] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.048] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    22.048] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.048] (WW) NVIDIA(0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    22.048] (WW) NVIDIA(0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    22.048] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    22.048] (II) NVIDIA(0):     Mode is valid.
[    22.048] (II) NVIDIA(0): 
[    22.048] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.048] (II) NVIDIA(0):     1920 x 1080 @ 24 Hz
[    22.048] (II) NVIDIA(0):     For use as DFP backend.
[    22.048] (II) NVIDIA(0):     Mode Source: EDID
[    22.048] (II) NVIDIA(0):       Pixel Clock      : 74.16 MHz
[    22.049] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2558
[    22.049] (II) NVIDIA(0):       HSyncEnd, HTotal : 2602, 2750
[    22.049] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.049] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.049] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.049] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    22.049] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.049] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-82.000 kHz) would
[    22.049] (WW) NVIDIA(0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    22.049] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    22.049] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    22.049] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.049] (WW) NVIDIA(0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    22.050] (WW) NVIDIA(0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    22.050] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    22.050] (II) NVIDIA(0):     Mode is valid.
[    22.050] (II) NVIDIA(0): 
[    22.050] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.050] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.050] (II) NVIDIA(0):     For use as DFP backend.
[    22.050] (II) NVIDIA(0):     Mode Source: EDID
[    22.050] (II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
[    22.050] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
[    22.050] (II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
[    22.050] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.050] (II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124
[    22.050] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.050] (II) NVIDIA(0):       Extra            : Interlace
[    22.051] (II) NVIDIA(0):     Mode is valid.
[    22.051] (II) NVIDIA(0): 
[    22.051] (II) NVIDIA(0):   Validating Mode "1280x720":
[    22.051] (II) NVIDIA(0):     1280 x 720 @ 60 Hz
[    22.051] (II) NVIDIA(0):     For use as DFP backend.
[    22.051] (II) NVIDIA(0):     Mode Source: EDID
[    22.051] (II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
[    22.051] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
[    22.051] (II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
[    22.051] (II) NVIDIA(0):       VRes, VSyncStart :  720,  725
[    22.051] (II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
[    22.051] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.051] (II) NVIDIA(0):     Mode is valid.
[    22.051] (II) NVIDIA(0): 
[    22.051] (II) NVIDIA(0):   Validating Mode "720x480":
[    22.052] (II) NVIDIA(0):     720 x 480 @ 60 Hz
[    22.052] (II) NVIDIA(0):     For use as DFP backend.
[    22.052] (II) NVIDIA(0):     Mode Source: EDID
[    22.052] (II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
[    22.052] (II) NVIDIA(0):       HRes, HSyncStart :  720,  736
[    22.052] (II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
[    22.052] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.052] (II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
[    22.052] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.052] (II) NVIDIA(0):     Mode is valid.
[    22.052] (II) NVIDIA(0): 
[    22.052] (II) NVIDIA(0):   Validating Mode "720x480":
[    22.052] (II) NVIDIA(0):     720 x 480 @ 60 Hz
[    22.052] (II) NVIDIA(0):     For use as DFP backend.
[    22.053] (II) NVIDIA(0):     Mode Source: EDID
[    22.053] (II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
[    22.053] (II) NVIDIA(0):       HRes, HSyncStart :  720,  736
[    22.053] (II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
[    22.053] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.053] (II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
[    22.053] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.053] (II) NVIDIA(0):     Mode is valid.
[    22.053] (II) NVIDIA(0): 
[    22.053] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.053] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[    22.053] (II) NVIDIA(0):     For use as DFP backend.
[    22.053] (II) NVIDIA(0):     Mode Source: EDID
[    22.053] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.054] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[    22.054] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    22.054] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.054] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    22.054] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.054] (II) NVIDIA(0):     Mode is valid.
[    22.054] (II) NVIDIA(0): 
[    22.054] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.054] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    22.054] (II) NVIDIA(0):     For use as DFP backend.
[    22.054] (II) NVIDIA(0):     Mode Source: EDID
[    22.054] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[    22.054] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    22.054] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[    22.055] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.055] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    22.055] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.055] (II) NVIDIA(0):     Mode is valid.
[    22.055] (II) NVIDIA(0): 
[    22.055] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.055] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    22.055] (II) NVIDIA(0):     For use as DFP backend.
[    22.055] (II) NVIDIA(0):     Mode Source: EDID
[    22.055] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[    22.055] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[    22.055] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[    22.055] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.055] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[    22.055] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.056] (II) NVIDIA(0):     Mode is valid.
[    22.056] (II) NVIDIA(0): 
[    22.056] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.056] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    22.056] (II) NVIDIA(0):     For use as DFP backend.
[    22.056] (II) NVIDIA(0):     Mode Source: EDID
[    22.056] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[    22.056] (II) NVIDIA(0):       HRes, HSyncStart :  640,  648
[    22.056] (II) NVIDIA(0):       HSyncEnd, HTotal :  744,  800
[    22.056] (II) NVIDIA(0):       VRes, VSyncStart :  480,  482
[    22.056] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  525
[    22.056] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.056] (II) NVIDIA(0):     Mode is valid.
[    22.056] (II) NVIDIA(0): 
[    22.057] (II) NVIDIA(0): 
[    22.057] (II) NVIDIA(0): Native backend timings for LG Electronics LG TV (DFP-0):
[    22.057] (II) NVIDIA(0):   1920 x 1080 @ 60 Hz
[    22.057] (II) NVIDIA(0):     Pixel Clock      : 148.500 MHz
[    22.057] (II) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
[    22.057] (II) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
[    22.057] (II) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
[    22.057] (II) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
[    22.057] (II) NVIDIA(0):     H/V Polarity     : +/+
[    22.057] (II) NVIDIA(0): 
[    22.057] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.057] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.057] (II) NVIDIA(0):     Mode Source: EDID
[    22.057] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    22.057] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
[    22.058] (II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
[    22.058] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.058] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.058] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.058] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.058] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.058] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.058] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.058] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.058] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.058] (II) NVIDIA(GPU-0):     Native Centered and Native Scaled are identical;
[    22.058] (II) NVIDIA(GPU-0):         collapsing Native Scaled.
[    22.058] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.059] (II) NVIDIA(GPU-0):     BestFit Centered         1920x1080
[    22.059] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.059] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.059] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.059] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.059] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.059] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.059] (II) NVIDIA(0):     Mode is valid.
[    22.059] (II) NVIDIA(0): 
[    22.060] (II) NVIDIA(0):   Validating Mode "1280x720":
[    22.060] (II) NVIDIA(0):     1280 x 720 @ 60 Hz
[    22.060] (II) NVIDIA(0):     Mode Source: EDID
[    22.060] (II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
[    22.060] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
[    22.060] (II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
[    22.060] (II) NVIDIA(0):       VRes, VSyncStart :  720,  725
[    22.060] (II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
[    22.060] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.060] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.060] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.060] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.060] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.061] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.061] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.062] (II) NVIDIA(GPU-0):     BestFit Centered         1280x720
[    22.062] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.062] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.062] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.062] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.062] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.062] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.062] (II) NVIDIA(GPU-0):     Native Centered          1280x720
[    22.062] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.062] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.062] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.062] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.062] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.062] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.063] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.063] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.063] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.063] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.063] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.063] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.063] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.063] (II) NVIDIA(0):     Mode is valid.
[    22.063] (II) NVIDIA(0): 
[    22.063] (II) NVIDIA(0):   Validating Mode "720x480":
[    22.063] (II) NVIDIA(0):     720 x 480 @ 60 Hz
[    22.063] (II) NVIDIA(0):     Mode Source: EDID
[    22.063] (II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
[    22.063] (II) NVIDIA(0):       HRes, HSyncStart :  720,  736
[    22.064] (II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
[    22.064] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.064] (II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
[    22.064] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.064] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.064] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.064] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.064] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.065] (II) NVIDIA(GPU-0):     BestFit Centered         720x480
[    22.065] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.065] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.065] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.066] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.066] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.066] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.066] (II) NVIDIA(GPU-0):     Native Centered          720x480
[    22.066] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.066] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.066] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.066] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.066] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.066] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.066] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.066] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.066] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.066] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.067] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.067] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.067] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.067] (II) NVIDIA(GPU-0):     Native AspectScaled      1620x1080
[    22.067] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.067] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.067] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.067] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.067] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.067] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.067] (II) NVIDIA(0):     Mode is valid.
[    22.067] (II) NVIDIA(0): 
[    22.067] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.067] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.067] (II) NVIDIA(0):     Mode Source: EDID
[    22.067] (II) NVIDIA(0):       Pixel Clock      : 148.35 MHz
[    22.068] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
[    22.068] (II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
[    22.068] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.068] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.068] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.068] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.068] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.068] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.068] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.068] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.068] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.068] (II) NVIDIA(GPU-0):     Native Centered and Native Scaled are identical;
[    22.068] (II) NVIDIA(GPU-0):         collapsing Native Scaled.
[    22.069] (II) NVIDIA(GPU-0):     BestFit Centered         1920x1080
[    22.069] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.069] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.069] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.069] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.069] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.070] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.070] (II) NVIDIA(GPU-0):     Native Centered          1920x1080
[    22.070] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.070] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.070] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.070] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.070] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.070] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.070] (II) NVIDIA(0):     Mode is valid.
[    22.070] (II) NVIDIA(0): 
[    22.070] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.070] (II) NVIDIA(0):     1920 x 1080 @ 30 Hz
[    22.070] (II) NVIDIA(0):     Mode Source: EDID
[    22.071] (II) NVIDIA(0):       Pixel Clock      : 89.01 MHz
[    22.071] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
[    22.071] (II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
[    22.071] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.071] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.071] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.071] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    22.071] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.071] (WW) NVIDIA(0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    22.071] (WW) NVIDIA(0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    22.071] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    22.071] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.071] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.071] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.071] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.072] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.072] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.072] (II) NVIDIA(GPU-0):     Native Centered and Native Scaled are identical;
[    22.072] (II) NVIDIA(GPU-0):         collapsing Native Scaled.
[    22.073] (II) NVIDIA(GPU-0):     BestFit Centered         1920x1080
[    22.073] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.073] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.073] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.073] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.073] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.073] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.073] (II) NVIDIA(GPU-0):     Native Centered          1920x1080
[    22.073] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.073] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.073] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.073] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.073] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.073] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.073] (II) NVIDIA(0):     Mode is valid.
[    22.074] (II) NVIDIA(0): 
[    22.074] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.074] (II) NVIDIA(0):     1920 x 1080 @ 24 Hz
[    22.074] (II) NVIDIA(0):     Mode Source: EDID
[    22.074] (II) NVIDIA(0):       Pixel Clock      : 74.16 MHz
[    22.074] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2558
[    22.074] (II) NVIDIA(0):       HSyncEnd, HTotal : 2602, 2750
[    22.074] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.074] (II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
[    22.074] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.074] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    22.074] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.074] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-82.000 kHz) would
[    22.074] (WW) NVIDIA(0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    22.075] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    22.075] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    22.075] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.075] (WW) NVIDIA(0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    22.075] (WW) NVIDIA(0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    22.075] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    22.075] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.075] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.075] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.075] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.075] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.075] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.075] (II) NVIDIA(GPU-0):     Native Centered and Native Scaled are identical;
[    22.076] (II) NVIDIA(GPU-0):         collapsing Native Scaled.
[    22.076] (II) NVIDIA(GPU-0):     BestFit Centered         1920x1080
[    22.076] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.076] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.076] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.077] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.077] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.077] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.077] (II) NVIDIA(GPU-0):     Native Centered          1920x1080
[    22.077] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.077] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.077] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.077] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.077] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.077] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.077] (II) NVIDIA(0):     Mode is valid.
[    22.077] (II) NVIDIA(0): 
[    22.077] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.077] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.078] (II) NVIDIA(0):     Mode Source: EDID
[    22.078] (II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
[    22.078] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
[    22.078] (II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
[    22.078] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
[    22.078] (II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124
[    22.078] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.078] (II) NVIDIA(0):       Extra            : Interlace
[    22.078] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.078] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.078] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.078] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.078] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.078] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.079] (II) NVIDIA(GPU-0):     Native Centered and Native Scaled are identical;
[    22.079] (II) NVIDIA(GPU-0):         collapsing Native Scaled.
[    22.079] (II) NVIDIA(GPU-0):     BestFit Centered         1920x1080
[    22.079] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.079] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.080] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.080] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.080] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.080] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.080] (II) NVIDIA(GPU-0):     Native Centered          1920x1080
[    22.080] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.080] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.080] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.080] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.080] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.080] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.080] (II) NVIDIA(0):     Mode is valid.
[    22.080] (II) NVIDIA(0): 
[    22.080] (II) NVIDIA(0):   Validating Mode "1280x720":
[    22.081] (II) NVIDIA(0):     1280 x 720 @ 60 Hz
[    22.081] (II) NVIDIA(0):     Mode Source: EDID
[    22.081] (II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
[    22.081] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
[    22.081] (II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
[    22.081] (II) NVIDIA(0):       VRes, VSyncStart :  720,  725
[    22.081] (II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
[    22.081] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.081] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.081] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.081] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.081] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.081] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.082] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.082] (II) NVIDIA(GPU-0):     BestFit Centered         1280x720
[    22.083] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.083] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.083] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.083] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.083] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.083] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.083] (II) NVIDIA(GPU-0):     Native Centered          1280x720
[    22.083] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.083] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.083] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.083] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.083] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.083] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.083] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.084] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.084] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.084] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.084] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.084] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.084] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.084] (II) NVIDIA(0):     Mode is valid.
[    22.084] (II) NVIDIA(0): 
[    22.084] (II) NVIDIA(0):   Validating Mode "720x480":
[    22.084] (II) NVIDIA(0):     720 x 480 @ 60 Hz
[    22.084] (II) NVIDIA(0):     Mode Source: EDID
[    22.084] (II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
[    22.084] (II) NVIDIA(0):       HRes, HSyncStart :  720,  736
[    22.084] (II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
[    22.084] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.085] (II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
[    22.085] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.085] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.085] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.085] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.085] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.086] (II) NVIDIA(GPU-0):     BestFit Centered         720x480
[    22.086] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.086] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.086] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.086] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.086] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.087] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.087] (II) NVIDIA(GPU-0):     Native Centered          720x480
[    22.087] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.087] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.087] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.087] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.087] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.087] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.087] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.087] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.087] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.087] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.087] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.088] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.088] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.088] (II) NVIDIA(GPU-0):     Native AspectScaled      1620x1080
[    22.088] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.088] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.088] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.088] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.088] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.088] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.088] (II) NVIDIA(0):     Mode is valid.
[    22.088] (II) NVIDIA(0): 
[    22.088] (II) NVIDIA(0):   Validating Mode "720x480":
[    22.088] (II) NVIDIA(0):     720 x 480 @ 60 Hz
[    22.088] (II) NVIDIA(0):     Mode Source: EDID
[    22.089] (II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
[    22.089] (II) NVIDIA(0):       HRes, HSyncStart :  720,  736
[    22.089] (II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
[    22.089] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.089] (II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
[    22.089] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.089] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.089] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.089] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.089] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.090] (II) NVIDIA(GPU-0):     BestFit Centered         720x480
[    22.090] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.091] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.091] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.091] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.091] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.091] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.091] (II) NVIDIA(GPU-0):     Native Centered          720x480
[    22.091] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.091] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.091] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.091] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.091] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.091] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.091] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.091] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.091] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.092] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.092] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.092] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.092] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.092] (II) NVIDIA(GPU-0):     Native AspectScaled      1620x1080
[    22.092] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.092] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.092] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.092] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.092] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.092] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.092] (II) NVIDIA(0):     Mode is valid.
[    22.092] (II) NVIDIA(0): 
[    22.092] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.093] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[    22.093] (II) NVIDIA(0):     Mode Source: EDID
[    22.093] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.093] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[    22.093] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    22.093] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.093] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    22.093] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.093] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.093] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.093] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.093] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.095] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.095] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.095] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.095] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.095] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.095] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.095] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.095] (II) NVIDIA(GPU-0):     Native Centered          1280x1024
[    22.095] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.095] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.095] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.095] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.095] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.096] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.096] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.096] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.096] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.096] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.096] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.096] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.096] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.096] (II) NVIDIA(GPU-0):     Native AspectScaled      1350x1080
[    22.096] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.096] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.096] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.096] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.096] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.096] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.097] (II) NVIDIA(0):     Mode is valid.
[    22.097] (II) NVIDIA(0): 
[    22.097] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.097] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    22.097] (II) NVIDIA(0):     Mode Source: EDID
[    22.097] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[    22.097] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    22.097] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[    22.097] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.097] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    22.097] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.097] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.097] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.097] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.098] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.099] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.099] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.099] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.099] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.099] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.099] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.099] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.099] (II) NVIDIA(GPU-0):     Native Centered          1024x768
[    22.099] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.099] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.099] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.100] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.100] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.100] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.100] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.100] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.100] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.100] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.100] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.100] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.100] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.100] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.100] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.100] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.100] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.101] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.101] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.101] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.101] (II) NVIDIA(0):     Mode is valid.
[    22.101] (II) NVIDIA(0): 
[    22.101] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.101] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    22.101] (II) NVIDIA(0):     Mode Source: EDID
[    22.101] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[    22.101] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[    22.101] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[    22.101] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.101] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[    22.101] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.102] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.102] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.102] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.102] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.103] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.103] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.103] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.103] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.103] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.103] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.103] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.103] (II) NVIDIA(GPU-0):     Native Centered          800x600
[    22.104] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.104] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.104] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.104] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.104] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.104] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.104] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.104] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.104] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.104] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.104] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.104] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.104] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.104] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.105] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.105] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.105] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.105] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.105] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.105] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.105] (II) NVIDIA(0):     Mode is valid.
[    22.105] (II) NVIDIA(0): 
[    22.105] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.105] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    22.105] (II) NVIDIA(0):     Mode Source: EDID
[    22.105] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[    22.105] (II) NVIDIA(0):       HRes, HSyncStart :  640,  648
[    22.105] (II) NVIDIA(0):       HSyncEnd, HTotal :  744,  800
[    22.105] (II) NVIDIA(0):       VRes, VSyncStart :  480,  482
[    22.106] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  525
[    22.106] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.106] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.106] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.106] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.106] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.107] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.107] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.107] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.107] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.107] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.108] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.108] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.108] (II) NVIDIA(GPU-0):     Native Centered          640x480
[    22.108] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.108] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.108] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.108] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.108] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.108] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.108] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.108] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.108] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.108] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.108] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.109] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.109] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.109] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.109] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.109] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.109] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.109] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.109] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.109] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.109] (II) NVIDIA(0):     Mode is valid.
[    22.109] (II) NVIDIA(0): 
[    22.109] (II) NVIDIA(0):   Validating Mode "640x350":
[    22.109] (II) NVIDIA(0):     640 x 350 @ 85 Hz
[    22.109] (II) NVIDIA(0):     Mode Source: X Server
[    22.110] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.110] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    22.110] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    22.110] (II) NVIDIA(0):       VRes, VSyncStart :  350,  382
[    22.110] (II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
[    22.110] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.110] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.110] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.110] (II) NVIDIA(0):         mode validation
[    22.110] (II) NVIDIA(0):     BestFit Backend for "640x350": 1920x1080
[    22.110] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.111] (II) NVIDIA(GPU-0):     BestFit Centered         640x350
[    22.111] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.111] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.111] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.111] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.112] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.112] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.112] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.112] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.112] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.112] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.112] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.112] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.112] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.112] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1920x1050
[    22.112] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.112] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.112] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.112] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.113] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.113] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.113] (II) NVIDIA(0):     Mode is valid.
[    22.113] (II) NVIDIA(0): 
[    22.113] (II) NVIDIA(0):   Validating Mode "320x175":
[    22.113] (II) NVIDIA(0):     320 x 175 @ 85 Hz
[    22.113] (II) NVIDIA(0):     Mode Source: X Server
[    22.113] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    22.113] (II) NVIDIA(0):       HRes, HSyncStart :  320,  336
[    22.113] (II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
[    22.113] (II) NVIDIA(0):       VRes, VSyncStart :  175,  191
[    22.113] (II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
[    22.113] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.113] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.114] (II) NVIDIA(0):     VertRefresh (85.3 Hz) out of range (57.000-63.000 Hz);
[    22.114] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.114] (II) NVIDIA(0):         mode validation
[    22.114] (II) NVIDIA(0):     BestFit Backend for "320x175": 1920x1080
[    22.114] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.115] (II) NVIDIA(GPU-0):     BestFit Centered         320x175
[    22.115] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.115] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.115] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.115] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.115] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.115] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.115] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.115] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.115] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.115] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.116] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.116] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.116] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.116] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1920x1050
[    22.116] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.116] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.116] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.116] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.116] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.116] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.116] (II) NVIDIA(0):     Mode is valid.
[    22.116] (II) NVIDIA(0): 
[    22.116] (II) NVIDIA(0):   Validating Mode "640x400":
[    22.116] (II) NVIDIA(0):     640 x 400 @ 85 Hz
[    22.117] (II) NVIDIA(0):     Mode Source: X Server
[    22.117] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.117] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    22.117] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    22.117] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    22.117] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
[    22.117] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.117] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.117] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.117] (II) NVIDIA(0):         mode validation
[    22.117] (II) NVIDIA(0):     BestFit Backend for "640x400": 1920x1080
[    22.117] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.118] (II) NVIDIA(GPU-0):     BestFit Centered         640x400
[    22.118] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.119] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.119] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.119] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.119] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.119] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.119] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.119] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.119] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.119] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.119] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.119] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.119] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.119] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.119] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.119] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.120] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.120] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.120] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.120] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.120] (II) NVIDIA(0):     Mode is valid.
[    22.120] (II) NVIDIA(0): 
[    22.120] (II) NVIDIA(0):   Validating Mode "320x200":
[    22.120] (II) NVIDIA(0):     320 x 200 @ 85 Hz
[    22.120] (II) NVIDIA(0):     Mode Source: X Server
[    22.120] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    22.120] (II) NVIDIA(0):       HRes, HSyncStart :  320,  336
[    22.120] (II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
[    22.120] (II) NVIDIA(0):       VRes, VSyncStart :  200,  200
[    22.120] (II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
[    22.121] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.121] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.121] (II) NVIDIA(0):     VertRefresh (85.3 Hz) out of range (57.000-63.000 Hz);
[    22.121] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.121] (II) NVIDIA(0):         mode validation
[    22.121] (II) NVIDIA(0):     BestFit Backend for "320x200": 1920x1080
[    22.121] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.122] (II) NVIDIA(GPU-0):     BestFit Centered         320x200
[    22.122] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.122] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.122] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.122] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.122] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.122] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.122] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.123] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.123] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.123] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.123] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.123] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.123] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.123] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.123] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.123] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.123] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.123] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.123] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.123] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.123] (II) NVIDIA(0):     Mode is valid.
[    22.123] (II) NVIDIA(0): 
[    22.124] (II) NVIDIA(0):   Validating Mode "720x400":
[    22.124] (II) NVIDIA(0):     720 x 400 @ 85 Hz
[    22.124] (II) NVIDIA(0):     Mode Source: X Server
[    22.124] (II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
[    22.124] (II) NVIDIA(0):       HRes, HSyncStart :  720,  756
[    22.124] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
[    22.124] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    22.124] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
[    22.124] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.124] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.124] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.124] (II) NVIDIA(0):         mode validation
[    22.124] (II) NVIDIA(0):     BestFit Backend for "720x400": 1920x1080
[    22.125] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.126] (II) NVIDIA(GPU-0):     BestFit Centered         720x400
[    22.126] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.126] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.126] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.126] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.126] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.126] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.126] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.126] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.126] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.126] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.126] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.126] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.126] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.127] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1920x1066
[    22.127] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.127] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.127] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.127] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.127] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.127] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.127] (II) NVIDIA(0):     Mode is valid.
[    22.127] (II) NVIDIA(0): 
[    22.127] (II) NVIDIA(0):   Validating Mode "360x200":
[    22.127] (II) NVIDIA(0):     360 x 200 @ 85 Hz
[    22.127] (II) NVIDIA(0):     Mode Source: X Server
[    22.127] (II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
[    22.127] (II) NVIDIA(0):       HRes, HSyncStart :  360,  378
[    22.127] (II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
[    22.128] (II) NVIDIA(0):       VRes, VSyncStart :  200,  200
[    22.128] (II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
[    22.128] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.128] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.128] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.128] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.128] (II) NVIDIA(0):         mode validation
[    22.128] (II) NVIDIA(0):     BestFit Backend for "360x200": 1920x1080
[    22.128] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.129] (II) NVIDIA(GPU-0):     BestFit Centered         360x200
[    22.129] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.129] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.129] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.129] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.129] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.130] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.130] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.130] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.130] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.130] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.130] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.130] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.130] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.130] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1920x1066
[    22.130] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.130] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.130] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.130] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.130] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.130] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.131] (II) NVIDIA(0):     Mode is valid.
[    22.131] (II) NVIDIA(0): 
[    22.131] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.131] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    22.131] (II) NVIDIA(0):     Mode Source: X Server
[    22.131] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[    22.131] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    22.131] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
[    22.131] (II) NVIDIA(0):       VRes, VSyncStart :  480,  490
[    22.131] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
[    22.131] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.131] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.131] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.132] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.133] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.133] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.133] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.133] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.133] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.133] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.133] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.133] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.133] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.133] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.133] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.133] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.133] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.133] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.134] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.134] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.134] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.134] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.134] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.134] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.134] (II) NVIDIA(0):     Mode is valid.
[    22.134] (II) NVIDIA(0): 
[    22.134] (II) NVIDIA(0):   Validating Mode "320x240":
[    22.134] (II) NVIDIA(0):     320 x 240 @ 60 Hz
[    22.134] (II) NVIDIA(0):     Mode Source: X Server
[    22.134] (II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
[    22.134] (II) NVIDIA(0):       HRes, HSyncStart :  320,  328
[    22.134] (II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
[    22.134] (II) NVIDIA(0):       VRes, VSyncStart :  240,  245
[    22.135] (II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
[    22.135] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.135] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.135] (II) NVIDIA(0):     BestFit Backend for "320x240": 1920x1080
[    22.135] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.136] (II) NVIDIA(GPU-0):     BestFit Centered         320x240
[    22.136] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.136] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.136] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.136] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.136] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.136] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.136] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.136] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.136] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.137] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.137] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.137] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.137] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.137] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.137] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.137] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.137] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.137] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.137] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.137] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.137] (II) NVIDIA(0):     Mode is valid.
[    22.137] (II) NVIDIA(0): 
[    22.137] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.138] (II) NVIDIA(0):     640 x 480 @ 73 Hz
[    22.138] (II) NVIDIA(0):     Mode Source: X Server
[    22.138] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.138] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[    22.138] (II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
[    22.138] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.138] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
[    22.138] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.138] (II) NVIDIA(0):     VertRefresh (72.8 Hz) out of range (57.000-63.000 Hz);
[    22.138] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.138] (II) NVIDIA(0):         mode validation
[    22.138] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.138] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.139] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.139] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.140] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.140] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.140] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.140] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.140] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.140] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.140] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.140] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.140] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.140] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.141] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.141] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.141] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.141] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.141] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.141] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.141] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.141] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.141] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.141] (II) NVIDIA(0):     Mode is valid.
[    22.141] (II) NVIDIA(0): 
[    22.141] (II) NVIDIA(0):   Validating Mode "320x240":
[    22.141] (II) NVIDIA(0):     320 x 240 @ 73 Hz
[    22.141] (II) NVIDIA(0):     Mode Source: X Server
[    22.142] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    22.142] (II) NVIDIA(0):       HRes, HSyncStart :  320,  332
[    22.142] (II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
[    22.142] (II) NVIDIA(0):       VRes, VSyncStart :  240,  244
[    22.142] (II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
[    22.142] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.142] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.142] (II) NVIDIA(0):     VertRefresh (72.8 Hz) out of range (57.000-63.000 Hz);
[    22.142] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.142] (II) NVIDIA(0):         mode validation
[    22.142] (II) NVIDIA(0):     BestFit Backend for "320x240": 1920x1080
[    22.142] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.143] (II) NVIDIA(GPU-0):     BestFit Centered         320x240
[    22.143] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.143] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.144] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.144] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.144] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.144] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.144] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.144] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.144] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.144] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.144] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.144] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.144] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.144] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.144] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.144] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.145] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.145] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.145] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.145] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.145] (II) NVIDIA(0):     Mode is valid.
[    22.145] (II) NVIDIA(0): 
[    22.145] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.145] (II) NVIDIA(0):     640 x 480 @ 75 Hz
[    22.145] (II) NVIDIA(0):     Mode Source: X Server
[    22.145] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.145] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    22.145] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
[    22.145] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    22.145] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
[    22.145] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.146] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.146] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.146] (II) NVIDIA(0):         mode validation
[    22.146] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.146] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.147] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.147] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.147] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.147] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.147] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.147] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.147] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.147] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.147] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.147] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.147] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.148] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.148] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.148] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.148] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.148] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.148] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.148] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.148] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.148] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.148] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.148] (II) NVIDIA(0):     Mode is valid.
[    22.148] (II) NVIDIA(0): 
[    22.148] (II) NVIDIA(0):   Validating Mode "320x240":
[    22.149] (II) NVIDIA(0):     320 x 240 @ 75 Hz
[    22.149] (II) NVIDIA(0):     Mode Source: X Server
[    22.149] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    22.149] (II) NVIDIA(0):       HRes, HSyncStart :  320,  328
[    22.149] (II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
[    22.149] (II) NVIDIA(0):       VRes, VSyncStart :  240,  240
[    22.149] (II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
[    22.149] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.149] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.149] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.149] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.149] (II) NVIDIA(0):         mode validation
[    22.149] (II) NVIDIA(0):     BestFit Backend for "320x240": 1920x1080
[    22.149] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.150] (II) NVIDIA(GPU-0):     BestFit Centered         320x240
[    22.151] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.151] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.151] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.151] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.151] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.151] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.151] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.151] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.151] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.151] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.151] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.151] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.151] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.151] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.151] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.151] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.152] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.152] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.152] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.152] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.152] (II) NVIDIA(0):     Mode is valid.
[    22.152] (II) NVIDIA(0): 
[    22.152] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.152] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[    22.152] (II) NVIDIA(0):     Mode Source: X Server
[    22.152] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    22.152] (II) NVIDIA(0):       HRes, HSyncStart :  640,  696
[    22.152] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
[    22.152] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    22.152] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
[    22.152] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.153] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.153] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.153] (II) NVIDIA(0):         mode validation
[    22.153] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.153] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.154] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.154] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.154] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.154] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.154] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.154] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.154] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.154] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.154] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.154] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.154] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.154] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.154] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.155] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.155] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.155] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.155] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.155] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.155] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.155] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.155] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.155] (II) NVIDIA(0):     Mode is valid.
[    22.155] (II) NVIDIA(0): 
[    22.155] (II) NVIDIA(0):   Validating Mode "320x240":
[    22.155] (II) NVIDIA(0):     320 x 240 @ 85 Hz
[    22.155] (II) NVIDIA(0):     Mode Source: X Server
[    22.155] (II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
[    22.156] (II) NVIDIA(0):       HRes, HSyncStart :  320,  348
[    22.156] (II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
[    22.156] (II) NVIDIA(0):       VRes, VSyncStart :  240,  240
[    22.156] (II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
[    22.156] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.156] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.156] (II) NVIDIA(0):     VertRefresh (85.2 Hz) out of range (57.000-63.000 Hz);
[    22.156] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.156] (II) NVIDIA(0):         mode validation
[    22.156] (II) NVIDIA(0):     BestFit Backend for "320x240": 1920x1080
[    22.156] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.157] (II) NVIDIA(GPU-0):     BestFit Centered         320x240
[    22.157] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.157] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.157] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.157] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.158] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.158] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.158] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.158] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.158] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.158] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.158] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.158] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.158] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.158] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.158] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.158] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.158] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.158] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.158] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.158] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.159] (II) NVIDIA(0):     Mode is valid.
[    22.159] (II) NVIDIA(0): 
[    22.159] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.159] (II) NVIDIA(0):     800 x 600 @ 56 Hz
[    22.159] (II) NVIDIA(0):     Mode Source: X Server
[    22.159] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    22.159] (II) NVIDIA(0):       HRes, HSyncStart :  800,  824
[    22.159] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
[    22.159] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.159] (II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
[    22.159] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.159] (II) NVIDIA(0):     VertRefresh (56.2 Hz) out of range (57.000-63.000 Hz);
[    22.159] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.159] (II) NVIDIA(0):         mode validation
[    22.160] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.160] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.161] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.161] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.161] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.161] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.161] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.161] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.161] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.161] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.161] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.161] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.161] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.161] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.162] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.162] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.162] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.162] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.162] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.162] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.162] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.162] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.162] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.162] (II) NVIDIA(0):     Mode is valid.
[    22.162] (II) NVIDIA(0): 
[    22.162] (II) NVIDIA(0):   Validating Mode "400x300":
[    22.162] (II) NVIDIA(0):     400 x 300 @ 56 Hz
[    22.162] (II) NVIDIA(0):     Mode Source: X Server
[    22.163] (II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
[    22.163] (II) NVIDIA(0):       HRes, HSyncStart :  400,  412
[    22.163] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
[    22.163] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    22.163] (II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
[    22.163] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.163] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.163] (II) NVIDIA(0):     VertRefresh (56.3 Hz) out of range (57.000-63.000 Hz);
[    22.163] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.163] (II) NVIDIA(0):         mode validation
[    22.163] (II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
[    22.163] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.164] (II) NVIDIA(GPU-0):     BestFit Centered         400x300
[    22.165] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.165] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.165] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.165] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.165] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.165] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.165] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.165] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.165] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.165] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.165] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.165] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.165] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.165] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.165] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.166] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.166] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.166] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.166] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.166] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.166] (II) NVIDIA(0):     Mode is valid.
[    22.166] (II) NVIDIA(0): 
[    22.166] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.166] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    22.166] (II) NVIDIA(0):     Mode Source: X Server
[    22.166] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[    22.166] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[    22.166] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[    22.166] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.166] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[    22.167] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.167] (II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
[    22.167] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.167] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.167] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.167] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.168] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.168] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.168] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.168] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.168] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.168] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.168] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.168] (II) NVIDIA(GPU-0):     Native Centered          800x600
[    22.169] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.169] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.169] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.169] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.169] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.169] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.169] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.169] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.169] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.169] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.169] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.169] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.169] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.169] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.169] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.169] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.170] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.170] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.170] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.170] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.170] (II) NVIDIA(0):     Mode is valid.
[    22.170] (II) NVIDIA(0): 
[    22.170] (II) NVIDIA(0):   Validating Mode "400x300":
[    22.170] (II) NVIDIA(0):     400 x 300 @ 60 Hz
[    22.170] (II) NVIDIA(0):     Mode Source: X Server
[    22.170] (II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
[    22.170] (II) NVIDIA(0):       HRes, HSyncStart :  400,  420
[    22.170] (II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
[    22.170] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    22.170] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
[    22.170] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.171] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.171] (II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
[    22.171] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.171] (II) NVIDIA(GPU-0):     BestFit Centered         400x300
[    22.172] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.172] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.172] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.172] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.172] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.172] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.172] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.172] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.172] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.172] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.172] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.172] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.172] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.173] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.173] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.173] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.173] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.173] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.173] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.173] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.173] (II) NVIDIA(0):     Mode is valid.
[    22.173] (II) NVIDIA(0): 
[    22.173] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.173] (II) NVIDIA(0):     800 x 600 @ 72 Hz
[    22.173] (II) NVIDIA(0):     Mode Source: X Server
[    22.173] (II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
[    22.173] (II) NVIDIA(0):       HRes, HSyncStart :  800,  856
[    22.174] (II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
[    22.174] (II) NVIDIA(0):       VRes, VSyncStart :  600,  637
[    22.174] (II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
[    22.174] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.174] (II) NVIDIA(0):     VertRefresh (72.2 Hz) out of range (57.000-63.000 Hz);
[    22.174] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.174] (II) NVIDIA(0):         mode validation
[    22.174] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.174] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.175] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.175] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.175] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.175] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.175] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.175] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.175] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.176] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.176] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.176] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.176] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.176] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.176] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.176] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.176] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.176] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.176] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.176] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.176] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.176] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.176] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.177] (II) NVIDIA(0):     Mode is valid.
[    22.177] (II) NVIDIA(0): 
[    22.177] (II) NVIDIA(0):   Validating Mode "400x300":
[    22.177] (II) NVIDIA(0):     400 x 300 @ 72 Hz
[    22.177] (II) NVIDIA(0):     Mode Source: X Server
[    22.177] (II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
[    22.177] (II) NVIDIA(0):       HRes, HSyncStart :  400,  428
[    22.177] (II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
[    22.177] (II) NVIDIA(0):       VRes, VSyncStart :  300,  318
[    22.177] (II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
[    22.177] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.177] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.177] (II) NVIDIA(0):     VertRefresh (72.2 Hz) out of range (57.000-63.000 Hz);
[    22.178] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.178] (II) NVIDIA(0):         mode validation
[    22.178] (II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
[    22.178] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.179] (II) NVIDIA(GPU-0):     BestFit Centered         400x300
[    22.179] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.179] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.179] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.179] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.179] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.179] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.179] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.179] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.179] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.179] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.179] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.180] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.180] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.180] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.180] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.180] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.180] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.180] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.180] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.181] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.181] (II) NVIDIA(0):     Mode is valid.
[    22.181] (II) NVIDIA(0): 
[    22.181] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.181] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[    22.181] (II) NVIDIA(0):     Mode Source: X Server
[    22.181] (II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
[    22.188] (II) NVIDIA(0):       HRes, HSyncStart :  800,  816
[    22.188] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
[    22.188] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.188] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
[    22.188] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.189] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.189] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.189] (II) NVIDIA(0):         mode validation
[    22.189] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.189] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.190] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.190] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.190] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.190] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.190] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.190] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.190] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.190] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.190] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.190] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.190] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.191] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.191] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.191] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.191] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.191] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.191] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.191] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.191] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.191] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.191] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.191] (II) NVIDIA(0):     Mode is valid.
[    22.191] (II) NVIDIA(0): 
[    22.191] (II) NVIDIA(0):   Validating Mode "400x300":
[    22.191] (II) NVIDIA(0):     400 x 300 @ 75 Hz
[    22.192] (II) NVIDIA(0):     Mode Source: X Server
[    22.192] (II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
[    22.192] (II) NVIDIA(0):       HRes, HSyncStart :  400,  408
[    22.192] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
[    22.192] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    22.192] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
[    22.192] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.192] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.192] (II) NVIDIA(0):     VertRefresh (75.1 Hz) out of range (57.000-63.000 Hz);
[    22.192] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.192] (II) NVIDIA(0):         mode validation
[    22.192] (II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
[    22.192] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.193] (II) NVIDIA(GPU-0):     BestFit Centered         400x300
[    22.194] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.194] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.194] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.194] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.194] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.194] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.194] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.194] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.194] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.194] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.194] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.194] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.194] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.194] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.194] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.195] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.195] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.195] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.195] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.195] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.195] (II) NVIDIA(0):     Mode is valid.
[    22.195] (II) NVIDIA(0): 
[    22.195] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.195] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[    22.195] (II) NVIDIA(0):     Mode Source: X Server
[    22.195] (II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
[    22.195] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
[    22.195] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
[    22.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.196] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.196] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.196] (II) NVIDIA(0):         mode validation
[    22.196] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.196] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.199] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.199] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.199] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.199] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.199] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.199] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.199] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.199] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.199] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.199] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.199] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.199] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.199] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.200] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.200] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.200] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.200] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.200] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.200] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.200] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.200] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.200] (II) NVIDIA(0):     Mode is valid.
[    22.200] (II) NVIDIA(0): 
[    22.200] (II) NVIDIA(0):   Validating Mode "400x300":
[    22.200] (II) NVIDIA(0):     400 x 300 @ 85 Hz
[    22.200] (II) NVIDIA(0):     Mode Source: X Server
[    22.200] (II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
[    22.201] (II) NVIDIA(0):       HRes, HSyncStart :  400,  416
[    22.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
[    22.201] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    22.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
[    22.201] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.201] (II) NVIDIA(0):     VertRefresh (85.3 Hz) out of range (57.000-63.000 Hz);
[    22.201] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.201] (II) NVIDIA(0):         mode validation
[    22.201] (II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
[    22.201] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.202] (II) NVIDIA(GPU-0):     BestFit Centered         400x300
[    22.202] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.202] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.203] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.203] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.203] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.203] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.203] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.203] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.203] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.203] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.203] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.203] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.203] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.203] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.203] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.203] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.203] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.204] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.204] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.204] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.204] (II) NVIDIA(0):     Mode is valid.
[    22.204] (II) NVIDIA(0): 
[    22.204] (II) NVIDIA(0):   Validating Mode "1024x768i":
[    22.204] (II) NVIDIA(0):     1024 x 768 @ 87 Hz
[    22.207] (II) NVIDIA(0):     Mode Source: X Server
[    22.207] (II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
[    22.207] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
[    22.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
[    22.207] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    22.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
[    22.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.207] (II) NVIDIA(0):       Extra            : Interlace
[    22.207] (II) NVIDIA(0):     VertRefresh (87.0 Hz) out of range (57.000-63.000 Hz);
[    22.207] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.207] (II) NVIDIA(0):         mode validation
[    22.208] (II) NVIDIA(0):     BestFit Backend for "1024x768i": 1920x1080
[    22.208] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.209] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.209] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.209] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.209] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.209] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.209] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.209] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.209] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.209] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.209] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.209] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.209] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.209] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.209] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.210] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.210] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.210] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.210] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.210] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.210] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.210] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.210] (II) NVIDIA(0):     Mode is valid.
[    22.210] (II) NVIDIA(0): 
[    22.210] (II) NVIDIA(0):   Validating Mode "512x384i":
[    22.210] (II) NVIDIA(0):     512 x 384 @ 87 Hz
[    22.210] (II) NVIDIA(0):     Mode Source: X Server
[    22.210] (II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
[    22.210] (II) NVIDIA(0):       HRes, HSyncStart :  512,  516
[    22.211] (II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
[    22.211] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[    22.211] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
[    22.211] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.211] (II) NVIDIA(0):       Extra            : Interlace DoubleScan
[    22.211] (II) NVIDIA(0):     VertRefresh (87.1 Hz) out of range (57.000-63.000 Hz);
[    22.211] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.211] (II) NVIDIA(0):         mode validation
[    22.211] (II) NVIDIA(0):     BestFit Backend for "512x384i": 1920x1080
[    22.211] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.212] (II) NVIDIA(GPU-0):     BestFit Centered         512x384
[    22.212] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.212] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.212] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.212] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.213] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.213] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.213] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.213] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.213] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.213] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.213] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.213] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.213] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.213] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.213] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.213] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.213] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.213] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.214] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.214] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.214] (II) NVIDIA(0):     Mode is valid.
[    22.214] (II) NVIDIA(0): 
[    22.214] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.214] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    22.214] (II) NVIDIA(0):     Mode Source: X Server
[    22.214] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[    22.214] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    22.214] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[    22.214] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.214] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    22.214] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.214] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
[    22.215] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.215] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.215] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.215] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.216] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.216] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.216] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.216] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.216] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.216] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.216] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.216] (II) NVIDIA(GPU-0):     Native Centered          1024x768
[    22.217] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.217] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.217] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.217] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.217] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.217] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.217] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.217] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.217] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.217] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.217] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.217] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.217] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.217] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.217] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.217] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.218] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.218] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.218] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.218] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.218] (II) NVIDIA(0):     Mode is valid.
[    22.218] (II) NVIDIA(0): 
[    22.218] (II) NVIDIA(0):   Validating Mode "512x384":
[    22.218] (II) NVIDIA(0):     512 x 384 @ 60 Hz
[    22.218] (II) NVIDIA(0):     Mode Source: X Server
[    22.218] (II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
[    22.218] (II) NVIDIA(0):       HRes, HSyncStart :  512,  524
[    22.218] (II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
[    22.218] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    22.218] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
[    22.218] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.218] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.219] (II) NVIDIA(0):     BestFit Backend for "512x384": 1920x1080
[    22.219] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.220] (II) NVIDIA(GPU-0):     BestFit Centered         512x384
[    22.220] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.220] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.220] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.220] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.220] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.220] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.220] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.220] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.220] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.220] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.220] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.220] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.220] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.221] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.221] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.221] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.221] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.221] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.221] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.221] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.221] (II) NVIDIA(0):     Mode is valid.
[    22.221] (II) NVIDIA(0): 
[    22.221] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.221] (II) NVIDIA(0):     1024 x 768 @ 70 Hz
[    22.221] (II) NVIDIA(0):     Mode Source: X Server
[    22.221] (II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
[    22.221] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    22.222] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
[    22.222] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.222] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    22.222] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.222] (II) NVIDIA(0):     VertRefresh (70.1 Hz) out of range (57.000-63.000 Hz);
[    22.222] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.222] (II) NVIDIA(0):         mode validation
[    22.222] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.222] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.223] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.223] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.223] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.223] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.223] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.223] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.223] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.223] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.224] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.224] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.224] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.224] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.224] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.224] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.224] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.224] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.224] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.224] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.224] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.224] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.224] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.224] (II) NVIDIA(0):     Mode is valid.
[    22.224] (II) NVIDIA(0): 
[    22.225] (II) NVIDIA(0):   Validating Mode "512x384":
[    22.225] (II) NVIDIA(0):     512 x 384 @ 70 Hz
[    22.225] (II) NVIDIA(0):     Mode Source: X Server
[    22.225] (II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
[    22.225] (II) NVIDIA(0):       HRes, HSyncStart :  512,  524
[    22.225] (II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
[    22.225] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    22.225] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
[    22.225] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.225] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.225] (II) NVIDIA(0):     VertRefresh (70.1 Hz) out of range (57.000-63.000 Hz);
[    22.225] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.225] (II) NVIDIA(0):         mode validation
[    22.225] (II) NVIDIA(0):     BestFit Backend for "512x384": 1920x1080
[    22.226] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.227] (II) NVIDIA(GPU-0):     BestFit Centered         512x384
[    22.227] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.227] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.227] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.227] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.227] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.227] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.227] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.227] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.227] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.227] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.227] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.227] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.228] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.228] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.228] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.228] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.228] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.228] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.228] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.228] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.228] (II) NVIDIA(0):     Mode is valid.
[    22.228] (II) NVIDIA(0): 
[    22.228] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.228] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[    22.228] (II) NVIDIA(0):     Mode Source: X Server
[    22.228] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[    22.228] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
[    22.229] (II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
[    22.229] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    22.229] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
[    22.229] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.229] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.229] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.229] (II) NVIDIA(0):         mode validation
[    22.229] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.229] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.230] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.230] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.230] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.230] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.230] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.230] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.230] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.231] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.231] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.231] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.231] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.231] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.231] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.231] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.231] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.231] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.231] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.231] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.231] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.231] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.231] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.231] (II) NVIDIA(0):     Mode is valid.
[    22.231] (II) NVIDIA(0): 
[    22.232] (II) NVIDIA(0):   Validating Mode "512x384":
[    22.232] (II) NVIDIA(0):     512 x 384 @ 75 Hz
[    22.232] (II) NVIDIA(0):     Mode Source: X Server
[    22.232] (II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
[    22.232] (II) NVIDIA(0):       HRes, HSyncStart :  512,  520
[    22.232] (II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
[    22.232] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[    22.232] (II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
[    22.232] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.232] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.232] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.232] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.232] (II) NVIDIA(0):         mode validation
[    22.232] (II) NVIDIA(0):     BestFit Backend for "512x384": 1920x1080
[    22.233] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.233] (II) NVIDIA(GPU-0):     BestFit Centered         512x384
[    22.234] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.234] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.234] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.234] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.234] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.234] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.234] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.234] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.234] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.234] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.234] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.234] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.234] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.234] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.235] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.235] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.235] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.235] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.235] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.235] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.235] (II) NVIDIA(0):     Mode is valid.
[    22.235] (II) NVIDIA(0): 
[    22.235] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.235] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[    22.235] (II) NVIDIA(0):     Mode Source: X Server
[    22.235] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[    22.235] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
[    22.235] (II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
[    22.235] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    22.236] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
[    22.236] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.236] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.236] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.236] (II) NVIDIA(0):         mode validation
[    22.236] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.236] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.237] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.237] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.237] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.237] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.237] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.237] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.237] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.238] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.238] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.238] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.238] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.238] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.238] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.238] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.238] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.238] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.238] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.238] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.238] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.238] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.238] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.238] (II) NVIDIA(0):     Mode is valid.
[    22.239] (II) NVIDIA(0): 
[    22.239] (II) NVIDIA(0):   Validating Mode "512x384":
[    22.239] (II) NVIDIA(0):     512 x 384 @ 85 Hz
[    22.239] (II) NVIDIA(0):     Mode Source: X Server
[    22.239] (II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
[    22.239] (II) NVIDIA(0):       HRes, HSyncStart :  512,  536
[    22.239] (II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
[    22.239] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[    22.239] (II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
[    22.239] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.239] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.239] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.239] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.240] (II) NVIDIA(0):         mode validation
[    22.240] (II) NVIDIA(0):     BestFit Backend for "512x384": 1920x1080
[    22.240] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.241] (II) NVIDIA(GPU-0):     BestFit Centered         512x384
[    22.241] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.241] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.241] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.241] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.241] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.241] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.241] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.241] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.241] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.241] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.241] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.241] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.241] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.242] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.242] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.242] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.242] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.242] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.242] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.242] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.242] (II) NVIDIA(0):     Mode is valid.
[    22.242] (II) NVIDIA(0): 
[    22.242] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.242] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[    22.242] (II) NVIDIA(0):     Mode Source: X Server
[    22.242] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.242] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    22.242] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
[    22.243] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.243] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[    22.243] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.243] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.243] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.243] (II) NVIDIA(0):         mode validation
[    22.243] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.243] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.244] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.244] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.244] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.244] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.244] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.244] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.244] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.244] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.245] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.245] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.245] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.245] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.245] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.245] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.245] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.245] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.245] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.245] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.245] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.245] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.245] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.245] (II) NVIDIA(0):     Mode is valid.
[    22.245] (II) NVIDIA(0): 
[    22.246] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.246] (II) NVIDIA(0):     576 x 432 @ 75 Hz
[    22.246] (II) NVIDIA(0):     Mode Source: X Server
[    22.246] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[    22.246] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[    22.246] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
[    22.246] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.246] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
[    22.246] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.246] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.246] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.246] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.246] (II) NVIDIA(0):         mode validation
[    22.246] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.246] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.247] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.247] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.248] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.248] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.248] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.248] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.248] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.248] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.248] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.248] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.249] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.249] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.249] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.249] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.249] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.249] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.249] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.249] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.249] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.249] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.249] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.249] (II) NVIDIA(0):     Mode is valid.
[    22.249] (II) NVIDIA(0): 
[    22.249] (II) NVIDIA(0):   Validating Mode "1280x960":
[    22.249] (II) NVIDIA(0):     1280 x 960 @ 60 Hz
[    22.250] (II) NVIDIA(0):     Mode Source: X Server
[    22.250] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.250] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
[    22.250] (II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
[    22.250] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    22.250] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
[    22.250] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.250] (II) NVIDIA(0):     BestFit Backend for "1280x960": 1920x1080
[    22.250] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.251] (II) NVIDIA(GPU-0):     BestFit Centered         1280x960
[    22.251] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.251] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.251] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.251] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.251] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.251] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.251] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.252] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.252] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.252] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.252] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.252] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.252] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.252] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.252] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.252] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.252] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.252] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.252] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.252] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.252] (II) NVIDIA(0):     Mode is valid.
[    22.252] (II) NVIDIA(0): 
[    22.252] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.253] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    22.253] (II) NVIDIA(0):     Mode Source: X Server
[    22.253] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[    22.253] (II) NVIDIA(0):       HRes, HSyncStart :  640,  688
[    22.253] (II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
[    22.253] (II) NVIDIA(0):       VRes, VSyncStart :  480,  480
[    22.253] (II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
[    22.253] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.253] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.253] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.253] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.254] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.254] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.254] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.254] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.254] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.254] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.254] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.254] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.255] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.255] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.255] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.255] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.255] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.255] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.255] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.255] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.255] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.255] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.255] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.255] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.255] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.255] (II) NVIDIA(0):     Mode is valid.
[    22.255] (II) NVIDIA(0): 
[    22.256] (II) NVIDIA(0):   Validating Mode "1280x960":
[    22.256] (II) NVIDIA(0):     1280 x 960 @ 85 Hz
[    22.256] (II) NVIDIA(0):     Mode Source: X Server
[    22.256] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    22.256] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    22.256] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    22.256] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    22.256] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
[    22.256] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.256] (II) NVIDIA(0):     HorizSync (85.9 kHz) out of range (31.000-82.000 kHz);
[    22.256] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.256] (II) NVIDIA(0):         mode validation
[    22.256] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.257] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.257] (II) NVIDIA(0):         mode validation
[    22.257] (II) NVIDIA(0):     BestFit Backend for "1280x960": 1920x1080
[    22.257] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.258] (II) NVIDIA(GPU-0):     BestFit Centered         1280x960
[    22.258] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.258] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.258] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.258] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.258] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.258] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.258] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.258] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.258] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.258] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.258] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.258] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.259] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.259] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.259] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.259] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.259] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.259] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.259] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.259] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.259] (II) NVIDIA(0):     Mode is valid.
[    22.259] (II) NVIDIA(0): 
[    22.259] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.259] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[    22.259] (II) NVIDIA(0):     Mode Source: X Server
[    22.259] (II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
[    22.260] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    22.260] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
[    22.260] (II) NVIDIA(0):       VRes, VSyncStart :  480,  480
[    22.260] (II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
[    22.260] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.260] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.260] (II) NVIDIA(0):     HorizSync (85.9 kHz) out of range (31.000-82.000 kHz);
[    22.262] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.262] (II) NVIDIA(0):         mode validation
[    22.263] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.263] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.263] (II) NVIDIA(0):         mode validation
[    22.263] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.263] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.264] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.264] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.264] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.264] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.264] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.264] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.264] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.264] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.264] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.264] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.265] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.265] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.265] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.265] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.265] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.265] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.265] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.265] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.265] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.265] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.265] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.265] (II) NVIDIA(0):     Mode is valid.
[    22.265] (II) NVIDIA(0): 
[    22.265] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.266] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[    22.266] (II) NVIDIA(0):     Mode Source: X Server
[    22.266] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.266] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[    22.266] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    22.266] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.266] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    22.266] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.266] (II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
[    22.266] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.266] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.266] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.266] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.268] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.268] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.268] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.268] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.268] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.268] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.268] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.268] (II) NVIDIA(GPU-0):     Native Centered          1280x1024
[    22.268] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.268] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.268] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.268] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.269] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.269] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.269] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.269] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.269] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.269] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.269] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.269] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.269] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.269] (II) NVIDIA(GPU-0):     Native AspectScaled      1350x1080
[    22.269] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.269] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.269] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.269] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.269] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.270] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.270] (II) NVIDIA(0):     Mode is valid.
[    22.270] (II) NVIDIA(0): 
[    22.270] (II) NVIDIA(0):   Validating Mode "640x512":
[    22.270] (II) NVIDIA(0):     640 x 512 @ 60 Hz
[    22.270] (II) NVIDIA(0):     Mode Source: X Server
[    22.270] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[    22.270] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[    22.270] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
[    22.270] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    22.270] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
[    22.270] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.270] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.270] (II) NVIDIA(0):     BestFit Backend for "640x512": 1920x1080
[    22.271] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.271] (II) NVIDIA(GPU-0):     BestFit Centered         640x512
[    22.272] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.272] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.272] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.272] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.272] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.272] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.272] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.272] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.273] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.273] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.273] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.273] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.273] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.273] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.273] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.273] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.273] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.273] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.273] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.273] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.273] (II) NVIDIA(0):     Mode is valid.
[    22.273] (II) NVIDIA(0): 
[    22.273] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.274] (II) NVIDIA(0):     1280 x 1024 @ 75 Hz
[    22.274] (II) NVIDIA(0):     Mode Source: X Server
[    22.274] (II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
[    22.274] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
[    22.274] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    22.274] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.274] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    22.274] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.274] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.274] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.274] (II) NVIDIA(0):         mode validation
[    22.274] (II) NVIDIA(0):     BestFit Backend for "1280x1024": 1920x1080
[    22.274] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.275] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.275] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.276] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.276] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.276] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.276] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.276] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.276] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.276] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.276] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.276] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.276] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.276] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.276] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.276] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.276] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.277] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.277] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.277] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.277] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.277] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.277] (II) NVIDIA(0):     Mode is valid.
[    22.277] (II) NVIDIA(0): 
[    22.277] (II) NVIDIA(0):   Validating Mode "640x512":
[    22.277] (II) NVIDIA(0):     640 x 512 @ 75 Hz
[    22.277] (II) NVIDIA(0):     Mode Source: X Server
[    22.277] (II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
[    22.277] (II) NVIDIA(0):       HRes, HSyncStart :  640,  648
[    22.277] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
[    22.277] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    22.278] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
[    22.278] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.278] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.278] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.278] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.278] (II) NVIDIA(0):         mode validation
[    22.278] (II) NVIDIA(0):     BestFit Backend for "640x512": 1920x1080
[    22.278] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.279] (II) NVIDIA(GPU-0):     BestFit Centered         640x512
[    22.279] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.279] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.279] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.279] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.279] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.279] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.280] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.280] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.280] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.280] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.280] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.280] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.280] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.280] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.280] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.281] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.281] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.281] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.281] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.281] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.281] (II) NVIDIA(0):     Mode is valid.
[    22.281] (II) NVIDIA(0): 
[    22.281] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.281] (II) NVIDIA(0):     1280 x 1024 @ 85 Hz
[    22.281] (II) NVIDIA(0):     Mode Source: X Server
[    22.281] (II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
[    22.281] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    22.281] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    22.281] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.282] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
[    22.282] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.282] (II) NVIDIA(0):     HorizSync (91.1 kHz) out of range (31.000-82.000 kHz);
[    22.282] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.282] (II) NVIDIA(0):         mode validation
[    22.282] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.282] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.282] (II) NVIDIA(0):         mode validation
[    22.282] (II) NVIDIA(0):     BestFit Backend for "1280x1024": 1920x1080
[    22.282] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.283] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.283] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.283] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.283] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.284] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.284] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.284] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.284] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.284] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.284] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.284] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.284] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.284] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.284] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.284] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.284] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.284] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.284] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.284] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.285] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.285] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.285] (II) NVIDIA(0):     Mode is valid.
[    22.285] (II) NVIDIA(0): 
[    22.285] (II) NVIDIA(0):   Validating Mode "640x512":
[    22.285] (II) NVIDIA(0):     640 x 512 @ 85 Hz
[    22.285] (II) NVIDIA(0):     Mode Source: X Server
[    22.285] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[    22.285] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    22.285] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
[    22.285] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    22.285] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
[    22.285] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.285] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.285] (II) NVIDIA(0):     HorizSync (91.1 kHz) out of range (31.000-82.000 kHz);
[    22.285] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.286] (II) NVIDIA(0):         mode validation
[    22.286] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.286] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.286] (II) NVIDIA(0):         mode validation
[    22.286] (II) NVIDIA(0):     BestFit Backend for "640x512": 1920x1080
[    22.286] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.287] (II) NVIDIA(GPU-0):     BestFit Centered         640x512
[    22.287] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.287] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.287] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.287] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.287] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.287] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.287] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.287] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.287] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.287] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.287] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.288] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.288] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.288] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.288] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.288] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.288] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.288] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.288] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.288] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.289] (II) NVIDIA(0):     Mode is valid.
[    22.289] (II) NVIDIA(0): 
[    22.289] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.289] (II) NVIDIA(0):     1600 x 1200 @ 60 Hz
[    22.289] (II) NVIDIA(0):     Mode Source: X Server
[    22.289] (II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
[    22.289] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.289] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.289] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.289] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.289] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.289] (WW) NVIDIA(0):     Mode is rejected: PixelClock (162.0 MHz) too high for EDID
[    22.289] (WW) NVIDIA(0):     (EDID Max: 160.0 MHz).
[    22.290] (II) NVIDIA(0): 
[    22.290] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.290] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    22.290] (II) NVIDIA(0):     Mode Source: X Server
[    22.290] (II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
[    22.290] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.290] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    22.290] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    22.290] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    22.290] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.290] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.290] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.290] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.291] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.291] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.291] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.292] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.292] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.292] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.292] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.292] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.292] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.292] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.292] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.292] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.292] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.292] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.292] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.292] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.292] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.292] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.293] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.293] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.293] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.293] (II) NVIDIA(0):     Mode is valid.
[    22.293] (II) NVIDIA(0): 
[    22.293] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.293] (II) NVIDIA(0):     1600 x 1200 @ 65 Hz
[    22.293] (II) NVIDIA(0):     Mode Source: X Server
[    22.293] (II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
[    22.293] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.293] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.293] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.293] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.293] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.294] (WW) NVIDIA(0):     Mode is rejected: PixelClock (175.5 MHz) too high for
[    22.294] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.294] (II) NVIDIA(0): 
[    22.294] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.294] (II) NVIDIA(0):     800 x 600 @ 65 Hz
[    22.294] (II) NVIDIA(0):     Mode Source: X Server
[    22.294] (II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
[    22.294] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.294] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    22.294] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    22.294] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    22.294] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.294] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.294] (II) NVIDIA(0):     VertRefresh (65.0 Hz) out of range (57.000-63.000 Hz);
[    22.294] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.295] (II) NVIDIA(0):         mode validation
[    22.295] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.295] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.296] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.296] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.296] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.296] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.296] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.296] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.298] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.298] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.298] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.298] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.298] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.298] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.298] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.298] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.298] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.298] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.298] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.299] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.299] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.299] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.299] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.299] (II) NVIDIA(0):     Mode is valid.
[    22.299] (II) NVIDIA(0): 
[    22.299] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.299] (II) NVIDIA(0):     1600 x 1200 @ 70 Hz
[    22.299] (II) NVIDIA(0):     Mode Source: X Server
[    22.299] (II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
[    22.299] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.299] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.299] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.299] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.299] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.300] (WW) NVIDIA(0):     Mode is rejected: PixelClock (189.0 MHz) too high for
[    22.300] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.300] (II) NVIDIA(0): 
[    22.300] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.300] (II) NVIDIA(0):     800 x 600 @ 70 Hz
[    22.300] (II) NVIDIA(0):     Mode Source: X Server
[    22.300] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[    22.300] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.300] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    22.300] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    22.300] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    22.300] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.300] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.300] (II) NVIDIA(0):     HorizSync (87.5 kHz) out of range (31.000-82.000 kHz);
[    22.300] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.300] (II) NVIDIA(0):         mode validation
[    22.301] (II) NVIDIA(0):     VertRefresh (70.0 Hz) out of range (57.000-63.000 Hz);
[    22.301] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.301] (II) NVIDIA(0):         mode validation
[    22.301] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.301] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.302] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.302] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.302] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.302] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.302] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.302] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.302] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.302] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.302] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.302] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.302] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.302] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.303] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.303] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.303] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.303] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.303] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.303] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.303] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.303] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.303] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.303] (II) NVIDIA(0):     Mode is valid.
[    22.303] (II) NVIDIA(0): 
[    22.303] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.303] (II) NVIDIA(0):     1600 x 1200 @ 75 Hz
[    22.303] (II) NVIDIA(0):     Mode Source: X Server
[    22.303] (II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
[    22.303] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.304] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.304] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.304] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.304] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.304] (WW) NVIDIA(0):     Mode is rejected: PixelClock (202.5 MHz) too high for
[    22.304] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.304] (II) NVIDIA(0): 
[    22.304] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.307] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[    22.307] (II) NVIDIA(0):     Mode Source: X Server
[    22.308] (II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
[    22.308] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.308] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    22.308] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    22.308] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    22.308] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.308] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.308] (II) NVIDIA(0):     HorizSync (93.8 kHz) out of range (31.000-82.000 kHz);
[    22.308] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.308] (II) NVIDIA(0):         mode validation
[    22.308] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.308] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.308] (II) NVIDIA(0):         mode validation
[    22.309] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.309] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.310] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.310] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.310] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.310] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.310] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.310] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.310] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.310] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.310] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.310] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.310] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.310] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.310] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.311] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.311] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.311] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.311] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.311] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.311] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.311] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.311] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.311] (II) NVIDIA(0):     Mode is valid.
[    22.311] (II) NVIDIA(0): 
[    22.311] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.311] (II) NVIDIA(0):     1600 x 1200 @ 85 Hz
[    22.311] (II) NVIDIA(0):     Mode Source: X Server
[    22.311] (II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
[    22.312] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.312] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.312] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.312] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.312] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.312] (WW) NVIDIA(0):     Mode is rejected: PixelClock (229.5 MHz) too high for
[    22.312] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.312] (II) NVIDIA(0): 
[    22.312] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.312] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[    22.312] (II) NVIDIA(0):     Mode Source: X Server
[    22.312] (II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
[    22.312] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.312] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    22.312] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    22.313] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    22.313] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.313] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.313] (II) NVIDIA(0):     HorizSync (106.2 kHz) out of range (31.000-82.000 kHz);
[    22.313] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.313] (II) NVIDIA(0):         mode validation
[    22.313] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.313] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.313] (II) NVIDIA(0):         mode validation
[    22.313] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.313] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.314] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.314] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.314] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.314] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.315] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.315] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.315] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.315] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.315] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.315] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.315] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.315] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.315] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.315] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.315] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.315] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.315] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.315] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.315] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.316] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.316] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.316] (II) NVIDIA(0):     Mode is valid.
[    22.316] (II) NVIDIA(0): 
[    22.316] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    22.316] (II) NVIDIA(0):     1792 x 1344 @ 60 Hz
[    22.316] (II) NVIDIA(0):     Mode Source: X Server
[    22.316] (II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
[    22.317] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
[    22.317] (II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
[    22.317] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    22.317] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
[    22.317] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.317] (WW) NVIDIA(0):     Mode is rejected: PixelClock (204.8 MHz) too high for
[    22.317] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.317] (II) NVIDIA(0): 
[    22.317] (II) NVIDIA(0):   Validating Mode "896x672":
[    22.317] (II) NVIDIA(0):     896 x 672 @ 60 Hz
[    22.317] (II) NVIDIA(0):     Mode Source: X Server
[    22.317] (II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
[    22.317] (II) NVIDIA(0):       HRes, HSyncStart :  896,  960
[    22.317] (II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
[    22.317] (II) NVIDIA(0):       VRes, VSyncStart :  672,  672
[    22.318] (II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
[    22.318] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.318] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.318] (II) NVIDIA(0):     HorizSync (83.7 kHz) out of range (31.000-82.000 kHz);
[    22.318] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.319] (II) NVIDIA(0):         mode validation
[    22.319] (II) NVIDIA(0):     BestFit Backend for "896x672": 1920x1080
[    22.319] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.320] (II) NVIDIA(GPU-0):     BestFit Centered         896x672
[    22.320] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.320] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.320] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.320] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.320] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.320] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.320] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.320] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.320] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.320] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.321] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.321] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.321] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.321] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.321] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.321] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.321] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.321] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.321] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.321] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.321] (II) NVIDIA(0):     Mode is valid.
[    22.321] (II) NVIDIA(0): 
[    22.321] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    22.321] (II) NVIDIA(0):     1792 x 1344 @ 75 Hz
[    22.321] (II) NVIDIA(0):     Mode Source: X Server
[    22.322] (II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
[    22.322] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
[    22.322] (II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
[    22.322] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    22.322] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
[    22.322] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.322] (WW) NVIDIA(0):     Mode is rejected: PixelClock (261.0 MHz) too high for
[    22.322] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.322] (II) NVIDIA(0): 
[    22.322] (II) NVIDIA(0):   Validating Mode "896x672":
[    22.322] (II) NVIDIA(0):     896 x 672 @ 75 Hz
[    22.322] (II) NVIDIA(0):     Mode Source: X Server
[    22.322] (II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
[    22.322] (II) NVIDIA(0):       HRes, HSyncStart :  896,  944
[    22.323] (II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
[    22.323] (II) NVIDIA(0):       VRes, VSyncStart :  672,  672
[    22.323] (II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
[    22.323] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.323] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.323] (II) NVIDIA(0):     HorizSync (106.3 kHz) out of range (31.000-82.000 kHz);
[    22.323] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.323] (II) NVIDIA(0):         mode validation
[    22.323] (II) NVIDIA(0):     VertRefresh (75.1 Hz) out of range (57.000-63.000 Hz);
[    22.323] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.323] (II) NVIDIA(0):         mode validation
[    22.323] (II) NVIDIA(0):     BestFit Backend for "896x672": 1920x1080
[    22.323] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.324] (II) NVIDIA(GPU-0):     BestFit Centered         896x672
[    22.325] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.325] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.325] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.325] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.325] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.325] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.325] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.325] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.325] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.325] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.325] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.325] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.325] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.325] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.325] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.326] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.326] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.326] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.326] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.326] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.326] (II) NVIDIA(0):     Mode is valid.
[    22.326] (II) NVIDIA(0): 
[    22.326] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    22.326] (II) NVIDIA(0):     1856 x 1392 @ 60 Hz
[    22.326] (II) NVIDIA(0):     Mode Source: X Server
[    22.326] (II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
[    22.326] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
[    22.326] (II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
[    22.326] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    22.327] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
[    22.327] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.327] (WW) NVIDIA(0):     Mode is rejected: PixelClock (218.3 MHz) too high for
[    22.327] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.327] (II) NVIDIA(0): 
[    22.327] (II) NVIDIA(0):   Validating Mode "928x696":
[    22.327] (II) NVIDIA(0):     928 x 696 @ 60 Hz
[    22.327] (II) NVIDIA(0):     Mode Source: X Server
[    22.327] (II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
[    22.327] (II) NVIDIA(0):       HRes, HSyncStart :  928,  976
[    22.327] (II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
[    22.327] (II) NVIDIA(0):       VRes, VSyncStart :  696,  696
[    22.327] (II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
[    22.327] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.327] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.328] (II) NVIDIA(0):     HorizSync (86.4 kHz) out of range (31.000-82.000 kHz);
[    22.328] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.328] (II) NVIDIA(0):         mode validation
[    22.328] (II) NVIDIA(0):     BestFit Backend for "928x696": 1920x1080
[    22.328] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.332] (II) NVIDIA(GPU-0):     BestFit Centered         928x696
[    22.333] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.333] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.333] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.333] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.333] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.333] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.333] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.333] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.333] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.333] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.333] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.333] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.333] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.333] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.334] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.334] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.334] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.334] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.334] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.334] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.334] (II) NVIDIA(0):     Mode is valid.
[    22.334] (II) NVIDIA(0): 
[    22.334] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    22.334] (II) NVIDIA(0):     1856 x 1392 @ 75 Hz
[    22.334] (II) NVIDIA(0):     Mode Source: X Server
[    22.334] (II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
[    22.334] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
[    22.334] (II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
[    22.335] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    22.335] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
[    22.335] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.335] (WW) NVIDIA(0):     Mode is rejected: PixelClock (288.0 MHz) too high for
[    22.335] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.335] (II) NVIDIA(0): 
[    22.335] (II) NVIDIA(0):   Validating Mode "928x696":
[    22.335] (II) NVIDIA(0):     928 x 696 @ 75 Hz
[    22.335] (II) NVIDIA(0):     Mode Source: X Server
[    22.335] (II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
[    22.335] (II) NVIDIA(0):       HRes, HSyncStart :  928,  992
[    22.335] (II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
[    22.335] (II) NVIDIA(0):       VRes, VSyncStart :  696,  696
[    22.335] (II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
[    22.335] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.336] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.336] (II) NVIDIA(0):     HorizSync (112.5 kHz) out of range (31.000-82.000 kHz);
[    22.336] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.336] (II) NVIDIA(0):         mode validation
[    22.336] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.336] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.336] (II) NVIDIA(0):         mode validation
[    22.336] (II) NVIDIA(0):     BestFit Backend for "928x696": 1920x1080
[    22.336] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.337] (II) NVIDIA(GPU-0):     BestFit Centered         928x696
[    22.337] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.337] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.337] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.337] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.337] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.338] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.338] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.338] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.338] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.338] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.338] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.338] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.338] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.338] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.338] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.338] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.338] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.338] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.338] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.338] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.338] (II) NVIDIA(0):     Mode is valid.
[    22.339] (II) NVIDIA(0): 
[    22.339] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    22.339] (II) NVIDIA(0):     1920 x 1440 @ 60 Hz
[    22.339] (II) NVIDIA(0):     Mode Source: X Server
[    22.339] (II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
[    22.339] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
[    22.339] (II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
[    22.339] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    22.339] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    22.339] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.339] (WW) NVIDIA(0):     Mode is rejected: PixelClock (234.0 MHz) too high for
[    22.339] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.339] (II) NVIDIA(0): 
[    22.339] (II) NVIDIA(0):   Validating Mode "960x720":
[    22.339] (II) NVIDIA(0):     960 x 720 @ 60 Hz
[    22.339] (II) NVIDIA(0):     Mode Source: X Server
[    22.340] (II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
[    22.340] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
[    22.340] (II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
[    22.340] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[    22.340] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
[    22.340] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.340] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.341] (II) NVIDIA(0):     HorizSync (90.0 kHz) out of range (31.000-82.000 kHz);
[    22.341] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.341] (II) NVIDIA(0):         mode validation
[    22.341] (II) NVIDIA(0):     BestFit Backend for "960x720": 1920x1080
[    22.341] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.342] (II) NVIDIA(GPU-0):     BestFit Centered         960x720
[    22.342] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.342] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.342] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.342] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.343] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.343] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.343] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.343] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.343] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.343] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.343] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.343] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.343] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.343] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.343] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.343] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.343] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.343] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.343] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.344] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.344] (II) NVIDIA(0):     Mode is valid.
[    22.344] (II) NVIDIA(0): 
[    22.344] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    22.344] (II) NVIDIA(0):     1920 x 1440 @ 75 Hz
[    22.344] (II) NVIDIA(0):     Mode Source: X Server
[    22.344] (II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
[    22.344] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
[    22.344] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
[    22.344] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    22.344] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    22.344] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.344] (WW) NVIDIA(0):     Mode is rejected: PixelClock (297.0 MHz) too high for
[    22.344] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.344] (II) NVIDIA(0): 
[    22.345] (II) NVIDIA(0):   Validating Mode "960x720":
[    22.345] (II) NVIDIA(0):     960 x 720 @ 75 Hz
[    22.345] (II) NVIDIA(0):     Mode Source: X Server
[    22.345] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    22.345] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
[    22.345] (II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
[    22.345] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[    22.345] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
[    22.345] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.345] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.345] (II) NVIDIA(0):     HorizSync (112.5 kHz) out of range (31.000-82.000 kHz);
[    22.345] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.345] (II) NVIDIA(0):         mode validation
[    22.345] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.345] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.346] (II) NVIDIA(0):         mode validation
[    22.346] (II) NVIDIA(0):     BestFit Backend for "960x720": 1920x1080
[    22.346] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.347] (II) NVIDIA(GPU-0):     BestFit Centered         960x720
[    22.347] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.347] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.347] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.347] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.347] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.347] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.347] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.347] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.347] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.347] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.347] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.347] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.348] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.348] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.348] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.348] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.348] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.348] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.348] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.348] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.348] (II) NVIDIA(0):     Mode is valid.
[    22.348] (II) NVIDIA(0): 
[    22.349] (II) NVIDIA(0):   Validating Mode "832x624":
[    22.349] (II) NVIDIA(0):     832 x 624 @ 75 Hz
[    22.349] (II) NVIDIA(0):     Mode Source: X Server
[    22.349] (II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
[    22.349] (II) NVIDIA(0):       HRes, HSyncStart :  832,  864
[    22.349] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
[    22.349] (II) NVIDIA(0):       VRes, VSyncStart :  624,  625
[    22.349] (II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
[    22.349] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.349] (II) NVIDIA(0):     VertRefresh (74.6 Hz) out of range (57.000-63.000 Hz);
[    22.349] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.349] (II) NVIDIA(0):         mode validation
[    22.349] (II) NVIDIA(0):     BestFit Backend for "832x624": 1920x1080
[    22.349] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.350] (II) NVIDIA(GPU-0):     BestFit Centered         832x624
[    22.350] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.350] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.351] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.351] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.351] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.351] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.351] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.351] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.351] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.351] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.351] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.351] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.351] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.351] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.351] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.351] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.351] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.351] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.352] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.352] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.352] (II) NVIDIA(0):     Mode is valid.
[    22.352] (II) NVIDIA(0): 
[    22.352] (II) NVIDIA(0):   Validating Mode "416x312":
[    22.352] (II) NVIDIA(0):     416 x 312 @ 75 Hz
[    22.352] (II) NVIDIA(0):     Mode Source: X Server
[    22.352] (II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
[    22.352] (II) NVIDIA(0):       HRes, HSyncStart :  416,  432
[    22.352] (II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
[    22.352] (II) NVIDIA(0):       VRes, VSyncStart :  312,  312
[    22.352] (II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
[    22.352] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.352] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.352] (II) NVIDIA(0):     VertRefresh (74.7 Hz) out of range (57.000-63.000 Hz);
[    22.353] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.353] (II) NVIDIA(0):         mode validation
[    22.353] (II) NVIDIA(0):     BestFit Backend for "416x312": 1920x1080
[    22.353] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.354] (II) NVIDIA(GPU-0):     BestFit Centered         416x312
[    22.354] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.354] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.354] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.354] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.354] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.354] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.354] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.354] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.354] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.354] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.354] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.354] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.354] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.354] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.355] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.355] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.355] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.355] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.355] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.355] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.355] (II) NVIDIA(0):     Mode is valid.
[    22.355] (II) NVIDIA(0): 
[    22.355] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.355] (II) NVIDIA(0):     1152 x 864 @ 60 Hz
[    22.355] (II) NVIDIA(0):     Mode Source: X Server
[    22.355] (II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
[    22.355] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    22.355] (II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
[    22.356] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.356] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
[    22.356] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.356] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.356] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.357] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.357] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.357] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.357] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.357] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.357] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.357] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.357] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.357] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.357] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.358] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.358] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.358] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.358] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.358] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.358] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.358] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.358] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.358] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.358] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.358] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.358] (II) NVIDIA(0):     Mode is valid.
[    22.358] (II) NVIDIA(0): 
[    22.358] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.359] (II) NVIDIA(0):     576 x 432 @ 60 Hz
[    22.359] (II) NVIDIA(0):     Mode Source: X Server
[    22.359] (II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
[    22.359] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[    22.359] (II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
[    22.359] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.359] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
[    22.359] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.359] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.359] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.359] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.363] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.363] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.363] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.363] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.363] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.363] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.364] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.364] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.364] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.364] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.364] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.364] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.364] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.364] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.364] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.364] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.364] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.364] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.364] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.364] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.365] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.365] (II) NVIDIA(0):     Mode is valid.
[    22.365] (II) NVIDIA(0): 
[    22.365] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.365] (II) NVIDIA(0):     1152 x 864 @ 70 Hz
[    22.365] (II) NVIDIA(0):     Mode Source: X Server
[    22.365] (II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
[    22.365] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[    22.365] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
[    22.365] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.365] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[    22.365] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.365] (II) NVIDIA(0):     VertRefresh (70.0 Hz) out of range (57.000-63.000 Hz);
[    22.365] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.365] (II) NVIDIA(0):         mode validation
[    22.366] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.366] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.367] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.367] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.367] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.367] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.367] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.367] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.367] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.367] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.367] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.367] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.367] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.367] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.367] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.368] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.368] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.368] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.368] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.368] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.368] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.368] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.368] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.368] (II) NVIDIA(0):     Mode is valid.
[    22.368] (II) NVIDIA(0): 
[    22.368] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.368] (II) NVIDIA(0):     576 x 432 @ 70 Hz
[    22.368] (II) NVIDIA(0):     Mode Source: X Server
[    22.369] (II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
[    22.369] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[    22.369] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
[    22.369] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.369] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
[    22.369] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.369] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.369] (II) NVIDIA(0):     VertRefresh (70.0 Hz) out of range (57.000-63.000 Hz);
[    22.369] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.369] (II) NVIDIA(0):         mode validation
[    22.369] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.369] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.370] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.370] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.370] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.371] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.371] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.371] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.371] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.371] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.371] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.371] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.371] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.371] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.371] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.371] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.371] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.371] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.371] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.371] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.372] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.372] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.372] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.372] (II) NVIDIA(0):     Mode is valid.
[    22.372] (II) NVIDIA(0): 
[    22.372] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.372] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[    22.372] (II) NVIDIA(0):     Mode Source: X Server
[    22.372] (II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
[    22.373] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[    22.373] (II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
[    22.373] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.373] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
[    22.373] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.373] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.373] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.373] (II) NVIDIA(0):         mode validation
[    22.373] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.373] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.374] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.374] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.374] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.374] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.374] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.375] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.375] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.375] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.375] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.375] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.375] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.375] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.375] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.375] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.375] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.375] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.375] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.375] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.375] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.375] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.376] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.376] (II) NVIDIA(0):     Mode is valid.
[    22.376] (II) NVIDIA(0): 
[    22.376] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.376] (II) NVIDIA(0):     576 x 432 @ 75 Hz
[    22.376] (II) NVIDIA(0):     Mode Source: X Server
[    22.376] (II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
[    22.376] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[    22.376] (II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
[    22.376] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.376] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
[    22.376] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.376] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.377] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.377] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.377] (II) NVIDIA(0):         mode validation
[    22.377] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.377] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.378] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.378] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.378] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.378] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.378] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.378] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.378] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.378] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.378] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.378] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.378] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.379] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.379] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.379] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.379] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.379] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.379] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.379] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.379] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.379] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.379] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.379] (II) NVIDIA(0):     Mode is valid.
[    22.379] (II) NVIDIA(0): 
[    22.379] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.379] (II) NVIDIA(0):     1152 x 864 @ 85 Hz
[    22.379] (II) NVIDIA(0):     Mode Source: X Server
[    22.380] (II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
[    22.380] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[    22.380] (II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
[    22.380] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.380] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
[    22.380] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.380] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.380] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.380] (II) NVIDIA(0):         mode validation
[    22.380] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.380] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.381] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.381] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.381] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.382] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.382] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.382] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.382] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.382] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.382] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.382] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.382] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.382] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.382] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.382] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.382] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.382] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.382] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.383] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.383] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.383] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.383] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.383] (II) NVIDIA(0):     Mode is valid.
[    22.383] (II) NVIDIA(0): 
[    22.383] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.383] (II) NVIDIA(0):     576 x 432 @ 85 Hz
[    22.383] (II) NVIDIA(0):     Mode Source: X Server
[    22.383] (II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
[    22.383] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[    22.383] (II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
[    22.383] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.383] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
[    22.384] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.384] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.384] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.384] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.384] (II) NVIDIA(0):         mode validation
[    22.384] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.384] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.385] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.385] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.385] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.385] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.385] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.385] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.385] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.385] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.386] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.386] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.386] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.386] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.386] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.386] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.386] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.386] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.386] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.386] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.386] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.386] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.386] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.386] (II) NVIDIA(0):     Mode is valid.
[    22.386] (II) NVIDIA(0): 
[    22.387] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.387] (II) NVIDIA(0):     1152 x 864 @ 85 Hz
[    22.387] (II) NVIDIA(0):     Mode Source: X Server
[    22.387] (II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
[    22.387] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    22.387] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
[    22.387] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.387] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
[    22.387] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.387] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.387] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.387] (II) NVIDIA(0):         mode validation
[    22.387] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.387] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.388] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.389] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.389] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.389] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.389] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.389] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.389] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.389] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.389] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.389] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.389] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.389] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.389] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.389] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.390] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.390] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.390] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.390] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.390] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.390] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.390] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.390] (II) NVIDIA(0):     Mode is valid.
[    22.390] (II) NVIDIA(0): 
[    22.390] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.390] (II) NVIDIA(0):     576 x 432 @ 85 Hz
[    22.390] (II) NVIDIA(0):     Mode Source: X Server
[    22.390] (II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
[    22.390] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[    22.391] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
[    22.391] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.391] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
[    22.391] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.391] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.391] (II) NVIDIA(0):     VertRefresh (85.2 Hz) out of range (57.000-63.000 Hz);
[    22.391] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.391] (II) NVIDIA(0):         mode validation
[    22.391] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.391] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.392] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.393] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.393] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.393] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.393] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.393] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.393] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.393] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.393] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.393] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.393] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.393] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.393] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.393] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.393] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.394] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.394] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.394] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.394] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.394] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.394] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.394] (II) NVIDIA(0):     Mode is valid.
[    22.394] (II) NVIDIA(0): 
[    22.394] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.394] (II) NVIDIA(0):     1152 x 864 @ 100 Hz
[    22.394] (II) NVIDIA(0):     Mode Source: X Server
[    22.394] (II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
[    22.394] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
[    22.394] (II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
[    22.394] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.395] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
[    22.395] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.395] (II) NVIDIA(0):     HorizSync (91.5 kHz) out of range (31.000-82.000 kHz);
[    22.395] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.395] (II) NVIDIA(0):         mode validation
[    22.395] (II) NVIDIA(0):     VertRefresh (100.0 Hz) out of range (57.000-63.000 Hz);
[    22.395] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.395] (II) NVIDIA(0):         mode validation
[    22.395] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.395] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.396] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.396] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.396] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.396] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.397] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.397] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.397] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.397] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.397] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.397] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.397] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.397] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.397] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.397] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.397] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.397] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.397] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.397] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.398] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.398] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.398] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.398] (II) NVIDIA(0):     Mode is valid.
[    22.398] (II) NVIDIA(0): 
[    22.398] (II) NVIDIA(0):   Validating Mode "576x432":
[    22.398] (II) NVIDIA(0):     576 x 432 @ 100 Hz
[    22.398] (II) NVIDIA(0):     Mode Source: X Server
[    22.398] (II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
[    22.398] (II) NVIDIA(0):       HRes, HSyncStart :  576,  616
[    22.398] (II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
[    22.398] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    22.398] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
[    22.398] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.398] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.399] (II) NVIDIA(0):     HorizSync (91.5 kHz) out of range (31.000-82.000 kHz);
[    22.399] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.399] (II) NVIDIA(0):         mode validation
[    22.399] (II) NVIDIA(0):     VertRefresh (100.1 Hz) out of range (57.000-63.000 Hz);
[    22.399] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.399] (II) NVIDIA(0):         mode validation
[    22.399] (II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
[    22.399] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.400] (II) NVIDIA(GPU-0):     BestFit Centered         576x432
[    22.400] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.400] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.400] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.400] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.400] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.400] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.401] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.401] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.401] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.401] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.401] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.401] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.401] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.401] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.401] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.401] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.401] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.401] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.401] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.401] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.402] (II) NVIDIA(0):     Mode is valid.
[    22.402] (II) NVIDIA(0): 
[    22.402] (II) NVIDIA(0):   Validating Mode "1360x768":
[    22.402] (II) NVIDIA(0):     1360 x 768 @ 60 Hz
[    22.402] (II) NVIDIA(0):     Mode Source: X Server
[    22.402] (II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
[    22.402] (II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
[    22.402] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
[    22.402] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.402] (II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
[    22.402] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.402] (II) NVIDIA(0):     BestFit Backend for "1360x768": 1920x1080
[    22.402] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.403] (II) NVIDIA(GPU-0):     BestFit Centered         1360x768
[    22.403] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.403] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.403] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.403] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.404] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.404] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.404] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.404] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.404] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.404] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.404] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.404] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.404] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.404] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1912x1080
[    22.405] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.405] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.405] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.405] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.405] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.405] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.405] (II) NVIDIA(0):     Mode is valid.
[    22.405] (II) NVIDIA(0): 
[    22.405] (II) NVIDIA(0):   Validating Mode "680x384":
[    22.405] (II) NVIDIA(0):     680 x 384 @ 60 Hz
[    22.405] (II) NVIDIA(0):     Mode Source: X Server
[    22.405] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    22.405] (II) NVIDIA(0):       HRes, HSyncStart :  680,  704
[    22.405] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
[    22.406] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    22.406] (II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
[    22.406] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.406] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.406] (II) NVIDIA(0):     BestFit Backend for "680x384": 1920x1080
[    22.406] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.407] (II) NVIDIA(GPU-0):     BestFit Centered         680x384
[    22.407] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.407] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.407] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.407] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.407] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.407] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.407] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.407] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.408] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.408] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.408] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.408] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.408] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.408] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1912x1080
[    22.408] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.408] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.408] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.408] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.408] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.408] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.408] (II) NVIDIA(0):     Mode is valid.
[    22.408] (II) NVIDIA(0): 
[    22.409] (II) NVIDIA(0):   Validating Mode "1360x768":
[    22.409] (II) NVIDIA(0):     1360 x 768 @ 60 Hz
[    22.409] (II) NVIDIA(0):     Mode Source: X Server
[    22.409] (II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
[    22.409] (II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
[    22.409] (II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
[    22.409] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.409] (II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
[    22.409] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.409] (II) NVIDIA(0):     BestFit Backend for "1360x768": 1920x1080
[    22.409] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.410] (II) NVIDIA(GPU-0):     BestFit Centered         1360x768
[    22.410] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.410] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.410] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.410] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.411] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.411] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.411] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.411] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.411] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.411] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.411] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.411] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.411] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.411] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1912x1080
[    22.411] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.411] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.411] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.411] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.412] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.412] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.412] (II) NVIDIA(0):     Mode is valid.
[    22.412] (II) NVIDIA(0): 
[    22.412] (II) NVIDIA(0):   Validating Mode "680x384":
[    22.412] (II) NVIDIA(0):     680 x 384 @ 60 Hz
[    22.412] (II) NVIDIA(0):     Mode Source: X Server
[    22.412] (II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
[    22.412] (II) NVIDIA(0):       HRes, HSyncStart :  680,  716
[    22.412] (II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
[    22.412] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    22.412] (II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
[    22.412] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.412] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.413] (II) NVIDIA(0):     BestFit Backend for "680x384": 1920x1080
[    22.413] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.414] (II) NVIDIA(GPU-0):     BestFit Centered         680x384
[    22.414] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.414] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.414] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.414] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.414] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.414] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.414] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.414] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.414] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.414] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.414] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.414] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.414] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.415] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1912x1080
[    22.415] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.415] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.415] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.415] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.415] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.415] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.415] (II) NVIDIA(0):     Mode is valid.
[    22.415] (II) NVIDIA(0): 
[    22.415] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    22.415] (II) NVIDIA(0):     1400 x 1050 @ 60 Hz
[    22.415] (II) NVIDIA(0):     Mode Source: X Server
[    22.415] (II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
[    22.415] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
[    22.416] (II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
[    22.416] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
[    22.416] (II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
[    22.416] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.416] (II) NVIDIA(0):     BestFit Backend for "1400x1050": 1920x1080
[    22.416] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.417] (II) NVIDIA(GPU-0):     BestFit Centered         1400x1050
[    22.417] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.417] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.417] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.417] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.417] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.417] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.417] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.417] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.417] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.418] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.418] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.418] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.418] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.418] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.418] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.418] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.418] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.418] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.418] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.418] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.418] (II) NVIDIA(0):     Mode is valid.
[    22.418] (II) NVIDIA(0): 
[    22.418] (II) NVIDIA(0):   Validating Mode "700x525":
[    22.418] (II) NVIDIA(0):     700 x 525 @ 60 Hz
[    22.419] (II) NVIDIA(0):     Mode Source: X Server
[    22.419] (II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
[    22.419] (II) NVIDIA(0):       HRes, HSyncStart :  700,  744
[    22.419] (II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
[    22.419] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.419] (II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
[    22.419] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.419] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.419] (II) NVIDIA(0):     BestFit Backend for "700x525": 1920x1080
[    22.419] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.420] (II) NVIDIA(GPU-0):     BestFit Centered         700x525
[    22.420] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.420] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.420] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.420] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.421] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.421] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.421] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.421] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.421] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.421] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.421] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.421] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.421] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.421] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.421] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.421] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.421] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.422] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.422] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.422] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.422] (II) NVIDIA(0):     Mode is valid.
[    22.422] (II) NVIDIA(0): 
[    22.422] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    22.422] (II) NVIDIA(0):     1400 x 1050 @ 70 Hz
[    22.422] (II) NVIDIA(0):     Mode Source: X Server
[    22.422] (II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
[    22.422] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
[    22.422] (II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
[    22.422] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
[    22.422] (II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
[    22.422] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.422] (II) NVIDIA(0):     VertRefresh (70.0 Hz) out of range (57.000-63.000 Hz);
[    22.423] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.423] (II) NVIDIA(0):         mode validation
[    22.423] (II) NVIDIA(0):     BestFit Backend for "1400x1050": 1920x1080
[    22.423] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.424] (II) NVIDIA(GPU-0):     BestFit Centered         1400x1050
[    22.424] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.424] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.424] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.424] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.424] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.424] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.424] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.424] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.424] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.424] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.424] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.425] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.425] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.425] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.425] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.425] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.425] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.425] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.425] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.425] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.425] (II) NVIDIA(0):     Mode is valid.
[    22.425] (II) NVIDIA(0): 
[    22.425] (II) NVIDIA(0):   Validating Mode "700x525":
[    22.425] (II) NVIDIA(0):     700 x 525 @ 70 Hz
[    22.425] (II) NVIDIA(0):     Mode Source: X Server
[    22.425] (II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
[    22.426] (II) NVIDIA(0):       HRes, HSyncStart :  700,  748
[    22.426] (II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
[    22.426] (II) NVIDIA(0):       VRes, VSyncStart :  525,  525
[    22.426] (II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
[    22.426] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.426] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.426] (II) NVIDIA(0):     VertRefresh (70.1 Hz) out of range (57.000-63.000 Hz);
[    22.426] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.426] (II) NVIDIA(0):         mode validation
[    22.426] (II) NVIDIA(0):     BestFit Backend for "700x525": 1920x1080
[    22.426] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.427] (II) NVIDIA(GPU-0):     BestFit Centered         700x525
[    22.427] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.427] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.427] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.427] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.427] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.428] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.428] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.428] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.428] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.428] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.428] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.428] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.428] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.428] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.428] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.428] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.428] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.428] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.429] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.429] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.429] (II) NVIDIA(0):     Mode is valid.
[    22.449] (II) NVIDIA(0): 
[    22.449] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    22.449] (II) NVIDIA(0):     1400 x 1050 @ 75 Hz
[    22.449] (II) NVIDIA(0):     Mode Source: X Server
[    22.449] (II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
[    22.449] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
[    22.449] (II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
[    22.449] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
[    22.449] (II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
[    22.449] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.449] (II) NVIDIA(0):     VertRefresh (74.8 Hz) out of range (57.000-63.000 Hz);
[    22.450] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.450] (II) NVIDIA(0):         mode validation
[    22.450] (II) NVIDIA(0):     BestFit Backend for "1400x1050": 1920x1080
[    22.450] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.450] (II) NVIDIA(GPU-0):     BestFit Centered         1400x1050
[    22.450] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.451] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.451] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.451] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.451] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.451] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.451] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.451] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.451] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.451] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.451] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.451] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.451] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.451] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.451] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.451] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.451] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.452] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.452] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.452] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.452] (II) NVIDIA(0):     Mode is valid.
[    22.452] (II) NVIDIA(0): 
[    22.452] (II) NVIDIA(0):   Validating Mode "700x525":
[    22.452] (II) NVIDIA(0):     700 x 525 @ 75 Hz
[    22.452] (II) NVIDIA(0):     Mode Source: X Server
[    22.452] (II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
[    22.452] (II) NVIDIA(0):       HRes, HSyncStart :  700,  732
[    22.452] (II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
[    22.452] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.452] (II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
[    22.452] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.452] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.452] (II) NVIDIA(0):     VertRefresh (74.8 Hz) out of range (57.000-63.000 Hz);
[    22.452] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.452] (II) NVIDIA(0):         mode validation
[    22.452] (II) NVIDIA(0):     BestFit Backend for "700x525": 1920x1080
[    22.453] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.453] (II) NVIDIA(GPU-0):     BestFit Centered         700x525
[    22.453] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.453] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.453] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.453] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.453] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.453] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.454] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.454] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.454] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.454] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.454] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.454] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.454] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.454] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.454] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.454] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.454] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.454] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.454] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.454] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.454] (II) NVIDIA(0):     Mode is valid.
[    22.454] (II) NVIDIA(0): 
[    22.454] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    22.454] (II) NVIDIA(0):     1400 x 1050 @ 85 Hz
[    22.454] (II) NVIDIA(0):     Mode Source: X Server
[    22.454] (II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
[    22.455] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
[    22.455] (II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
[    22.455] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
[    22.455] (II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
[    22.455] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.455] (WW) NVIDIA(0):     Mode is rejected: PixelClock (179.3 MHz) too high for
[    22.455] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.455] (II) NVIDIA(0): 
[    22.455] (II) NVIDIA(0):   Validating Mode "700x525":
[    22.455] (II) NVIDIA(0):     700 x 525 @ 85 Hz
[    22.455] (II) NVIDIA(0):     Mode Source: X Server
[    22.455] (II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
[    22.455] (II) NVIDIA(0):       HRes, HSyncStart :  700,  752
[    22.455] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
[    22.455] (II) NVIDIA(0):       VRes, VSyncStart :  525,  525
[    22.455] (II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
[    22.455] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.455] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.455] (II) NVIDIA(0):     HorizSync (93.8 kHz) out of range (31.000-82.000 kHz);
[    22.456] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.456] (II) NVIDIA(0):         mode validation
[    22.456] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.456] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.456] (II) NVIDIA(0):         mode validation
[    22.456] (II) NVIDIA(0):     BestFit Backend for "700x525": 1920x1080
[    22.456] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.457] (II) NVIDIA(GPU-0):     BestFit Centered         700x525
[    22.457] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.457] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.457] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.457] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.457] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.457] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.457] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.457] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.457] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.457] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.457] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.457] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.457] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.457] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.457] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.457] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.457] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.457] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.457] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.457] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.457] (II) NVIDIA(0):     Mode is valid.
[    22.458] (II) NVIDIA(0): 
[    22.458] (II) NVIDIA(0):   Validating Mode "1440x900":
[    22.458] (II) NVIDIA(0):     1440 x 900 @ 60 Hz
[    22.458] (II) NVIDIA(0):     Mode Source: X Server
[    22.458] (II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
[    22.458] (II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
[    22.458] (II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
[    22.458] (II) NVIDIA(0):       VRes, VSyncStart :  900,  903
[    22.458] (II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
[    22.458] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.458] (II) NVIDIA(0):     BestFit Backend for "1440x900": 1920x1080
[    22.458] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.459] (II) NVIDIA(GPU-0):     BestFit Centered         1440x900
[    22.459] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.459] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.459] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.459] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.459] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.459] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.459] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.459] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.459] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.459] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.459] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.459] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.459] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.459] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.459] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.459] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.460] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.460] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.460] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.460] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.460] (II) NVIDIA(0):     Mode is valid.
[    22.460] (II) NVIDIA(0): 
[    22.460] (II) NVIDIA(0):   Validating Mode "720x450":
[    22.460] (II) NVIDIA(0):     720 x 450 @ 60 Hz
[    22.460] (II) NVIDIA(0):     Mode Source: X Server
[    22.460] (II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
[    22.460] (II) NVIDIA(0):       HRes, HSyncStart :  720,  760
[    22.460] (II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
[    22.460] (II) NVIDIA(0):       VRes, VSyncStart :  450,  451
[    22.460] (II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
[    22.460] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.460] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.460] (II) NVIDIA(0):     BestFit Backend for "720x450": 1920x1080
[    22.460] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.461] (II) NVIDIA(GPU-0):     BestFit Centered         720x450
[    22.461] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.461] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.461] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.461] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.461] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.461] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.461] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.461] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.461] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.461] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.461] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.462] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.462] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.462] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.462] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.462] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.462] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.462] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.462] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.462] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.462] (II) NVIDIA(0):     Mode is valid.
[    22.462] (II) NVIDIA(0): 
[    22.462] (II) NVIDIA(0):   Validating Mode "1600x1024":
[    22.462] (II) NVIDIA(0):     1600 x 1024 @ 60 Hz
[    22.462] (II) NVIDIA(0):     Mode Source: X Server
[    22.462] (II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
[    22.462] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
[    22.462] (II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
[    22.462] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
[    22.462] (II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
[    22.462] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.462] (II) NVIDIA(0):     BestFit Backend for "1600x1024": 1920x1080
[    22.463] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.463] (II) NVIDIA(GPU-0):     BestFit Centered         1600x1024
[    22.463] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.463] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.463] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.463] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.463] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.463] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.463] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.464] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.464] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.464] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.464] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.464] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.464] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.464] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1687x1080
[    22.464] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.464] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.464] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.464] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.464] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.464] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.464] (II) NVIDIA(0):     Mode is valid.
[    22.464] (II) NVIDIA(0): 
[    22.464] (II) NVIDIA(0):   Validating Mode "800x512":
[    22.464] (II) NVIDIA(0):     800 x 512 @ 60 Hz
[    22.464] (II) NVIDIA(0):     Mode Source: X Server
[    22.464] (II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
[    22.465] (II) NVIDIA(0):       HRes, HSyncStart :  800,  800
[    22.465] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
[    22.465] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    22.465] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
[    22.465] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.465] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.465] (II) NVIDIA(0):     BestFit Backend for "800x512": 1920x1080
[    22.465] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.465] (II) NVIDIA(GPU-0):     BestFit Centered         800x512
[    22.466] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.466] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.466] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.466] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.466] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.466] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.466] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.466] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.466] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.466] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.466] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.466] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.466] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.466] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1687x1080
[    22.466] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.466] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.466] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.466] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.466] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.466] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.466] (II) NVIDIA(0):     Mode is valid.
[    22.466] (II) NVIDIA(0): 
[    22.467] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    22.467] (II) NVIDIA(0):     1680 x 1050 @ 60 Hz
[    22.467] (II) NVIDIA(0):     Mode Source: X Server
[    22.467] (II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
[    22.467] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
[    22.467] (II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
[    22.467] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    22.467] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
[    22.467] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.467] (II) NVIDIA(0):     BestFit Backend for "1680x1050": 1920x1080
[    22.467] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.468] (II) NVIDIA(GPU-0):     BestFit Centered         1680x1050
[    22.468] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.468] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.468] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.468] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.468] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.468] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.468] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.468] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.468] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.468] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.468] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.468] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.468] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.468] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.468] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.468] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.469] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.469] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.469] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.469] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.469] (II) NVIDIA(0):     Mode is valid.
[    22.469] (II) NVIDIA(0): 
[    22.469] (II) NVIDIA(0):   Validating Mode "840x525":
[    22.469] (II) NVIDIA(0):     840 x 525 @ 60 Hz
[    22.469] (II) NVIDIA(0):     Mode Source: X Server
[    22.469] (II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
[    22.469] (II) NVIDIA(0):       HRes, HSyncStart :  840,  864
[    22.469] (II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
[    22.469] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.469] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
[    22.469] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.469] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.469] (II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
[    22.469] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.470] (II) NVIDIA(GPU-0):     BestFit Centered         840x525
[    22.470] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.470] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.470] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.470] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.470] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.470] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.470] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.471] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.471] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.471] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.471] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.471] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.471] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.471] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.471] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.471] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.471] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.471] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.471] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.471] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.471] (II) NVIDIA(0):     Mode is valid.
[    22.471] (II) NVIDIA(0): 
[    22.471] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    22.471] (II) NVIDIA(0):     1680 x 1050 @ 60 Hz
[    22.471] (II) NVIDIA(0):     Mode Source: X Server
[    22.471] (II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
[    22.471] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
[    22.471] (II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
[    22.471] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    22.472] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
[    22.472] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.472] (II) NVIDIA(0):     BestFit Backend for "1680x1050": 1920x1080
[    22.472] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.472] (II) NVIDIA(GPU-0):     BestFit Centered         1680x1050
[    22.473] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.473] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.473] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.473] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.473] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.473] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.473] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.473] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.473] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.473] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.473] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.473] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.473] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.473] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.473] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.473] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.473] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.474] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.474] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.474] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.474] (II) NVIDIA(0):     Mode is valid.
[    22.474] (II) NVIDIA(0): 
[    22.474] (II) NVIDIA(0):   Validating Mode "840x525":
[    22.474] (II) NVIDIA(0):     840 x 525 @ 60 Hz
[    22.474] (II) NVIDIA(0):     Mode Source: X Server
[    22.474] (II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
[    22.474] (II) NVIDIA(0):       HRes, HSyncStart :  840,  892
[    22.474] (II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
[    22.474] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.474] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
[    22.474] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.475] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.475] (II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
[    22.475] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.476] (II) NVIDIA(GPU-0):     BestFit Centered         840x525
[    22.476] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.476] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.476] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.476] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.476] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.476] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.476] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.476] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.476] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.476] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.476] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.476] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.476] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.477] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.477] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.477] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.477] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.477] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.477] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.477] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.477] (II) NVIDIA(0):     Mode is valid.
[    22.477] (II) NVIDIA(0): 
[    22.477] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    22.477] (II) NVIDIA(0):     1680 x 1050 @ 70 Hz
[    22.477] (II) NVIDIA(0):     Mode Source: X Server
[    22.477] (II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
[    22.477] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
[    22.478] (II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
[    22.478] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    22.478] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
[    22.478] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.478] (WW) NVIDIA(0):     Mode is rejected: PixelClock (174.0 MHz) too high for
[    22.478] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.478] (II) NVIDIA(0): 
[    22.478] (II) NVIDIA(0):   Validating Mode "840x525":
[    22.478] (II) NVIDIA(0):     840 x 525 @ 70 Hz
[    22.478] (II) NVIDIA(0):     Mode Source: X Server
[    22.478] (II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
[    22.478] (II) NVIDIA(0):       HRes, HSyncStart :  840,  900
[    22.478] (II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
[    22.478] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.478] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
[    22.479] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.479] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.479] (II) NVIDIA(0):     VertRefresh (69.9 Hz) out of range (57.000-63.000 Hz);
[    22.479] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.479] (II) NVIDIA(0):         mode validation
[    22.479] (II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
[    22.479] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.480] (II) NVIDIA(GPU-0):     BestFit Centered         840x525
[    22.481] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.481] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.481] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.481] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.481] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.481] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.482] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.482] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.482] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.482] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.482] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.482] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.482] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.482] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.482] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.482] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.482] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.482] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.482] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.482] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.482] (II) NVIDIA(0):     Mode is valid.
[    22.483] (II) NVIDIA(0): 
[    22.483] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    22.483] (II) NVIDIA(0):     1680 x 1050 @ 75 Hz
[    22.483] (II) NVIDIA(0):     Mode Source: X Server
[    22.483] (II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
[    22.483] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
[    22.483] (II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
[    22.483] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    22.483] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
[    22.483] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.483] (WW) NVIDIA(0):     Mode is rejected: PixelClock (187.0 MHz) too high for
[    22.483] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.483] (II) NVIDIA(0): 
[    22.483] (II) NVIDIA(0):   Validating Mode "840x525":
[    22.484] (II) NVIDIA(0):     840 x 525 @ 75 Hz
[    22.484] (II) NVIDIA(0):     Mode Source: X Server
[    22.484] (II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
[    22.484] (II) NVIDIA(0):       HRes, HSyncStart :  840,  900
[    22.484] (II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
[    22.484] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.484] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
[    22.484] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.484] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.484] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.484] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.484] (II) NVIDIA(0):         mode validation
[    22.484] (II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
[    22.485] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.485] (II) NVIDIA(GPU-0):     BestFit Centered         840x525
[    22.486] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.486] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.486] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.486] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.486] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.486] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.486] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.486] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.486] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.486] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.486] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.486] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.487] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.487] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.487] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.487] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.487] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.487] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.487] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.487] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.487] (II) NVIDIA(0):     Mode is valid.
[    22.487] (II) NVIDIA(0): 
[    22.488] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    22.488] (II) NVIDIA(0):     1680 x 1050 @ 85 Hz
[    22.488] (II) NVIDIA(0):     Mode Source: X Server
[    22.488] (II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
[    22.488] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
[    22.489] (II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
[    22.489] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    22.489] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
[    22.489] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.489] (WW) NVIDIA(0):     Mode is rejected: PixelClock (214.8 MHz) too high for
[    22.489] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.489] (II) NVIDIA(0): 
[    22.489] (II) NVIDIA(0):   Validating Mode "840x525":
[    22.489] (II) NVIDIA(0):     840 x 525 @ 85 Hz
[    22.489] (II) NVIDIA(0):     Mode Source: X Server
[    22.489] (II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
[    22.489] (II) NVIDIA(0):       HRes, HSyncStart :  840,  904
[    22.490] (II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
[    22.490] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    22.490] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
[    22.490] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.490] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.490] (II) NVIDIA(0):     HorizSync (93.9 kHz) out of range (31.000-82.000 kHz);
[    22.490] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.490] (II) NVIDIA(0):         mode validation
[    22.490] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.490] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.490] (II) NVIDIA(0):         mode validation
[    22.490] (II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
[    22.490] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.491] (II) NVIDIA(GPU-0):     BestFit Centered         840x525
[    22.492] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.492] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.492] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.492] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.492] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.492] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.492] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.492] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.492] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.492] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.492] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.492] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.492] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.492] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.493] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.493] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.493] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.493] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.493] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.493] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.493] (II) NVIDIA(0):     Mode is valid.
[    22.493] (II) NVIDIA(0): 
[    22.493] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    22.493] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    22.493] (II) NVIDIA(0):     Mode Source: X Server
[    22.493] (II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
[    22.493] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
[    22.493] (II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
[    22.494] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
[    22.494] (II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
[    22.494] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.494] (II) NVIDIA(0):     BestFit Backend for "1920x1080": 1920x1080
[    22.494] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.494] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.494] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.494] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.494] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.494] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.494] (II) NVIDIA(GPU-0):     Native Centered and Native Scaled are identical;
[    22.494] (II) NVIDIA(GPU-0):         collapsing Native Scaled.
[    22.494] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.495] (II) NVIDIA(GPU-0):     BestFit Centered         1920x1080
[    22.495] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.495] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.495] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.495] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.496] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.496] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.496] (II) NVIDIA(0):     Mode is valid.
[    22.496] (II) NVIDIA(0): 
[    22.496] (II) NVIDIA(0):   Validating Mode "960x540":
[    22.496] (II) NVIDIA(0):     960 x 540 @ 60 Hz
[    22.496] (II) NVIDIA(0):     Mode Source: X Server
[    22.496] (II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
[    22.496] (II) NVIDIA(0):       HRes, HSyncStart :  960,  984
[    22.496] (II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
[    22.496] (II) NVIDIA(0):       VRes, VSyncStart :  540,  541
[    22.496] (II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
[    22.496] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.496] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.496] (II) NVIDIA(0):     BestFit Backend for "960x540": 1920x1080
[    22.497] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.497] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.497] (II) NVIDIA(GPU-0):     Native Scaled and Native AspectScaled are identical;
[    22.497] (II) NVIDIA(GPU-0):         collapsing Native AspectScaled.
[    22.497] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.498] (II) NVIDIA(GPU-0):     BestFit Centered         960x540
[    22.498] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.498] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.498] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.498] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.498] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.498] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.498] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.498] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.498] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.499] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.499] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.499] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.499] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.499] (II) NVIDIA(0):     Mode is valid.
[    22.499] (II) NVIDIA(0): 
[    22.499] (II) NVIDIA(0):   Validating Mode "1920x1200":
[    22.499] (II) NVIDIA(0):     1920 x 1200 @ 60 Hz
[    22.499] (II) NVIDIA(0):     Mode Source: X Server
[    22.499] (II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
[    22.499] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
[    22.499] (II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
[    22.499] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
[    22.499] (II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
[    22.499] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.500] (II) NVIDIA(0):     Mode (1920 x 1200) is too large for DFP Native Resolution
[    22.500] (II) NVIDIA(0):         (Max: 1920 x 1080); mode will not be allowed to scale
[    22.500] (II) NVIDIA(0):         to the DFP's native resolution.
[    22.500] (WW) NVIDIA(0):     Unable to use mode "1920x1200" for LG Electronics LG TV
[    22.500] (WW) NVIDIA(0):         (DFP-0); cannot compute backend DFP timings (mode is
[    22.500] (WW) NVIDIA(0):         larger than native backend 1920 x 1080).
[    22.500] (WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
[    22.500] (WW) NVIDIA(0):     timings.
[    22.500] (II) NVIDIA(0): 
[    22.501] (II) NVIDIA(0):   Validating Mode "960x600":
[    22.501] (II) NVIDIA(0):     960 x 600 @ 60 Hz
[    22.501] (II) NVIDIA(0):     Mode Source: X Server
[    22.501] (II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
[    22.501] (II) NVIDIA(0):       HRes, HSyncStart :  960,  984
[    22.501] (II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
[    22.501] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.501] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
[    22.501] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.501] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.501] (II) NVIDIA(0):     BestFit Backend for "960x600": 1920x1080
[    22.501] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.502] (II) NVIDIA(GPU-0):     BestFit Centered         960x600
[    22.502] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.502] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.503] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.503] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.503] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.503] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.503] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.503] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.503] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.503] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.503] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.503] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.503] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.503] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.503] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.503] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.503] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.504] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.504] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.504] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.504] (II) NVIDIA(0):     Mode is valid.
[    22.504] (II) NVIDIA(0): 
[    22.504] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    22.504] (II) NVIDIA(0):     1920 x 1440 @ 85 Hz
[    22.504] (II) NVIDIA(0):     Mode Source: X Server
[    22.504] (II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
[    22.504] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
[    22.504] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
[    22.504] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    22.504] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
[    22.504] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.505] (WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for
[    22.505] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.505] (II) NVIDIA(0): 
[    22.505] (II) NVIDIA(0):   Validating Mode "960x720":
[    22.505] (II) NVIDIA(0):     960 x 720 @ 85 Hz
[    22.505] (II) NVIDIA(0):     Mode Source: X Server
[    22.505] (II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
[    22.505] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
[    22.505] (II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
[    22.505] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[    22.505] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
[    22.505] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.505] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.505] (WW) NVIDIA(0):     Mode is rejected: PixelClock (170.7 MHz) too high for
[    22.506] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.506] (II) NVIDIA(0): 
[    22.506] (II) NVIDIA(0):   Validating Mode "2048x1536":
[    22.506] (II) NVIDIA(0):     2048 x 1536 @ 60 Hz
[    22.506] (II) NVIDIA(0):     Mode Source: X Server
[    22.506] (II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
[    22.506] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
[    22.506] (II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
[    22.506] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[    22.506] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
[    22.506] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.506] (WW) NVIDIA(0):     Mode is rejected: PixelClock (266.9 MHz) too high for
[    22.506] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.506] (II) NVIDIA(0): 
[    22.506] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.507] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    22.507] (II) NVIDIA(0):     Mode Source: X Server
[    22.507] (II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
[    22.507] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
[    22.507] (II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
[    22.507] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    22.507] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
[    22.507] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.507] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.507] (II) NVIDIA(0):     HorizSync (95.3 kHz) out of range (31.000-82.000 kHz);
[    22.507] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.507] (II) NVIDIA(0):         mode validation
[    22.507] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.507] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.509] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.509] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.509] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.509] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.509] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.509] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.509] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.509] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.509] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.509] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.509] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.509] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.510] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.510] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.510] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.510] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.510] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.510] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.510] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.510] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.510] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.510] (II) NVIDIA(0):     Mode is valid.
[    22.510] (II) NVIDIA(0): 
[    22.510] (II) NVIDIA(0):   Validating Mode "2048x1536":
[    22.510] (II) NVIDIA(0):     2048 x 1536 @ 75 Hz
[    22.510] (II) NVIDIA(0):     Mode Source: X Server
[    22.511] (II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
[    22.511] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
[    22.511] (II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
[    22.511] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[    22.511] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
[    22.511] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.511] (WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for
[    22.511] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.511] (II) NVIDIA(0): 
[    22.511] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.511] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[    22.512] (II) NVIDIA(0):     Mode Source: X Server
[    22.512] (II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
[    22.512] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
[    22.512] (II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
[    22.512] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    22.512] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
[    22.512] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.512] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.512] (WW) NVIDIA(0):     Mode is rejected: PixelClock (170.2 MHz) too high for
[    22.512] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.512] (II) NVIDIA(0): 
[    22.512] (II) NVIDIA(0):   Validating Mode "2048x1536":
[    22.512] (II) NVIDIA(0):     2048 x 1536 @ 85 Hz
[    22.512] (II) NVIDIA(0):     Mode Source: X Server
[    22.513] (II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
[    22.513] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
[    22.513] (II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
[    22.513] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[    22.513] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
[    22.513] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.513] (WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
[    22.513] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.513] (II) NVIDIA(0): 
[    22.513] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.513] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[    22.513] (II) NVIDIA(0):     Mode Source: X Server
[    22.513] (II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
[    22.513] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
[    22.513] (II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
[    22.514] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    22.514] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
[    22.514] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.514] (II) NVIDIA(0):       Extra            : DoubleScan
[    22.514] (WW) NVIDIA(0):     Mode is rejected: PixelClock (194.0 MHz) too high for
[    22.514] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.514] (II) NVIDIA(0): 
[    22.514] (II) NVIDIA(0):   Validating Mode "640x350":
[    22.514] (II) NVIDIA(0):     640 x 350 @ 85 Hz
[    22.514] (II) NVIDIA(0):     Mode Source: VESA
[    22.514] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.514] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    22.514] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    22.514] (II) NVIDIA(0):       VRes, VSyncStart :  350,  382
[    22.515] (II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
[    22.515] (II) NVIDIA(0):       H/V Polarity     : +/-
[    22.515] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.515] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.515] (II) NVIDIA(0):         mode validation
[    22.515] (II) NVIDIA(0):     BestFit Backend for "640x350": 1920x1080
[    22.515] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.516] (II) NVIDIA(GPU-0):     BestFit Centered         640x350
[    22.516] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.516] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.516] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.516] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.516] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.517] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.517] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.517] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.517] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.517] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.517] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.517] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.517] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.517] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1920x1050
[    22.517] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.517] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.517] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.517] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.517] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.517] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.517] (II) NVIDIA(0):     Mode is valid.
[    22.518] (II) NVIDIA(0): 
[    22.518] (II) NVIDIA(0):   Validating Mode "640x400":
[    22.518] (II) NVIDIA(0):     640 x 400 @ 85 Hz
[    22.518] (II) NVIDIA(0):     Mode Source: VESA
[    22.518] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.518] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    22.518] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    22.518] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    22.518] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
[    22.518] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.518] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.518] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.518] (II) NVIDIA(0):         mode validation
[    22.518] (II) NVIDIA(0):     BestFit Backend for "640x400": 1920x1080
[    22.519] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.520] (II) NVIDIA(GPU-0):     BestFit Centered         640x400
[    22.520] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.520] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.520] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.520] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.520] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.520] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.520] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.520] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.520] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.521] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.521] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.521] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.521] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.521] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1728x1080
[    22.521] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.521] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.521] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.521] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.521] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.521] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.521] (II) NVIDIA(0):     Mode is valid.
[    22.521] (II) NVIDIA(0): 
[    22.521] (II) NVIDIA(0):   Validating Mode "720x400":
[    22.522] (II) NVIDIA(0):     720 x 400 @ 85 Hz
[    22.522] (II) NVIDIA(0):     Mode Source: VESA
[    22.522] (II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
[    22.522] (II) NVIDIA(0):       HRes, HSyncStart :  720,  756
[    22.522] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
[    22.522] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    22.522] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
[    22.522] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.522] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.522] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.522] (II) NVIDIA(0):         mode validation
[    22.522] (II) NVIDIA(0):     BestFit Backend for "720x400": 1920x1080
[    22.522] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.523] (II) NVIDIA(GPU-0):     BestFit Centered         720x400
[    22.523] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.524] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.524] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.524] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.524] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.524] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.524] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.524] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.524] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.524] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.524] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.524] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.524] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.525] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1920x1066
[    22.525] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.525] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.525] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.525] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.525] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.525] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.525] (II) NVIDIA(0):     Mode is valid.
[    22.525] (II) NVIDIA(0): 
[    22.525] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.525] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    22.525] (II) NVIDIA(0):     Mode Source: VESA
[    22.526] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[    22.526] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    22.526] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
[    22.526] (II) NVIDIA(0):       VRes, VSyncStart :  480,  490
[    22.526] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
[    22.526] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.526] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.526] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.527] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.527] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.527] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.527] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.527] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.527] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.527] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.527] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.527] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.527] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.528] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.528] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.528] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.528] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.529] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.529] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.529] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.529] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.529] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.529] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.529] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.529] (II) NVIDIA(0):     Mode is valid.
[    22.529] (II) NVIDIA(0): 
[    22.529] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.529] (II) NVIDIA(0):     640 x 480 @ 73 Hz
[    22.529] (II) NVIDIA(0):     Mode Source: VESA
[    22.529] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.529] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[    22.529] (II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
[    22.530] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    22.530] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
[    22.530] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.530] (II) NVIDIA(0):     VertRefresh (72.8 Hz) out of range (57.000-63.000 Hz);
[    22.530] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.530] (II) NVIDIA(0):         mode validation
[    22.530] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.530] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.531] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.531] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.531] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.533] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.533] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.533] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.533] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.534] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.534] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.534] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.534] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.534] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.534] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.534] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.534] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.534] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.534] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.534] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.534] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.534] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.534] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.534] (II) NVIDIA(0):     Mode is valid.
[    22.535] (II) NVIDIA(0): 
[    22.535] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.535] (II) NVIDIA(0):     640 x 480 @ 75 Hz
[    22.535] (II) NVIDIA(0):     Mode Source: VESA
[    22.535] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    22.535] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    22.535] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
[    22.535] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    22.535] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
[    22.535] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.535] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.535] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.535] (II) NVIDIA(0):         mode validation
[    22.535] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.536] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.537] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.537] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.537] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.537] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.537] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.537] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.537] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.537] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.537] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.537] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.538] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.538] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.538] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.538] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.538] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.538] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.538] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.538] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.538] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.538] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.538] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.538] (II) NVIDIA(0):     Mode is valid.
[    22.538] (II) NVIDIA(0): 
[    22.538] (II) NVIDIA(0):   Validating Mode "640x480":
[    22.538] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[    22.539] (II) NVIDIA(0):     Mode Source: VESA
[    22.539] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    22.539] (II) NVIDIA(0):       HRes, HSyncStart :  640,  696
[    22.539] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
[    22.539] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    22.539] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
[    22.539] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.539] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.539] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.539] (II) NVIDIA(0):         mode validation
[    22.539] (II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
[    22.539] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.541] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[    22.541] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.541] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.541] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.541] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.541] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.541] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.541] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.541] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.541] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.542] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.542] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.542] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.542] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.542] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.542] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.542] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.542] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.542] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.542] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.542] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.543] (II) NVIDIA(0):     Mode is valid.
[    22.543] (II) NVIDIA(0): 
[    22.543] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.543] (II) NVIDIA(0):     800 x 600 @ 56 Hz
[    22.543] (II) NVIDIA(0):     Mode Source: VESA
[    22.543] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    22.543] (II) NVIDIA(0):       HRes, HSyncStart :  800,  824
[    22.543] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
[    22.543] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.543] (II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
[    22.543] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.543] (II) NVIDIA(0):     VertRefresh (56.2 Hz) out of range (57.000-63.000 Hz);
[    22.543] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.543] (II) NVIDIA(0):         mode validation
[    22.544] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.544] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.545] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.545] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.545] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.545] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.545] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.545] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.545] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.545] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.545] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.545] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.545] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.545] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.545] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.546] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.546] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.546] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.546] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.546] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.546] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.546] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.546] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.546] (II) NVIDIA(0):     Mode is valid.
[    22.546] (II) NVIDIA(0): 
[    22.547] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.547] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    22.547] (II) NVIDIA(0):     Mode Source: VESA
[    22.547] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[    22.547] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[    22.547] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[    22.547] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.547] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[    22.547] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.547] (II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
[    22.547] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.547] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.547] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.547] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.549] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.549] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.549] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.549] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.549] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.549] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.549] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.549] (II) NVIDIA(GPU-0):     Native Centered          800x600
[    22.549] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.549] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.549] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.549] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.550] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.550] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.550] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.550] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.550] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.550] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.550] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.550] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.550] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.550] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.550] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.550] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.550] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.551] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.551] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.551] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.551] (II) NVIDIA(0):     Mode is valid.
[    22.551] (II) NVIDIA(0): 
[    22.551] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.551] (II) NVIDIA(0):     800 x 600 @ 72 Hz
[    22.551] (II) NVIDIA(0):     Mode Source: VESA
[    22.551] (II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
[    22.551] (II) NVIDIA(0):       HRes, HSyncStart :  800,  856
[    22.552] (II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
[    22.552] (II) NVIDIA(0):       VRes, VSyncStart :  600,  637
[    22.552] (II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
[    22.552] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.552] (II) NVIDIA(0):     VertRefresh (72.2 Hz) out of range (57.000-63.000 Hz);
[    22.552] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.552] (II) NVIDIA(0):         mode validation
[    22.552] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.552] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.553] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.553] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.553] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.553] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.553] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.554] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.554] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.554] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.554] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.554] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.554] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.554] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.554] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.554] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.554] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.554] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.554] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.554] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.554] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.554] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.555] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.555] (II) NVIDIA(0):     Mode is valid.
[    22.555] (II) NVIDIA(0): 
[    22.555] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.555] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[    22.555] (II) NVIDIA(0):     Mode Source: VESA
[    22.555] (II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
[    22.555] (II) NVIDIA(0):       HRes, HSyncStart :  800,  816
[    22.555] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
[    22.555] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.555] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
[    22.555] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.555] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.555] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.556] (II) NVIDIA(0):         mode validation
[    22.556] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.556] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.557] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.557] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.557] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.557] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.557] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.557] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.557] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.558] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.558] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.558] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.558] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.558] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.558] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.558] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.558] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.558] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.558] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.558] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.558] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.558] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.558] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.558] (II) NVIDIA(0):     Mode is valid.
[    22.559] (II) NVIDIA(0): 
[    22.559] (II) NVIDIA(0):   Validating Mode "800x600":
[    22.559] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[    22.559] (II) NVIDIA(0):     Mode Source: VESA
[    22.559] (II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
[    22.559] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    22.559] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
[    22.559] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    22.559] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
[    22.559] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.559] (II) NVIDIA(0):     VertRefresh (85.1 Hz) out of range (57.000-63.000 Hz);
[    22.559] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.559] (II) NVIDIA(0):         mode validation
[    22.559] (II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
[    22.560] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.561] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[    22.561] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.561] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.561] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.561] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.561] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.561] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.562] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.562] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.562] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.562] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.562] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.562] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.562] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.563] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.563] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.563] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.563] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.563] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.563] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.563] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.563] (II) NVIDIA(0):     Mode is valid.
[    22.563] (II) NVIDIA(0): 
[    22.563] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.563] (II) NVIDIA(0):     1024 x 768 @ 87 Hz
[    22.564] (II) NVIDIA(0):     Mode Source: VESA
[    22.564] (II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
[    22.564] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
[    22.564] (II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
[    22.564] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    22.564] (II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
[    22.564] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.564] (II) NVIDIA(0):       Extra            : Interlace
[    22.564] (II) NVIDIA(0):     VertRefresh (87.0 Hz) out of range (57.000-63.000 Hz);
[    22.564] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.564] (II) NVIDIA(0):         mode validation
[    22.564] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.564] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.565] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.565] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.565] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.565] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.565] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.565] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.566] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.566] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.566] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.566] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.566] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.566] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.566] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.566] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.566] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.566] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.566] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.566] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.566] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.566] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.567] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.567] (II) NVIDIA(0):     Mode is valid.
[    22.567] (II) NVIDIA(0): 
[    22.567] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.567] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    22.567] (II) NVIDIA(0):     Mode Source: VESA
[    22.567] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[    22.567] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    22.567] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[    22.567] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.567] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    22.567] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.567] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
[    22.567] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.567] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.567] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.567] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.570] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.570] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.571] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.571] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.571] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.571] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.571] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.571] (II) NVIDIA(GPU-0):     Native Centered          1024x768
[    22.571] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.571] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.571] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.571] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.571] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.571] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.571] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.571] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.571] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.574] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.574] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.574] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.574] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.574] (II) NVIDIA(GPU-0):     Native AspectScaled      1440x1080
[    22.575] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.575] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.575] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.575] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.575] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.575] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.575] (II) NVIDIA(0):     Mode is valid.
[    22.575] (II) NVIDIA(0): 
[    22.575] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.575] (II) NVIDIA(0):     1024 x 768 @ 70 Hz
[    22.575] (II) NVIDIA(0):     Mode Source: VESA
[    22.575] (II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
[    22.575] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    22.575] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
[    22.575] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    22.576] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    22.576] (II) NVIDIA(0):       H/V Polarity     : -/-
[    22.576] (II) NVIDIA(0):     VertRefresh (70.1 Hz) out of range (57.000-63.000 Hz);
[    22.576] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.576] (II) NVIDIA(0):         mode validation
[    22.576] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.576] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.577] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.577] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.577] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.577] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.578] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.578] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.578] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.578] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.578] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.578] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.578] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.578] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.578] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.579] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.579] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.579] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.579] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.579] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.579] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.579] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.579] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.579] (II) NVIDIA(0):     Mode is valid.
[    22.579] (II) NVIDIA(0): 
[    22.579] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.579] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[    22.579] (II) NVIDIA(0):     Mode Source: VESA
[    22.579] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[    22.579] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
[    22.580] (II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
[    22.580] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    22.580] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
[    22.580] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.580] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.580] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.580] (II) NVIDIA(0):         mode validation
[    22.580] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.580] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.582] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.582] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.582] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.582] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.582] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.582] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.582] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.582] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.582] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.582] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.582] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.582] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.582] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.583] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.583] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.583] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.583] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.583] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.583] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.583] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.583] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.583] (II) NVIDIA(0):     Mode is valid.
[    22.583] (II) NVIDIA(0): 
[    22.583] (II) NVIDIA(0):   Validating Mode "1024x768":
[    22.585] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[    22.585] (II) NVIDIA(0):     Mode Source: VESA
[    22.585] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[    22.585] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
[    22.585] (II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
[    22.585] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    22.585] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
[    22.585] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.586] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.586] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.586] (II) NVIDIA(0):         mode validation
[    22.586] (II) NVIDIA(0):     BestFit Backend for "1024x768": 1920x1080
[    22.586] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.587] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[    22.587] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.587] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.587] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.587] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.587] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.587] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.587] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.588] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.588] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.588] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.588] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.588] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.588] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.588] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.588] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.588] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.588] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.588] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.588] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.588] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.588] (II) NVIDIA(0):     Mode is valid.
[    22.589] (II) NVIDIA(0): 
[    22.589] (II) NVIDIA(0):   Validating Mode "1152x864":
[    22.589] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[    22.589] (II) NVIDIA(0):     Mode Source: VESA
[    22.589] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.589] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    22.589] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
[    22.589] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    22.589] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[    22.589] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.589] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.589] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.589] (II) NVIDIA(0):         mode validation
[    22.590] (II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
[    22.590] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.590] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[    22.591] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.591] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.591] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.591] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.591] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.591] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.591] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.591] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.591] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.591] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.591] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.591] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.591] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.591] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.592] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.592] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.592] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.592] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.592] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.592] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.592] (II) NVIDIA(0):     Mode is valid.
[    22.592] (II) NVIDIA(0): 
[    22.592] (II) NVIDIA(0):   Validating Mode "1280x960":
[    22.592] (II) NVIDIA(0):     1280 x 960 @ 60 Hz
[    22.592] (II) NVIDIA(0):     Mode Source: VESA
[    22.592] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.592] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
[    22.593] (II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
[    22.593] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    22.593] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
[    22.593] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.593] (II) NVIDIA(0):     BestFit Backend for "1280x960": 1920x1080
[    22.593] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.594] (II) NVIDIA(GPU-0):     BestFit Centered         1280x960
[    22.594] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.595] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.595] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.595] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.595] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.595] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.595] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.595] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.595] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.595] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.595] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.595] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.595] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.595] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.595] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.595] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.596] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.596] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.596] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.596] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.596] (II) NVIDIA(0):     Mode is valid.
[    22.596] (II) NVIDIA(0): 
[    22.596] (II) NVIDIA(0):   Validating Mode "1280x960":
[    22.596] (II) NVIDIA(0):     1280 x 960 @ 85 Hz
[    22.596] (II) NVIDIA(0):     Mode Source: VESA
[    22.596] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    22.596] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    22.596] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    22.596] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    22.597] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
[    22.597] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.597] (II) NVIDIA(0):     HorizSync (85.9 kHz) out of range (31.000-82.000 kHz);
[    22.597] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.597] (II) NVIDIA(0):         mode validation
[    22.597] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.597] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.597] (II) NVIDIA(0):         mode validation
[    22.597] (II) NVIDIA(0):     BestFit Backend for "1280x960": 1920x1080
[    22.597] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.598] (II) NVIDIA(GPU-0):     BestFit Centered         1280x960
[    22.598] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.598] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.598] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.598] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.598] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.599] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.599] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.599] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.599] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.599] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.599] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.599] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.599] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.599] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1440x1080
[    22.599] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.599] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.599] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.599] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.599] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.599] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.600] (II) NVIDIA(0):     Mode is valid.
[    22.600] (II) NVIDIA(0): 
[    22.600] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.600] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[    22.600] (II) NVIDIA(0):     Mode Source: VESA
[    22.600] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    22.600] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[    22.600] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    22.600] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.600] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    22.600] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.600] (II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
[    22.600] (II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
[    22.601] (II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
[    22.601] (II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
[    22.601] (II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
[    22.602] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.602] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.602] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.602] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.602] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.602] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.602] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.602] (II) NVIDIA(GPU-0):     Native Centered          1280x1024
[    22.602] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.603] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.603] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.603] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.603] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.603] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.603] (II) NVIDIA(GPU-0):     Native Scaled            1920x1080
[    22.603] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.603] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.603] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.603] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.603] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.603] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.604] (II) NVIDIA(GPU-0):     Native AspectScaled      1350x1080
[    22.604] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.604] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.604] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.604] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.604] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.604] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.604] (II) NVIDIA(0):     Mode is valid.
[    22.604] (II) NVIDIA(0): 
[    22.605] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.605] (II) NVIDIA(0):     1280 x 1024 @ 75 Hz
[    22.605] (II) NVIDIA(0):     Mode Source: VESA
[    22.605] (II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
[    22.605] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
[    22.605] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    22.605] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.605] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    22.605] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.605] (II) NVIDIA(0):     VertRefresh (75.0 Hz) out of range (57.000-63.000 Hz);
[    22.605] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.605] (II) NVIDIA(0):         mode validation
[    22.605] (II) NVIDIA(0):     BestFit Backend for "1280x1024": 1920x1080
[    22.605] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.606] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.606] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.606] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.606] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.606] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.606] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.606] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.606] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.606] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.606] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.606] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.606] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.606] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.606] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.607] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.607] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.607] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.607] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.607] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.607] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.607] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.607] (II) NVIDIA(0):     Mode is valid.
[    22.607] (II) NVIDIA(0): 
[    22.607] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    22.607] (II) NVIDIA(0):     1280 x 1024 @ 85 Hz
[    22.607] (II) NVIDIA(0):     Mode Source: VESA
[    22.607] (II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
[    22.607] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    22.607] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    22.607] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    22.607] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
[    22.607] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.607] (II) NVIDIA(0):     HorizSync (91.1 kHz) out of range (31.000-82.000 kHz);
[    22.607] (II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
[    22.607] (II) NVIDIA(0):         mode validation
[    22.608] (II) NVIDIA(0):     VertRefresh (85.0 Hz) out of range (57.000-63.000 Hz);
[    22.608] (II) NVIDIA(0):         however, ignoring VertRefresh check for DFP frontend
[    22.608] (II) NVIDIA(0):         mode validation
[    22.608] (II) NVIDIA(0):     BestFit Backend for "1280x1024": 1920x1080
[    22.608] (II) NVIDIA(GPU-0):     BestFit and Native are identical; collapsing Native.
[    22.608] (II) NVIDIA(GPU-0):     BestFit Centered         1280x1024
[    22.609] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[    22.609] (II) NVIDIA(GPU-0):       Vertical Taps          0
[    22.609] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.609] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.609] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.609] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.609] (II) NVIDIA(GPU-0):     BestFit Scaled           1920x1080
[    22.609] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.609] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.609] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.609] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.609] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.609] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.609] (II) NVIDIA(GPU-0):     BestFit AspectScaled     1350x1080
[    22.609] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[    22.609] (II) NVIDIA(GPU-0):       Vertical Taps          1
[    22.609] (II) NVIDIA(GPU-0):       Base SuperSample       x1
[    22.609] (II) NVIDIA(GPU-0):       Base Depth             32
[    22.609] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[    22.609] (II) NVIDIA(GPU-0):       Overlay Depth          32
[    22.609] (II) NVIDIA(0):     Mode is valid.
[    22.610] (II) NVIDIA(0): 
[    22.610] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.610] (II) NVIDIA(0):     1600 x 1200 @ 60 Hz
[    22.610] (II) NVIDIA(0):     Mode Source: VESA
[    22.610] (II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
[    22.610] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.610] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.610] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.610] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.610] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.610] (WW) NVIDIA(0):     Mode is rejected: PixelClock (162.0 MHz) too high for EDID
[    22.610] (WW) NVIDIA(0):     (EDID Max: 160.0 MHz).
[    22.610] (II) NVIDIA(0): 
[    22.610] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.610] (II) NVIDIA(0):     1600 x 1200 @ 65 Hz
[    22.610] (II) NVIDIA(0):     Mode Source: VESA
[    22.610] (II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
[    22.610] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.610] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.610] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.610] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.611] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.611] (WW) NVIDIA(0):     Mode is rejected: PixelClock (175.5 MHz) too high for
[    22.611] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.611] (II) NVIDIA(0): 
[    22.611] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.611] (II) NVIDIA(0):     1600 x 1200 @ 70 Hz
[    22.611] (II) NVIDIA(0):     Mode Source: VESA
[    22.611] (II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
[    22.611] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.611] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.611] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.611] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.611] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.611] (WW) NVIDIA(0):     Mode is rejected: PixelClock (189.0 MHz) too high for
[    22.611] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.611] (II) NVIDIA(0): 
[    22.611] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.611] (II) NVIDIA(0):     1600 x 1200 @ 75 Hz
[    22.611] (II) NVIDIA(0):     Mode Source: VESA
[    22.611] (II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
[    22.611] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.611] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.612] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.612] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.612] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.612] (WW) NVIDIA(0):     Mode is rejected: PixelClock (202.5 MHz) too high for
[    22.612] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.612] (II) NVIDIA(0): 
[    22.612] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    22.612] (II) NVIDIA(0):     1600 x 1200 @ 85 Hz
[    22.612] (II) NVIDIA(0):     Mode Source: VESA
[    22.612] (II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
[    22.612] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    22.612] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    22.612] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    22.612] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    22.613] (II) NVIDIA(0):       H/V Polarity     : +/+
[    22.613] (WW) NVIDIA(0):     Mode is rejected: PixelClock (229.5 MHz) too high for
[    22.613] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.613] (II) NVIDIA(0): 
[    22.613] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    22.613] (II) NVIDIA(0):     1792 x 1344 @ 60 Hz
[    22.613] (II) NVIDIA(0):     Mode Source: VESA
[    22.613] (II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
[    22.613] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
[    22.613] (II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
[    22.613] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    22.614] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
[    22.614] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.614] (WW) NVIDIA(0):     Mode is rejected: PixelClock (204.8 MHz) too high for
[    22.614] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.614] (II) NVIDIA(0): 
[    22.614] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    22.614] (II) NVIDIA(0):     1792 x 1344 @ 75 Hz
[    22.614] (II) NVIDIA(0):     Mode Source: VESA
[    22.614] (II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
[    22.614] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
[    22.614] (II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
[    22.614] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    22.614] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
[    22.614] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.615] (WW) NVIDIA(0):     Mode is rejected: PixelClock (261.0 MHz) too high for
[    22.615] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.615] (II) NVIDIA(0): 
[    22.615] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    22.615] (II) NVIDIA(0):     1856 x 1392 @ 60 Hz
[    22.615] (II) NVIDIA(0):     Mode Source: VESA
[    22.615] (II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
[    22.615] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
[    22.615] (II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
[    22.615] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    22.615] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
[    22.615] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.615] (WW) NVIDIA(0):     Mode is rejected: PixelClock (218.3 MHz) too high for
[    22.615] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.615] (II) NVIDIA(0): 
[    22.616] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    22.616] (II) NVIDIA(0):     1856 x 1392 @ 75 Hz
[    22.616] (II) NVIDIA(0):     Mode Source: VESA
[    22.616] (II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
[    22.616] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
[    22.616] (II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
[    22.616] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    22.616] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
[    22.616] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.616] (WW) NVIDIA(0):     Mode is rejected: PixelClock (288.0 MHz) too high for
[    22.616] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.616] (II) NVIDIA(0): 
[    22.616] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    22.617] (II) NVIDIA(0):     1920 x 1440 @ 60 Hz
[    22.617] (II) NVIDIA(0):     Mode Source: VESA
[    22.617] (II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
[    22.617] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
[    22.617] (II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
[    22.617] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    22.617] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    22.617] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.617] (WW) NVIDIA(0):     Mode is rejected: PixelClock (234.0 MHz) too high for
[    22.617] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.617] (II) NVIDIA(0): 
[    22.617] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    22.617] (II) NVIDIA(0):     1920 x 1440 @ 75 Hz
[    22.617] (II) NVIDIA(0):     Mode Source: VESA
[    22.617] (II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
[    22.617] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
[    22.617] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
[    22.617] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    22.617] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    22.617] (II) NVIDIA(0):       H/V Polarity     : -/+
[    22.617] (WW) NVIDIA(0):     Mode is rejected: PixelClock (297.0 MHz) too high for
[    22.617] (WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
[    22.618] (II) NVIDIA(0): 
[    22.619] (II) NVIDIA(0): --- Done building ModePool for LG Electronics LG TV (DFP-0)
[    22.620] (II) NVIDIA(0):     ---
[    22.620] (II) NVIDIA(0): 
[    22.620] (II) NVIDIA(0): 
[    22.620] (II) NVIDIA(0): --- Modes in ModePool for LG Electronics LG TV (DFP-0) ---
[    22.620] (II) NVIDIA(0): "nvidia-auto-select" : 1920 x 1080 @  60.0 Hz  (from: EDID)
[    22.620] (II) NVIDIA(0): "1920x1080"          : 1920 x 1080 @  60.0 Hz  (from: EDID)
[    22.620] (II) NVIDIA(0): "1920x1080_60"       : 1920 x 1080 @  60.0 Hz  (from: EDID)
[    22.620] (II) NVIDIA(0): "1920x1080_60_0"     : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 16) (from: EDID)
[    22.620] (II) NVIDIA(0): "1920x1080_60_1"     : 1920 x 1080 @  59.9 Hz  (from: X Server)
[    22.620] (II) NVIDIA(0): "1920x1080_30"       : 1920 x 1080 @ 29.97/30 Hz (CEA-861B Format 34) (from: EDID)
[    22.620] (II) NVIDIA(0): "1920x1080_24"       : 1920 x 1080 @ 23.97/24 Hz (CEA-861B Format 32) (from: EDID)
[    22.620] (II) NVIDIA(0): "1920x1080_60i"      : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 5) (from: EDID)
[    22.620] (II) NVIDIA(0): "1680x1050"          : 1680 x 1050 @  60.0 Hz  (from: X Server)
[    22.620] (II) NVIDIA(0): "1680x1050_60"       : 1680 x 1050 @  60.0 Hz  (from: X Server)
[    22.620] (II) NVIDIA(0): "1680x1050_60_0"     : 1680 x 1050 @  59.9 Hz  (from: X Server)
[    22.620] (II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.2 Hz  (from: X Server)
[    22.620] (II) NVIDIA(0): "1600x1024_60"       : 1600 x 1024 @  60.2 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1440x900"           : 1440 x  900 @  59.9 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  59.9 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  74.8 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1400x1050_75"       : 1400 x 1050 @  74.8 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1400x1050_70"       : 1400 x 1050 @  70.0 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1400x1050_60"       : 1400 x 1050 @  60.0 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)
[    22.621] (II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  85.0 Hz  (from: X Server, VESA)
[    22.621] (II) NVIDIA(0): "1280x1024_85"       : 1280 x 1024 @  85.0 Hz  (from: X Server, VESA)
[    22.621] (II) NVIDIA(0): "1280x1024_75"       : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA)
[    22.621] (II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
[    22.621] (II) NVIDIA(0): "1280x960"           : 1280 x  960 @  85.0 Hz  (from: X Server, VESA)
[    22.621] (II) NVIDIA(0): "1280x960_85"        : 1280 x  960 @  85.0 Hz  (from: X Server, VESA)
[    22.621] (II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
[    22.621] (II) NVIDIA(0): "1280x720"           : 1280 x  720 @  60.0 Hz  (from: EDID)
[    22.621] (II) NVIDIA(0): "1280x720_60"        : 1280 x  720 @  60.0 Hz  (from: EDID)
[    22.622] (II) NVIDIA(0): "1280x720_60_0"      : 1280 x  720 @ 59.94/60 Hz (CEA-861B Format 4) (from: EDID)
[    22.622] (II) NVIDIA(0): "1152x864"           : 1152 x  864 @ 100.0 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1152x864_100"       : 1152 x  864 @ 100.0 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1152x864_85"        : 1152 x  864 @  85.1 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1152x864_85_0"      : 1152 x  864 @  85.0 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1152x864_75"        : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
[    22.622] (II) NVIDIA(0): "1152x864_75_0"      : 1152 x  864 @  75.0 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1152x864_70"        : 1152 x  864 @  70.0 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1152x864_60"        : 1152 x  864 @  60.0 Hz  (from: X Server)
[    22.622] (II) NVIDIA(0): "1024x768"           : 1024 x  768 @  85.0 Hz  (from: X Server, VESA)
[    22.622] (II) NVIDIA(0): "1024x768i"          : 1024 x  768 @  87.0 Hz Interlace  (from: X Server)
[    22.622] (II) NVIDIA(0): "1024x768_85"        : 1024 x  768 @  85.0 Hz  (from: X Server, VESA)
[    22.622] (II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    22.622] (II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
[    22.622] (II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
[    22.622] (II) NVIDIA(0): "1024x768d60"        : 1024 x  768 @  60.0 Hz DoubleScan  (from: X Server)
[    22.622] (II) NVIDIA(0): "1024x768_87i"       : 1024 x  768 @  87.0 Hz Interlace  (from: VESA)
[    22.623] (II) NVIDIA(0): "1024x768_87i_0"     : 1024 x  768 @  87.0 Hz Interlace  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x720"            :  960 x  720 @  75.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x720d75"         :  960 x  720 @  75.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x720d60"         :  960 x  720 @  60.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x600d60"         :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x540"            :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "960x540d60"         :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "928x696"            :  928 x  696 @  75.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "928x696d75"         :  928 x  696 @  75.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "928x696d60"         :  928 x  696 @  60.1 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "896x672"            :  896 x  672 @  75.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "896x672d75"         :  896 x  672 @  75.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "896x672d60"         :  896 x  672 @  60.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "840x525"            :  840 x  525 @  85.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "840x525d85"         :  840 x  525 @  85.0 Hz DoubleScan  (from: X Server)
[    22.623] (II) NVIDIA(0): "840x525d75"         :  840 x  525 @  75.0 Hz DoubleScan  (from: X Server)
[    22.624] (II) NVIDIA(0): "840x525d70"         :  840 x  525 @  69.9 Hz DoubleScan  (from: X Server)
[    22.624] (II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
[    22.624] (II) NVIDIA(0): "840x525d60_0"       :  840 x  525 @  59.9 Hz DoubleScan  (from: X Server)
[    22.624] (II) NVIDIA(0): "832x624"            :  832 x  624 @  74.6 Hz  (from: X Server)
[    22.624] (II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.6 Hz  (from: X Server)
[    22.624] (II) NVIDIA(0): "800x600"            :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
[    22.624] (II) NVIDIA(0): "800x600_85"         :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
[    22.624] (II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
[    22.624] (II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
[    22.624] (II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
[    22.624] (II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
[    22.624] (II) NVIDIA(0): "800x600d85"         :  800 x  600 @  85.0 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "800x600d75"         :  800 x  600 @  75.0 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "800x600d70"         :  800 x  600 @  70.0 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "800x600d65"         :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "800x512"            :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "720x480"            :  720 x  480 @  59.9 Hz  (from: EDID)
[    22.625] (II) NVIDIA(0): "720x480_60"         :  720 x  480 @  59.9 Hz  (from: EDID)
[    22.625] (II) NVIDIA(0): "720x450"            :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "720x450d60"         :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
[    22.625] (II) NVIDIA(0): "720x400"            :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
[    22.625] (II) NVIDIA(0): "720x400_85"         :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
[    22.625] (II) NVIDIA(0): "700x525"            :  700 x  525 @  85.1 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "700x525d85"         :  700 x  525 @  85.1 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "700x525d75"         :  700 x  525 @  74.8 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "700x525d70"         :  700 x  525 @  70.1 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "700x525d60"         :  700 x  525 @  60.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "680x384"            :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "680x384d60"         :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "680x384d60_0"       :  680 x  384 @  59.8 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "640x512"            :  640 x  512 @  85.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "640x512d85"         :  640 x  512 @  85.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "640x512d75"         :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
[    22.626] (II) NVIDIA(0): "640x480"            :  640 x  480 @  85.0 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x480_85"         :  640 x  480 @  85.0 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz  (from: EDID)
[    22.627] (II) NVIDIA(0): "640x480_60_0"       :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x480d85"         :  640 x  480 @  85.1 Hz DoubleScan  (from: X Server)
[    22.627] (II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
[    22.627] (II) NVIDIA(0): "640x400"            :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x400_85"         :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x350"            :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "640x350_85"         :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
[    22.627] (II) NVIDIA(0): "576x432"            :  576 x  432 @ 100.1 Hz DoubleScan  (from: X Server)
[    22.627] (II) NVIDIA(0): "576x432d100"        :  576 x  432 @ 100.1 Hz DoubleScan  (from: X Server)
[    22.627] (II) NVIDIA(0): "576x432d85"         :  576 x  432 @  85.2 Hz DoubleScan  (from: X Server)
[    22.627] (II) NVIDIA(0): "576x432d85_0"       :  576 x  432 @  85.1 Hz DoubleScan  (from: X Server)
[    22.627] (II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384"            :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384i"           :  512 x  384 @  87.1 Hz Interlace DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384d85"         :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "512x384d87i"        :  512 x  384 @  87.1 Hz Interlace DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "400x300"            :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "400x300d85"         :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
[    22.628] (II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "360x200"            :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "360x200d85"         :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x240"            :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x240d85"         :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x200"            :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x200d85"         :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x175"            :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): "320x175d85"         :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
[    22.629] (II) NVIDIA(0): --- End of ModePool for LG Electronics LG TV (DFP-0): ---
[    22.629] (II) NVIDIA(0): 
[    22.629] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    22.629] (==) NVIDIA(0): 
[    22.629] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.629] (==) NVIDIA(0):     will be used as the requested mode.
[    22.630] (==) NVIDIA(0): 
[    22.630] (II) NVIDIA(0): Validated modes:
[    22.630] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    22.638] (II) NVIDIA(0): 
[    22.638] (II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
[    22.638] (II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
[    22.638] (II) NVIDIA(0): 
[    22.638] (II) NVIDIA(0): "1920x1080_60_0" : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 16)
[    22.638] (II) NVIDIA(0): "1920x1080_60_1" : 1920 x 1080 @  59.9 Hz 
[    22.638] (II) NVIDIA(0): "1920x1080_30"   : 1920 x 1080 @ 29.97/30 Hz (CEA-861B Format 34)
[    22.638] (II) NVIDIA(0): "1920x1080_24"   : 1920 x 1080 @ 23.97/24 Hz (CEA-861B Format 32)
[    22.638] (II) NVIDIA(0): "1920x1080_60i"  : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 5)
[    22.638] (II) NVIDIA(0): "1680x1050"      : 1680 x 1050 @  60.0 Hz 
[    22.638] (II) NVIDIA(0): "1680x1050_60_0" : 1680 x 1050 @  59.9 Hz 
[    22.638] (II) NVIDIA(0): "1600x1024"      : 1600 x 1024 @  60.2 Hz 
[    22.638] (II) NVIDIA(0): "1440x900"       : 1440 x  900 @  59.9 Hz 
[    22.638] (II) NVIDIA(0): "1400x1050"      : 1400 x 1050 @  74.8 Hz 
[    22.639] (II) NVIDIA(0): "1400x1050_70"   : 1400 x 1050 @  70.0 Hz 
[    22.639] (II) NVIDIA(0): "1400x1050_60"   : 1400 x 1050 @  60.0 Hz 
[    22.639] (II) NVIDIA(0): "1360x768"       : 1360 x  768 @  60.0 Hz 
[    22.639] (II) NVIDIA(0): "1360x768_60_0"  : 1360 x  768 @  59.8 Hz 
[    22.639] (II) NVIDIA(0): "1280x1024"      : 1280 x 1024 @  85.0 Hz 
[    22.639] (II) NVIDIA(0): "1280x1024_75"   : 1280 x 1024 @  75.0 Hz 
[    22.639] (II) NVIDIA(0): "1280x1024_60"   : 1280 x 1024 @  60.0 Hz 
[    22.639] (II) NVIDIA(0): "1280x960"       : 1280 x  960 @  85.0 Hz 
[    22.639] (II) NVIDIA(0): "1280x960_60"    : 1280 x  960 @  60.0 Hz 
[    22.639] (II) NVIDIA(0): "1280x720"       : 1280 x  720 @  60.0 Hz 
[    22.639] (II) NVIDIA(0): "1280x720_60_0"  : 1280 x  720 @ 59.94/60 Hz (CEA-861B Format 4)
[    22.639] (II) NVIDIA(0): "1152x864"       : 1152 x  864 @ 100.0 Hz 
[    22.639] (II) NVIDIA(0): "1152x864_85"    : 1152 x  864 @  85.1 Hz 
[    22.639] (II) NVIDIA(0): "1152x864_85_0"  : 1152 x  864 @  85.0 Hz 
[    22.639] (II) NVIDIA(0): "1152x864_75"    : 1152 x  864 @  75.0 Hz 
[    22.639] (II) NVIDIA(0): "1152x864_75_0"  : 1152 x  864 @  75.0 Hz 
[    22.639] (II) NVIDIA(0): "1152x864_70"    : 1152 x  864 @  70.0 Hz 
[    22.639] (II) NVIDIA(0): "1152x864_60"    : 1152 x  864 @  60.0 Hz 
[    22.640] (II) NVIDIA(0): "1024x768"       : 1024 x  768 @  85.0 Hz 
[    22.640] (II) NVIDIA(0): "1024x768i"      : 1024 x  768 @  87.0 Hz Interlace 
[    22.640] (II) NVIDIA(0): "1024x768_75"    : 1024 x  768 @  75.0 Hz 
[    22.640] (II) NVIDIA(0): "1024x768_70"    : 1024 x  768 @  70.1 Hz 
[    22.640] (II) NVIDIA(0): "1024x768_60"    : 1024 x  768 @  60.0 Hz 
[    22.640] (II) NVIDIA(0): "1024x768d60"    : 1024 x  768 @  60.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "960x720"        :  960 x  720 @  75.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "960x720d60"     :  960 x  720 @  60.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "960x600"        :  960 x  600 @  60.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "960x540"        :  960 x  540 @  60.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "928x696"        :  928 x  696 @  75.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "928x696d60"     :  928 x  696 @  60.1 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "896x672"        :  896 x  672 @  75.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "896x672d60"     :  896 x  672 @  60.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "840x525"        :  840 x  525 @  85.0 Hz DoubleScan 
[    22.640] (II) NVIDIA(0): "840x525d75"     :  840 x  525 @  75.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "840x525d70"     :  840 x  525 @  69.9 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "840x525d60"     :  840 x  525 @  60.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "840x525d60_0"   :  840 x  525 @  59.9 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "832x624"        :  832 x  624 @  74.6 Hz 
[    22.641] (II) NVIDIA(0): "800x600"        :  800 x  600 @  85.1 Hz 
[    22.641] (II) NVIDIA(0): "800x600_75"     :  800 x  600 @  75.0 Hz 
[    22.641] (II) NVIDIA(0): "800x600_72"     :  800 x  600 @  72.2 Hz 
[    22.641] (II) NVIDIA(0): "800x600_60"     :  800 x  600 @  60.3 Hz 
[    22.641] (II) NVIDIA(0): "800x600_56"     :  800 x  600 @  56.2 Hz 
[    22.641] (II) NVIDIA(0): "800x600d85"     :  800 x  600 @  85.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "800x600d75"     :  800 x  600 @  75.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "800x600d70"     :  800 x  600 @  70.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "800x600d65"     :  800 x  600 @  65.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "800x600d60"     :  800 x  600 @  60.0 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "800x512"        :  800 x  512 @  60.2 Hz DoubleScan 
[    22.641] (II) NVIDIA(0): "720x480"        :  720 x  480 @  59.9 Hz 
[    22.641] (II) NVIDIA(0): "720x450"        :  720 x  450 @  59.9 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "720x400"        :  720 x  400 @  85.0 Hz 
[    22.642] (II) NVIDIA(0): "700x525"        :  700 x  525 @  85.1 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "700x525d75"     :  700 x  525 @  74.8 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "700x525d70"     :  700 x  525 @  70.1 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "700x525d60"     :  700 x  525 @  60.0 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "680x384"        :  680 x  384 @  60.0 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "680x384d60_0"   :  680 x  384 @  59.8 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "640x512"        :  640 x  512 @  85.0 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "640x512d75"     :  640 x  512 @  75.0 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "640x512d60"     :  640 x  512 @  60.0 Hz DoubleScan 
[    22.642] (II) NVIDIA(0): "640x480"        :  640 x  480 @  85.0 Hz 
[    22.642] (II) NVIDIA(0): "640x480_75"     :  640 x  480 @  75.0 Hz 
[    22.642] (II) NVIDIA(0): "640x480_73"     :  640 x  480 @  72.8 Hz 
[    22.642] (II) NVIDIA(0): "640x480_60"     :  640 x  480 @  60.0 Hz 
[    22.642] (II) NVIDIA(0): "640x480_60_0"   :  640 x  480 @  59.9 Hz 
[    22.642] (II) NVIDIA(0): "640x480d85"     :  640 x  480 @  85.1 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "640x480d60"     :  640 x  480 @  60.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "640x400"        :  640 x  400 @  85.1 Hz 
[    22.643] (II) NVIDIA(0): "640x350"        :  640 x  350 @  85.1 Hz 
[    22.643] (II) NVIDIA(0): "576x432"        :  576 x  432 @ 100.1 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "576x432d85"     :  576 x  432 @  85.2 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "576x432d85_0"   :  576 x  432 @  85.1 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "576x432d75"     :  576 x  432 @  75.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "576x432d75_0"   :  576 x  432 @  75.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "576x432d70"     :  576 x  432 @  70.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "576x432d60"     :  576 x  432 @  60.1 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "512x384"        :  512 x  384 @  85.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "512x384i"       :  512 x  384 @  87.1 Hz Interlace DoubleScan 
[    22.643] (II) NVIDIA(0): "512x384d75"     :  512 x  384 @  75.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "512x384d70"     :  512 x  384 @  70.1 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "512x384d60"     :  512 x  384 @  60.0 Hz DoubleScan 
[    22.643] (II) NVIDIA(0): "416x312"        :  416 x  312 @  74.7 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "400x300"        :  400 x  300 @  85.3 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "400x300d75"     :  400 x  300 @  75.1 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "400x300d72"     :  400 x  300 @  72.2 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "400x300d60"     :  400 x  300 @  60.3 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "400x300d56"     :  400 x  300 @  56.3 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "360x200"        :  360 x  200 @  85.0 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "320x240"        :  320 x  240 @  85.2 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "320x240d75"     :  320 x  240 @  75.0 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "320x240d73"     :  320 x  240 @  72.8 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "320x240d60"     :  320 x  240 @  60.1 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "320x200"        :  320 x  200 @  85.3 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): "320x175"        :  320 x  175 @  85.3 Hz DoubleScan 
[    22.644] (II) NVIDIA(0): 
[    22.674] (**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
[    22.675] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.675] (--) Depth 24 pixmap format is 32 bpp
[    22.675] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.676] (II) NVIDIA(0): Initialized GPU GART.
[    22.682] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.760] (II) Loading extension NV-GLX
[    22.880] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    22.908] (==) NVIDIA(0): Disabling shared memory pixmaps
[    22.908] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    22.908] (==) NVIDIA(0): Backing store disabled
[    22.908] (==) NVIDIA(0): Silken mouse enabled
[    22.919] (==) NVIDIA(0): DPMS enabled
[    22.919] (II) Loading extension NV-CONTROL
[    22.920] (II) Loading extension XINERAMA
[    22.920] (II) Loading sub module "dri2"
[    22.920] (II) LoadModule: "dri2"
[    22.921] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.921] (II) NVIDIA(0): [DRI2] Setup complete
[    22.921] (==) RandR enabled
[    22.921] (II) Initializing built-in extension Generic Event Extension
[    22.921] (II) Initializing built-in extension SHAPE
[    22.921] (II) Initializing built-in extension MIT-SHM
[    22.921] (II) Initializing built-in extension XInputExtension
[    22.921] (II) Initializing built-in extension XTEST
[    22.921] (II) Initializing built-in extension BIG-REQUESTS
[    22.921] (II) Initializing built-in extension SYNC
[    22.921] (II) Initializing built-in extension XKEYBOARD
[    22.921] (II) Initializing built-in extension XC-MISC
[    22.921] (II) Initializing built-in extension SECURITY
[    22.921] (II) Initializing built-in extension XINERAMA
[    22.921] (II) Initializing built-in extension XFIXES
[    22.921] (II) Initializing built-in extension RENDER
[    22.921] (II) Initializing built-in extension RANDR
[    22.921] (II) Initializing built-in extension COMPOSITE
[    22.921] (II) Initializing built-in extension DAMAGE
[    22.921] (II) Initializing built-in extension GESTURE
[    22.930] (II) Initializing extension GLX
[    23.113] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.147] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.147] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.147] (II) LoadModule: "evdev"
[    23.148] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.149] (II) Module evdev: vendor="X.Org Foundation"
[    23.149] 	compiled for 1.9.0, module version = 2.3.2
[    23.149] 	Module class: X.Org XInput Driver
[    23.149] 	ABI class: X.Org XInput driver, version 11.0
[    23.149] (**) Power Button: always reports core events
[    23.149] (**) Power Button: Device: "/dev/input/event1"
[    23.156] (II) Power Button: Found keys
[    23.156] (II) Power Button: Configuring as keyboard
[    23.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.156] (**) Option "xkb_rules" "evdev"
[    23.157] (**) Option "xkb_model" "pc105"
[    23.157] (**) Option "xkb_layout" "us"
[    23.162] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.162] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.162] (**) Power Button: always reports core events
[    23.162] (**) Power Button: Device: "/dev/input/event0"
[    23.172] (II) Power Button: Found keys
[    23.172] (II) Power Button: Configuring as keyboard
[    23.172] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.172] (**) Option "xkb_rules" "evdev"
[    23.173] (**) Option "xkb_model" "pc105"
[    23.173] (**) Option "xkb_layout" "us"
[    23.205] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) (/dev/input/event2)
[    23.205] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Applying InputClass "evdev keyboard catchall"
[    23.205] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): always reports core events
[    23.205] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Device: "/dev/input/event2"
[    23.216] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Found keys
[    23.216] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Configuring as keyboard
[    23.216] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (1784:0008)" (type: KEYBOARD)
[    23.216] (**) Option "xkb_rules" "evdev"
[    23.216] (**) Option "xkb_model" "pc105"
[    23.216] (**) Option "xkb_layout" "us"
[    27.260] (II) NVIDIA(0): Setting mode "1920x1080_60i"

```

And here is the output of dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-25-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 (Ubuntu 2.6.35-25.44-generic 2.6.35.10)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037f90000 (usable)
[    0.000000]  BIOS-e820: 0000000037f90000 - 0000000037f9e000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037f9e000 - 0000000037fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037fe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x37f90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037f90000 (usable)
[    0.000000]  modified: 0000000037f90000 - 0000000037f9e000 (ACPI data)
[    0.000000]  modified: 0000000037f9e000 - 0000000037fe0000 (ACPI NVS)
[    0.000000]  modified: 0000000037fe0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 295aa000 - 29fec000
[    0.000000] ACPI: RSDP 000fb3f0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 37f90100 0006C (v01 ACRSYS ACRPRDCT 20090617 MSFT 00000097)
[    0.000000] ACPI: FACP 37f90290 000F4 (v03 ACRSYS FACP1813 20090617 MSFT 00000097)
[    0.000000] ACPI: DSDT 37f90620 06AD8 (v01  963A1 963A1P02 00000004 INTL 20051117)
[    0.000000] ACPI: FACS 37f9e000 00040
[    0.000000] ACPI: APIC 37f90390 00080 (v01 ACRSYS APIC1813 20090617 MSFT 00000097)
[    0.000000] ACPI: MCFG 37f90410 0003C (v01 ACRSYS OEMMCFG  20090617 MSFT 00000097)
[    0.000000] ACPI: SLIC 37f90450 00176 (v01 ACRSYS ACRPRDCT 20090617 MSFT 00000097)
[    0.000000] ACPI: WDRT 37f905d0 00047 (v01 ACRSYS NV-WDRT  20090617 MSFT 00000097)
[    0.000000] ACPI: OEMB 37f9e040 00079 (v01 ACRSYS OEMB1813 20090617 MSFT 00000097)
[    0.000000] ACPI: HPET 37f9a620 00038 (v01 ACRSYS OEMHPET0 20090617 MSFT 00000097)
[    0.000000] ACPI: NVHD 37f9e0c0 00284 (v01 ACRSYS  NVHDCP  20090617 MSFT 00000097)
[    0.000000] ACPI: AWMI 37f9e350 0004E (v01 ACRSYS OEMB1813 20090617 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 7MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037f90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x00037f90
[    0.000000] On node 0 totalpages: 229150
[    0.000000] free_area_init_node: node 0, pgdat c07fffc0, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 16 pages used for memmap
[    0.000000]   HighMem zone: 1922 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u1048576
[    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227358
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=fc67910e-fcab-4bb4-93e5-d74269d81bd8 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4584960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (51 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [00295aa000 - 0029fec000]         RAMDISK
[    0.000000]   #4 [00009a3000 - 00009a6188]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009ec00 - 00000fd8c0]   BIOS reserved
[    0.000000]   #8 [00000fd9e0 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fd8c0 - 00000fd9e0]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001701000]         BOOTMEM
[    0.000000]   #15 [0001701000 - 0001701004]         BOOTMEM
[    0.000000]   #16 [0001701040 - 0001701100]         BOOTMEM
[    0.000000]   #17 [0001701100 - 0001701154]         BOOTMEM
[    0.000000]   #18 [0001701180 - 0001704180]         BOOTMEM
[    0.000000]   #19 [0001704180 - 0001704184]         BOOTMEM
[    0.000000]   #20 [00017041c0 - 0001704220]         BOOTMEM
[    0.000000]   #21 [0001704240 - 0001704265]         BOOTMEM
[    0.000000]   #22 [0001704280 - 00017042a7]         BOOTMEM
[    0.000000]   #23 [00017042c0 - 00017043f4]         BOOTMEM
[    0.000000]   #24 [0001704400 - 0001704440]         BOOTMEM
[    0.000000]   #25 [0001704440 - 0001704480]         BOOTMEM
[    0.000000]   #26 [0001704480 - 00017044c0]         BOOTMEM
[    0.000000]   #27 [00017044c0 - 0001704500]         BOOTMEM
[    0.000000]   #28 [0001704500 - 0001704540]         BOOTMEM
[    0.000000]   #29 [0001704540 - 0001704580]         BOOTMEM
[    0.000000]   #30 [0001704580 - 00017045c0]         BOOTMEM
[    0.000000]   #31 [00017045c0 - 0001704600]         BOOTMEM
[    0.000000]   #32 [0001704600 - 0001704640]         BOOTMEM
[    0.000000]   #33 [0001704640 - 0001704680]         BOOTMEM
[    0.000000]   #34 [0001704680 - 0001704690]         BOOTMEM
[    0.000000]   #35 [00017046c0 - 000170472a]         BOOTMEM
[    0.000000]   #36 [0001704740 - 00017047aa]         BOOTMEM
[    0.000000]   #37 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #38 [0001900000 - 000190e000]         BOOTMEM
[    0.000000]   #39 [0001a00000 - 0001a0e000]         BOOTMEM
[    0.000000]   #40 [0001b00000 - 0001b0e000]         BOOTMEM
[    0.000000]   #41 [00017067c0 - 00017067c4]         BOOTMEM
[    0.000000]   #42 [0001706800 - 0001706804]         BOOTMEM
[    0.000000]   #43 [0001706840 - 0001706850]         BOOTMEM
[    0.000000]   #44 [0001706880 - 0001706890]         BOOTMEM
[    0.000000]   #45 [00017068c0 - 0001706960]         BOOTMEM
[    0.000000]   #46 [0001706980 - 00017069c8]         BOOTMEM
[    0.000000]   #47 [0001706a00 - 000170aa00]         BOOTMEM
[    0.000000]   #48 [000170aa00 - 000178aa00]         BOOTMEM
[    0.000000]   #49 [000178aa00 - 00017caa00]         BOOTMEM
[    0.000000]   #50 [0001b0e000 - 0001f6d600]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:00037f90)
[    0.000000] Memory: 884532k/917056k available (4933k kernel code, 32068k reserved, 2331k data, 688k init, 7752k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d17ce - 0xc08187a8   (2331 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d17ce   (4933 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.220 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.44 BogoMIPS (lpj=6400880)
[    0.004021] pid_max: default: 32768 minimum: 301
[    0.004066] Security Framework initialized
[    0.004101] AppArmor: AppArmor initialized
[    0.004106] Yama: becoming mindful.
[    0.004224] Mount-cache hash table entries: 512
[    0.004460] Initializing cgroup subsys ns
[    0.004470] Initializing cgroup subsys cpuacct
[    0.004481] Initializing cgroup subsys memory
[    0.004499] Initializing cgroup subsys devices
[    0.004506] Initializing cgroup subsys freezer
[    0.004512] Initializing cgroup subsys net_cls
[    0.004561] CPU: Physical Processor ID: 0
[    0.004566] CPU: Processor Core ID: 0
[    0.004572] mce: CPU supports 5 MCE banks
[    0.004585] CPU0: Thermal monitoring enabled (TM1)
[    0.004593] using mwait in idle threads.
[    0.004606] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.004625] ... version:                3
[    0.004630] ... bit width:              40
[    0.004634] ... generic registers:      2
[    0.004639] ... value mask:             000000ffffffffff
[    0.004645] ... max period:             000000007fffffff
[    0.004650] ... fixed-purpose events:   3
[    0.004655] ... event mask:             0000000700000003
[    0.012129] ACPI: Core revision 20100428
[    0.029340] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.029352] ftrace: allocating 21756 entries in 43 pages
[    0.032107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032541] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073971] CPU0: Intel(R) Atom(TM) CPU  230   @ 1.60GHz stepping 02
[    0.076000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.164032] Brought up 2 CPUs
[    0.164041] Total of 2 processors activated (6400.43 BogoMIPS).
[    0.164444] devtmpfs: initialized
[    0.166480] regulator: core version 0.5
[    0.166556] Time: 14:49:54  Date: 02/06/11
[    0.166643] NET: Registered protocol family 16
[    0.168203] Trying to unpack rootfs image as initramfs...
[    0.168433] EISA bus registered
[    0.168459] ACPI: bus type pci registered
[    0.168675] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.168686] PCI: not using MMCONFIG
[    0.169023] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.169031] PCI: Using configuration type 1 for base access
[    0.173157] bio: create slab <bio-0> at 0
[    0.178937] ACPI: EC: Look up EC in DSDT
[    0.184694] ACPI: Executed 1 blocks of module-level executable AML code
[    0.207695] ACPI: Interpreter enabled
[    0.207709] ACPI: (supports S0 S3 S4 S5)
[    0.207776] ACPI: Using IOAPIC for interrupt routing
[    0.207968] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.213281] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
[    0.213292] PCI: Using MMCONFIG for extended config space
[    0.259620] ACPI: No dock devices found.
[    0.259636] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.261123] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.262309] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.262321] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.262331] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.262340] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.262350] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xfbffffff]
[    0.262359] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
[    0.262654] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
[    0.262809] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
[    0.262835] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
[    0.262848] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
[    0.262886] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.262899] pci 0000:00:03.2: PME# disabled
[    0.263078] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
[    0.263209] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
[    0.263265] pci 0000:00:04.0: supports D1 D2
[    0.263273] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.263283] pci 0000:00:04.0: PME# disabled
[    0.263331] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
[    0.263392] pci 0000:00:04.1: supports D1 D2
[    0.263399] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.263409] pci 0000:00:04.1: PME# disabled
[    0.263469] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
[    0.263523] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.263532] pci 0000:00:08.0: PME# disabled
[    0.263635] pci 0000:00:0a.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
[    0.263648] pci 0000:00:0a.0: reg 14: [io  0xd080-0xd087]
[    0.263660] pci 0000:00:0a.0: reg 18: [mem 0xfae7e800-0xfae7e8ff]
[    0.263673] pci 0000:00:0a.0: reg 1c: [mem 0xfae7e400-0xfae7e40f]
[    0.263713] pci 0000:00:0a.0: supports D1 D2
[    0.263720] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.263731] pci 0000:00:0a.0: PME# disabled
[    0.263779] pci 0000:00:0b.0: reg 10: [io  0xd000-0xd007]
[    0.263792] pci 0000:00:0b.0: reg 14: [io  0xcc00-0xcc03]
[    0.263804] pci 0000:00:0b.0: reg 18: [io  0xc880-0xc887]
[    0.263816] pci 0000:00:0b.0: reg 1c: [io  0xc800-0xc803]
[    0.263827] pci 0000:00:0b.0: reg 20: [io  0xc480-0xc48f]
[    0.263840] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
[    0.264127] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264143] pci 0000:00:0c.0: PME# disabled
[    0.264273] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264283] pci 0000:00:10.0: PME# disabled
[    0.264532] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264546] pci 0000:00:15.0: PME# disabled
[    0.264807] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264822] pci 0000:00:16.0: PME# disabled
[    0.265087] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.265103] pci 0000:00:17.0: PME# disabled
[    0.265374] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.265388] pci 0000:00:18.0: PME# disabled
[    0.265531] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.265543] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.265555] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.265567] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.265577] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.265587] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.265596] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.265606] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.265616] pci 0000:00:09.0:   bridge window [mem 0x40000000-0xfbffffff] (subtractive decode)
[    0.265626] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.265795] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.265819] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.265836] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.265864] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.265953] pci 0000:03:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.265973] pci 0000:03:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.265992] pci 0000:03:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.266006] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]
[    0.266020] pci 0000:03:00.0: reg 30: [mem 0xfafe0000-0xfaffffff pref]
[    0.266106] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.266118] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.266128] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.266141] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.266309] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.266331] pci 0000:00:15.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.266346] pci 0000:00:15.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.266369] pci 0000:00:15.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.266538] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.266562] pci 0000:00:16.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.266580] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.266607] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.266784] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.266807] pci 0000:00:17.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.266824] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.266846] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.267019] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.267040] pci 0000:00:18.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.267056] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.267079] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.267167] pci_bus 0000:00: on NUMA node 0
[    0.267192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.267826] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.268197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.268415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.268733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.268985] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.269230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.269479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.305596] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.306428] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.307268] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.308115] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.308947] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *0, disabled.
[    0.309773] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.310600] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.311421] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.312256] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.313106] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.313941] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.314772] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.315595] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.316448] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.317283] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.318115] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.318943] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *0, disabled.
[    0.319785] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.320661] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.321502] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.322359] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.323193] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.324039] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.324874] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.325701] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.326527] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.327353] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.328201] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.329039] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.329852] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.330673] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.331525] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.332431] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *9
[    0.333280] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.334146] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[    0.334990] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.335838] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *7
[    0.336703] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.337545] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
[    0.338384] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.339337] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.340202] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *0, disabled.
[    0.341045] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *0, disabled.
[    0.341896] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
[    0.342734] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.343561] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.344424] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
[    0.345281] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
[    0.346127] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *15
[    0.346972] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *14
[    0.347156] HEST: Table is not found!
[    0.347429] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.347438] vgaarb: loaded
[    0.348047] SCSI subsystem initialized
[    0.348274] libata version 3.00 loaded.
[    0.348489] usbcore: registered new interface driver usbfs
[    0.348543] usbcore: registered new interface driver hub
[    0.348643] usbcore: registered new device driver usb
[    0.350068] ACPI: WMI: Mapper loaded
[    0.350077] PCI: Using ACPI for IRQ routing
[    0.350096] PCI: pci_cache_line_size set to 64 bytes
[    0.350279] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.350289] reserve RAM buffer: 0000000037f90000 - 0000000037ffffff 
[    0.350626] NetLabel: Initializing
[    0.350633] NetLabel:  domain hash size = 128
[    0.350638] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.350674] NetLabel:  unlabeled traffic allowed by default
[    0.350796] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.350812] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.350830] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.360086] Switching to clocksource tsc
[    0.389085] AppArmor: AppArmor Filesystem Enabled
[    0.389137] pnp: PnP ACPI init
[    0.389184] ACPI: bus type pnp registered
[    0.406278] pnp: PnP ACPI: found 10 devices
[    0.406289] ACPI: ACPI bus type pnp unregistered
[    0.406299] PnPBIOS: Disabled by ACPI PNP
[    0.406346] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.406356] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.406367] system 00:04: [io  0x4000-0x407f] has been reserved
[    0.406376] system 00:04: [io  0x4080-0x40ff] has been reserved
[    0.406386] system 00:04: [io  0x4400-0x447f] has been reserved
[    0.406396] system 00:04: [io  0x4480-0x44ff] has been reserved
[    0.406406] system 00:04: [io  0x4800-0x487f] has been reserved
[    0.406415] system 00:04: [io  0x4880-0x48ff] has been reserved
[    0.406427] system 00:04: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.406437] system 00:04: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.406448] system 00:04: [mem 0x000de000-0x000dffff window] has been reserved
[    0.406459] system 00:04: [mem 0xfefe2000-0xfefe3fff] has been reserved
[    0.406470] system 00:04: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.406480] system 00:04: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.406505] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.406515] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.406533] system 00:08: [mem 0xfc000000-0xfdffffff] has been reserved
[    0.406552] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.406562] system 00:09: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.406572] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.406583] system 00:09: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.406593] system 00:09: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.447227] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.447238] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.447249] pci 0000:00:09.0:   bridge window [mem disabled]
[    0.447259] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.447272] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.447279] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.447297] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.447310] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.447331] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.447342] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.447353] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.447364] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.447376] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.447383] pci 0000:00:15.0:   bridge window [io  disabled]
[    0.447399] pci 0000:00:15.0:   bridge window [mem disabled]
[    0.447412] pci 0000:00:15.0:   bridge window [mem pref disabled]
[    0.447432] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.447438] pci 0000:00:16.0:   bridge window [io  disabled]
[    0.447454] pci 0000:00:16.0:   bridge window [mem disabled]
[    0.447467] pci 0000:00:16.0:   bridge window [mem pref disabled]
[    0.447487] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.447493] pci 0000:00:17.0:   bridge window [io  disabled]
[    0.447511] pci 0000:00:17.0:   bridge window [mem disabled]
[    0.447524] pci 0000:00:17.0:   bridge window [mem pref disabled]
[    0.447545] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.447552] pci 0000:00:18.0:   bridge window [io  disabled]
[    0.447568] pci 0000:00:18.0:   bridge window [mem disabled]
[    0.447580] pci 0000:00:18.0:   bridge window [mem pref disabled]
[    0.447616] pci 0000:00:09.0: setting latency timer to 64
[    0.448872] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
[    0.448888]   alloc irq_desc for 23 on node -1
[    0.448895]   alloc kstat_irqs on node -1
[    0.448914] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
[    0.448932] pci 0000:00:0c.0: setting latency timer to 64
[    0.448953] pci 0000:00:10.0: setting latency timer to 64
[    0.450147] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
[    0.450162]   alloc irq_desc for 22 on node -1
[    0.450169]   alloc kstat_irqs on node -1
[    0.450188] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
[    0.450206] pci 0000:00:15.0: setting latency timer to 64
[    0.451380] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
[    0.451393]   alloc irq_desc for 21 on node -1
[    0.451399]   alloc kstat_irqs on node -1
[    0.451415] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
[    0.451432] pci 0000:00:16.0: setting latency timer to 64
[    0.452622] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 20
[    0.452635]   alloc irq_desc for 20 on node -1
[    0.452641]   alloc kstat_irqs on node -1
[    0.452657] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 20 (level, low) -> IRQ 20
[    0.452674] pci 0000:00:17.0: setting latency timer to 64
[    0.453853] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 23
[    0.453868] pci 0000:00:18.0: PCI INT A -> Link[LRP6] -> GSI 23 (level, low) -> IRQ 23
[    0.453885] pci 0000:00:18.0: setting latency timer to 64
[    0.453901] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.453909] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.453918] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.453927] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.453936] pci_bus 0000:00: resource 8 [mem 0x40000000-0xfbffffff]
[    0.453945] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.453955] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.453964] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.453972] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.453981] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.453989] pci_bus 0000:01: resource 8 [mem 0x40000000-0xfbffffff]
[    0.453998] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.454007] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.454016] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfbffffff]
[    0.454025] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.454138] NET: Registered protocol family 2
[    0.454344] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.455212] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.456351] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.456970] TCP: Hash tables configured (established 131072 bind 65536)
[    0.456982] TCP reno registered
[    0.456997] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.457022] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.457339] NET: Registered protocol family 1
[    0.492010] pci 0000:03:00.0: Boot video device
[    0.492024] PCI: CLS 64 bytes, default 64
[    0.492652] cpufreq-nforce2: No nForce2 chipset.
[    0.492771] Scanning for low memory corruption every 60 seconds
[    0.493136] audit: initializing netlink socket (disabled)
[    0.493165] type=2000 audit(1297003793.488:1): initialized
[    0.516950] highmem bounce pool size: 64 pages
[    0.516970] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.523599] VFS: Disk quotas dquot_6.5.2
[    0.523843] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.526011] fuse init (API version 7.14)
[    0.526358] msgmni has been set to 1712
[    0.527272] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.527283] io scheduler noop registered
[    0.527289] io scheduler deadline registered
[    0.527350] io scheduler cfq registered (default)
[    0.527722] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.527860]   alloc irq_desc for 40 on node -1
[    0.527867]   alloc kstat_irqs on node -1
[    0.527901] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.528161] pcieport 0000:00:15.0: setting latency timer to 64
[    0.528294]   alloc irq_desc for 41 on node -1
[    0.528301]   alloc kstat_irqs on node -1
[    0.528328] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.528548] pcieport 0000:00:16.0: setting latency timer to 64
[    0.528683]   alloc irq_desc for 42 on node -1
[    0.528690]   alloc kstat_irqs on node -1
[    0.528718] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.528947] pcieport 0000:00:17.0: setting latency timer to 64
[    0.529079]   alloc irq_desc for 43 on node -1
[    0.529086]   alloc kstat_irqs on node -1
[    0.529113] pcieport 0000:00:17.0: irq 43 for MSI/MSI-X
[    0.529331] pcieport 0000:00:18.0: setting latency timer to 64
[    0.529465]   alloc irq_desc for 44 on node -1
[    0.529472]   alloc kstat_irqs on node -1
[    0.529502] pcieport 0000:00:18.0: irq 44 for MSI/MSI-X
[    0.529819] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.529912] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.530240] intel_idle: MWAIT substates: 0x10
[    0.530247] intel_idle: v0.4 model 0x1C
[    0.530253] intel_idle: lapic_timer_reliable_states 0x2
[    0.530667] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.530683] ACPI: Power Button [PWRB]
[    0.530892] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.530905] ACPI: Power Button [PWRF]
[    0.531969] ACPI: acpi_idle yielding to intel_idle
[    0.553466] thermal LNXTHERM:01: registered as thermal_zone0
[    0.553495] ACPI: Thermal Zone [THRM] (52 C)
[    0.553741] ERST: Table is not found!
[    0.554658] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.559585] brd: module loaded
[    0.561599] loop: module loaded
[    0.563578] isapnp: Scanning for PnP cards...
[    0.603815] Fixed MDIO Bus: probed
[    0.603959] PPP generic driver version 2.4.2
[    0.604115] tun: Universal TUN/TAP device driver, 1.6
[    0.604122] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.604377] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.605541] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.605555] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    0.605597] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.605606] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.605734] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.605791] ehci_hcd 0000:00:04.1: debug port 1
[    0.605806] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.605849] ehci_hcd 0000:00:04.1: irq 22, io mem 0xfae7ec00
[    0.615684] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.616080] hub 1-0:1.0: USB hub found
[    0.616096] hub 1-0:1.0: 12 ports detected
[    0.616319] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.617476] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    0.617490] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    0.617531] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.617540] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.617693] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.617754] ohci_hcd 0000:00:04.0: irq 21, io mem 0xfae7f000
[    0.674107] hub 2-0:1.0: USB hub found
[    0.674126] hub 2-0:1.0: 12 ports detected
[    0.674334] uhci_hcd: USB Universal Host Controller Interface driver
[    0.674593] PNP: No PS/2 controller found. Probing ports directly.
[    0.676203] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.676220] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.676582] mice: PS/2 mouse device common for all mice
[    0.676947] rtc_cmos 00:06: RTC can wake from S4
[    0.677066] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.677131] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.677481] device-mapper: uevent: version 1.0.3
[    0.700417] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.716017] device-mapper: multipath: version 1.1.1 loaded
[    0.716028] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.724097] EISA: Probing bus 0 at eisa.0
[    0.724107] EISA: Cannot allocate resource for mainboard
[    0.724117] Cannot allocate resource for EISA slot 1
[    0.724125] Cannot allocate resource for EISA slot 2
[    0.724132] Cannot allocate resource for EISA slot 3
[    0.724140] Cannot allocate resource for EISA slot 4
[    0.724148] Cannot allocate resource for EISA slot 5
[    0.724156] Cannot allocate resource for EISA slot 6
[    0.724163] Cannot allocate resource for EISA slot 7
[    0.724171] Cannot allocate resource for EISA slot 8
[    0.724177] EISA: Detected 0 cards.
[    0.740490] cpuidle: using governor ladder
[    0.740701] cpuidle: using governor menu
[    0.741551] TCP cubic registered
[    0.741997] NET: Registered protocol family 10
[    0.743039] lo: Disabled Privacy Extensions
[    0.743740] NET: Registered protocol family 17
[    0.743888] Using IPI No-Shortcut mode
[    0.744190] PM: Resume from disk failed.
[    0.744219] registered taskstats version 1
[    0.744853]   Magic number: 15:695:838
[    0.745025] rtc_cmos 00:06: setting system clock to 2011-02-06 14:49:54 UTC (1297003794)
[    0.745035] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.745040] EDD information not available.
[    0.880691] Freeing initrd memory: 10504k freed
[    0.917135] isapnp: No Plug & Play device found
[    0.917182] Freeing unused kernel memory: 688k freed
[    0.918033] Write protecting the kernel text: 4936k
[    0.918124] Write protecting the kernel read-only data: 1976k
[    0.961552] udev[75]: starting version 163
[    1.155896] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.161338] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.161357] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.161372] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.212577] usb 2-4: new full speed USB device using ohci_hcd and address 2
[    1.226937] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:fb:a6:2e:d0:65
[    1.226951] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.328592] ahci 0000:00:0b.0: version 3.0
[    1.329913] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.329932] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.330029]   alloc irq_desc for 45 on node -1
[    1.330037]   alloc kstat_irqs on node -1
[    1.330062] ahci 0000:00:0b.0: irq 45 for MSI/MSI-X
[    1.330077] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    1.330217] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.330229] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
[    1.330242] ahci 0000:00:0b.0: setting latency timer to 64
[    1.332017] scsi0 : ahci
[    1.332432] scsi1 : ahci
[    1.332796] scsi2 : ahci
[    1.333067] scsi3 : ahci
[    1.333361] scsi4 : ahci
[    1.333613] scsi5 : ahci
[    1.334307] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 45
[    1.334320] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 45
[    1.334330] ata3: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76200 irq 45
[    1.334339] ata4: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76280 irq 45
[    1.334348] ata5: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76300 irq 45
[    1.334357] ata6: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76380 irq 45
[    1.424637] usb 2-4: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
[    1.424649] usb 2-4: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
[    1.652040] ata5: SATA link down (SStatus 0 SControl 300)
[    1.652048] ata3: SATA link down (SStatus 0 SControl 300)
[    1.652093] ata1: SATA link down (SStatus 0 SControl 300)
[    1.652102] ata6: SATA link down (SStatus 0 SControl 300)
[    1.652129] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.652171] ata4: SATA link down (SStatus 0 SControl 300)
[    1.669690] ata2.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133
[    1.669698] ata2.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.671164] ata2.00: configured for UDMA/133
[    1.671432] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    1.671920] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.671972] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.672437] sd 1:0:0:0: [sda] Write Protect is off
[    1.672447] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.672532] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.673246]  sda: sda1 sda2 < sda5 >
[    1.719278] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.027935] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.027946] EXT4-fs (sda1): write access will be enabled during recovery
[    2.326487] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.326511] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8912904
[    2.326575] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8912903
[    2.326599] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8912902
[    2.326620] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8912901
[    2.326640] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8912900
[    2.326658] EXT4-fs (sda1): 5 orphan inodes deleted
[    2.326666] EXT4-fs (sda1): recovery complete
[    2.519262] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.763279] Adding 2623484k swap on /dev/sda5.  Priority:-1 extents:1 across:2623484k 
[   13.819414] udev[358]: starting version 163
[   13.890594] lp: driver loaded but no devices found
[   14.027750] ACPI: resource nForce2_smbus [io  0x4d00-0x4d3f] conflicts with ACPI region IP2_ [??? 0x00004d00-0x00004d04 flags 0x5f]
[   14.027762] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.027779] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [??? 0x00004e00-0x00004e3f flags 0x30]
[   14.027788] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.318148] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.479618] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.507563] Linux agpgart interface v0.103
[   14.555975] IR NEC protocol handler initialized
[   14.643400] IR RC5(x) protocol handler initialized
[   14.652081] Registered IR keymap rc-rc6-mce
[   14.652380] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/virtual/rc/rc0/input2
[   14.652532] rc0: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/virtual/rc/rc0
[   14.652580] mceusb 2-4:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
[   14.652649] usbcore: registered new interface driver mceusb
[   14.748643] IR RC6 protocol handler initialized
[   14.807511] IR JVC protocol handler initialized
[   14.855270] IR Sony protocol handler initialized
[   14.944593] nvidia: module license 'NVIDIA' taints kernel.
[   14.944603] Disabling lock debugging due to kernel taint
[   14.954893] lirc_dev: IR Remote Control driver registered, major 251 
[   14.976236] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   14.976248] IR LIRC bridge handler initialized
[   14.986533] type=1400 audit(1297003808.735:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=659 comm="apparmor_parser"
[   14.987411] type=1400 audit(1297003808.735:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=659 comm="apparmor_parser"
[   14.987944] type=1400 audit(1297003808.735:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=659 comm="apparmor_parser"
[   15.036511] type=1400 audit(1297003808.787:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=678 comm="apparmor_parser"
[   15.623661] Registering the dns_resolver key type
[   15.623695] Slow work thread pool: Starting up
[   15.666797] Slow work thread pool: Ready
[   15.775441] CIFS VFS: Error connecting to socket. Aborting operation
[   15.775517] CIFS VFS: cifs_mount failed w/return code = -101
[   16.028451] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   16.028569] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   16.029716] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   16.029731] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   16.029742] hda_intel: Disable MSI for Nvidia chipset
[   16.029813] HDA Intel 0000:00:08.0: setting latency timer to 64
[   19.570691] type=1400 audit(1297003813.319:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=884 comm="apparmor_parser"
[   19.572353] type=1400 audit(1297003813.323:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=884 comm="apparmor_parser"
[   19.573058] type=1400 audit(1297003813.323:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=884 comm="apparmor_parser"
[   19.590891] type=1400 audit(1297003813.339:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=885 comm="apparmor_parser"
[   19.596765] type=1400 audit(1297003813.347:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=887 comm="apparmor_parser"
[   19.609926] type=1400 audit(1297003813.359:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=888 comm="apparmor_parser"
[   19.856522] hda_codec: ALC662 rev1: BIOS auto-probing.
[   20.212178] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 21
[   20.212195] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 21 (level, low) -> IRQ 21
[   20.213401] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   20.213414] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   20.213431] nvidia 0000:03:00.0: setting latency timer to 64
[   20.213444] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.216826] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   20.604125] CIFS VFS: Error connecting to socket. Aborting operation
[   20.604199] CIFS VFS: cifs_mount failed w/return code = -101
[   20.604482] CIFS VFS: Error connecting to socket. Aborting operation
[   20.604555] CIFS VFS: cifs_mount failed w/return code = -101
[   20.604867] CIFS VFS: Error connecting to socket. Aborting operation
[   20.604940] CIFS VFS: cifs_mount failed w/return code = -101
[   20.605236] CIFS VFS: Error connecting to socket. Aborting operation
[   20.605306] CIFS VFS: cifs_mount failed w/return code = -101
[   21.072397] audit_printk_skb: 9 callbacks suppressed
[   21.072408] type=1400 audit(1297003814.823:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1117 comm="apparmor_parser"
[   22.290529] CIFS VFS: cifs_mount failed w/return code = -6
[   22.525165] CIFS VFS: cifs_mount failed w/return code = -6
[   22.563524] CIFS VFS: cifs_mount failed w/return code = -6
[   22.574544] CIFS VFS: cifs_mount failed w/return code = -6
[   22.603760] CIFS VFS: cifs_mount failed w/return code = -6
[   22.613838] CIFS VFS: cifs_mount failed w/return code = -6
[   23.617641] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.916038] eth0: no IPv6 routers present
[ 1587.813616] nvidia-settings[2012]: segfault at 4c ip 0807f9c2 sp bfbe48f0 error 4 in nvidia-settings[8048000+b1000]

```

Thanks.

---

