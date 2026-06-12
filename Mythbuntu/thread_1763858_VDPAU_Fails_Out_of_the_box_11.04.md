---
title: "VDPAU Fails Out of the box 11.04"
date: 2011-05-20
forum: Mythbuntu
---

### Post by mitchell2345 on 2011-05-20
Hi,

Just did a re-install on my frontend.  VDPAU is broken out of the box:

```
2011-05-20 22:30:26.214 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-05-20 22:30:26.214 OpenGL: OpenGL renderer: GeForce 8400 GS/PCI/SSE2
2011-05-20 22:30:26.214 OpenGL: OpenGL version : 2.1.2 NVIDIA 173.14.30
2011-05-20 22:30:26.214 OpenGL: Max texture size: 8192 x 8192
2011-05-20 22:30:26.214 OpenGL: Max texture units: 4
2011-05-20 22:30:26.214 OpenGL: Direct rendering: Yes
2011-05-20 22:30:26.214 OpenGL: Initialised MythRenderOpenGL
2011-05-20 22:30:26.653 New DB connection, total: 2
2011-05-20 22:30:26.655 New DB connection, total: 3
2011-05-20 22:30:26.656 Connected to database 'mythconverg' at host: 192.168.0.254
2011-05-20 22:30:26.658 Connected to database 'mythconverg' at host: 192.168.0.254
2011-05-20 22:30:26.660 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-20 22:30:26.895 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-20 22:30:26.895 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-20 22:30:26.897 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-20 22:30:26.897 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-20 22:30:27.430 Registering Internal as a media playback plugin.
2011-05-20 22:30:27.496 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-20 22:30:27.497 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-20 22:30:27.502 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-20 22:30:27.503 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-20 22:30:27.504 Loading en_us translation for module mythgallery
2011-05-20 22:30:27.550 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-20 22:30:27.640 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-20 22:30:27.652 Loading en_us translation for module mythmusic
2011-05-20 22:30:27.672 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-20 22:30:27.714 Loading en_us translation for module mythvideo
2011-05-20 22:30:27.730 Loading en_us translation for module mythweather
2011-05-20 22:30:28.208 Found mainmenu.xml for theme 'Mythbuntu'
2011-05-20 22:30:28.856 MythCoreContext: Connecting to backend server: 192.168.0.254:6543 (try 1 of 1)
2011-05-20 22:30:28.858 Using protocol version 63
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-20 22:31:18.595 TV: Attempting to change from None to WatchingPreRecorded
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-20 22:31:20.355 AFD: Opened codec 0x9e03790, id(MPEG2VIDEO) type(Video)
2011-05-20 22:31:20.355 AFD: codec AC3 has 6 channels
2011-05-20 22:31:20.357 AFD: Opened codec 0x9e05f90, id(AC3) type(Audio)
2011-05-20 22:31:20.564 AO: Opening audio device 'front:CARD=SI7012,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2011-05-20 22:31:20.567 ALSA, Error: Setting hardware audio buffer size to 128
2011-05-20 22:31:20.568 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-05-20 22:31:20.568 ALSA, Error: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-05-20 22:31:20.568 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2011-05-20 22:31:20.813 ALSA, Error: failed to register mixer device /dev/mixer: No such file or directory
2011-05-20 22:31:20.813 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-20 22:31:20.813 AudioPlayer: Enabling Audio
2011-05-20 22:31:21.355 Clearing OpenGL painter cache.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2011-05-20 22:31:21.392 VDPAU Error: Error at mythrender_vdpau.cpp:1486 (#1, Unknown)
2011-05-20 22:31:21.392 VDPAU Error: Failed to create VDPAU device.
2011-05-20 22:31:21.392 VDPAU Error: No VDPAU device
2011-05-20 22:31:21.392 Failed to create VDPAU render device.
2011-05-20 22:31:21.392 VidOutVDPAU Error: Failed to initialise VDPAU
2011-05-20 22:31:21.395 VideoOutput, Error: Not compiled with any useable video output method.
2011-05-20 22:31:21.395 Player(0), Error: Couldn't create VideoOutput instance. Exiting..
2011-05-20 22:31:21.395 Unable to initialize video.

```

Xorg:
```
mitchell@mythfe:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 14 09:22:52 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

NVIDIA Info:
```
mitchell@mythfe:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 14 09:22:52 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Suggestions?  
Thanks,
Mitchell

---

### Post by superm1 on 2011-05-21
Do you actually have the nvidia driver installed?  Based on that it looks like it's configured, but not likely installed.

If so, how did you install it?

What's the Xorg log look like?

---

### Post by mitchell2345 on 2011-05-21
I installed it during the setup wizard....Xorg log:

```
mitchell@mythfe:~$ cat /var/log/Xorg.0.log
[    13.083] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.083] X Protocol Version 11, Revision 0
[    13.083] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    13.083] Current Operating System: Linux mythfe 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    13.083] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=ccb1f4d6-99e1-48b3-8b04-2a6b08184dd0 ro quiet splash vt.handoff=7
[    13.083] Build Date: 19 April 2011  03:33:17PM
[    13.083] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    13.083] Current version of pixman: 0.20.2
[    13.083]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    13.083] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.084] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May 20 22:29:08 2011
[    13.088] (==) Using config file: "/etc/X11/xorg.conf"
[    13.088] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.101] (==) ServerLayout "Layout0"
[    13.101] (**) |-->Screen "Screen0" (0)
[    13.101] (**) |   |-->Monitor "Monitor0"
[    13.105] (**) |   |-->Device "Device0"
[    13.105] (**) |-->Input Device "Keyboard0"
[    13.105] (**) |-->Input Device "Mouse0"
[    13.106] (==) Automatically adding devices
[    13.106] (==) Automatically enabling devices
[    13.341] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.341]    Entry deleted from font path.
[    13.341] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.341]    Entry deleted from font path.
[    13.341] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.342]    Entry deleted from font path.
[    13.350] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.350]    Entry deleted from font path.
[    13.350] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.350]    Entry deleted from font path.
[    13.363] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    13.363] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.363] (**) Extension "Composite" is disabled
[    13.364] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    13.364] (WW) Disabling Keyboard0
[    13.364] (WW) Disabling Mouse0
[    13.364] (II) Loader magic: 0x81ffde0
[    13.364] (II) Module ABI versions:
[    13.364]    X.Org ANSI C Emulation: 0.4
[    13.364]    X.Org Video Driver: 10.0
[    13.364]    X.Org XInput driver : 12.3
[    13.364]    X.Org Server Extension : 5.0
[    13.365] (--) PCI:*(0:2:0:0) 10de:06e4:0000:0000 rev 161, Mem @ 0xcf000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x0000e800/128, BIOS @ 0x????????/131072
[    13.366] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.366] (II) LoadModule: "extmod"
[    13.377] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.383] (II) Module extmod: vendor="X.Org Foundation"
[    13.383]    compiled for 1.10.1, module version = 1.0.0
[    13.383]    Module class: X.Org Server Extension
[    13.383]    ABI class: X.Org Server Extension, version 5.0
[    13.383] (II) Loading extension MIT-SCREEN-SAVER
[    13.383] (II) Loading extension XFree86-VidModeExtension
[    13.383] (II) Loading extension XFree86-DGA
[    13.385] (II) Loading extension DPMS
[    13.385] (II) Loading extension XVideo
[    13.385] (II) Loading extension XVideo-MotionCompensation
[    13.385] (II) Loading extension X-Resource
[    13.385] (II) LoadModule: "dbe"
[    13.387] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.390] (II) Module dbe: vendor="X.Org Foundation"
[    13.391]    compiled for 1.10.1, module version = 1.0.0
[    13.391]    Module class: X.Org Server Extension
[    13.391]    ABI class: X.Org Server Extension, version 5.0
[    13.391] (II) Loading extension DOUBLE-BUFFER
[    13.391] (II) LoadModule: "glx"
[    13.391] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.312] (II) Module glx: vendor="NVIDIA Corporation"
[    15.312]    compiled for 4.0.2, module version = 1.0.0
[    15.312]    Module class: X.Org Server Extension
[    15.312] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    15.312] (II) Loading extension GLX
[    15.312] (II) LoadModule: "record"
[    22.418] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.753] (II) Module record: vendor="X.Org Foundation"
[    22.753]    compiled for 1.10.1, module version = 1.13.0
[    22.753]    Module class: X.Org Server Extension
[    22.753]    ABI class: X.Org Server Extension, version 5.0
[    22.753] (II) Loading extension RECORD
[    22.753] (II) LoadModule: "dri"
[    22.755] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.760] (II) Module dri: vendor="X.Org Foundation"
[    22.760]    compiled for 1.10.1, module version = 1.0.0
[    22.761]    ABI class: X.Org Server Extension, version 5.0
[    22.761] (II) Loading extension XFree86-DRI
[    22.761] (II) LoadModule: "dri2"
[    22.763] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.769] (II) Module dri2: vendor="X.Org Foundation"
[    22.769]    compiled for 1.10.1, module version = 1.2.0
[    22.769]    ABI class: X.Org Server Extension, version 5.0
[    22.769] (II) Loading extension DRI2
[    22.769] (II) LoadModule: "nvidia"
[    22.769] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.839] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.839]    compiled for 4.0.2, module version = 1.0.0
[    22.839]    Module class: X.Org Video Driver
[    22.867] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    22.876] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.876] (++) using VT number 7

[    22.885] (II) Loading sub module "fb"
[    22.885] (II) LoadModule: "fb"
[    22.886] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.902] (II) Module fb: vendor="X.Org Foundation"
[    22.902]    compiled for 1.10.1, module version = 1.0.0
[    22.902]    ABI class: X.Org ANSI C Emulation, version 0.4
[    22.902] (II) Loading sub module "wfb"
[    22.902] (II) LoadModule: "wfb"
[    22.903] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.923] (II) Module wfb: vendor="X.Org Foundation"
[    22.924]    compiled for 1.10.1, module version = 1.0.0
[    22.924]    ABI class: X.Org ANSI C Emulation, version 0.4
[    22.924] (II) Loading sub module "ramdac"
[    22.924] (II) LoadModule: "ramdac"
[    22.924] (II) Module "ramdac" already built-in
[    22.924] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.924] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.924] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.938] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    22.938] (==) NVIDIA(0): RGB weight 888
[    22.938] (==) NVIDIA(0): Default visual is TrueColor
[    22.938] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.942] (**) NVIDIA(0): Enabling RENDER acceleration
[    26.018] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:2:0:0 (GPU-0)
[    26.348] (--) NVIDIA(0): Memory: 524288 kBytes
[    26.349] (--) NVIDIA(0): VideoBIOS: 62.98.12.00.00
[    26.349] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[    26.349] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    26.349] (--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:2:0:0:
[    26.349] (--) NVIDIA(0):     VIZ VX32L HDTV10A (DFP-0)
[    26.349] (--) NVIDIA(0): VIZ VX32L HDTV10A (DFP-0): 330.0 MHz maximum pixel clock
[    26.349] (--) NVIDIA(0): VIZ VX32L HDTV10A (DFP-0): Internal Dual Link TMDS
[    26.644] (WW) NVIDIA(0): The EDID for VIZ VX32L HDTV10A (DFP-0) contradicts itself:
[    26.644] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    26.645] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-70.000 kHz) would
[    26.645] (WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    26.645] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    26.645] (WW) NVIDIA(0): The EDID for VIZ VX32L HDTV10A (DFP-0) contradicts itself:
[    26.645] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    26.645] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-70.000 kHz) would
[    26.645] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    26.645] (WW) NVIDIA(0):     HorizSync check for mode "720x576".
[    26.645] (WW) NVIDIA(0): The EDID for VIZ VX32L HDTV10A (DFP-0) contradicts itself:
[    26.645] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    26.645] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-70.000 kHz) would
[    26.645] (WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    26.645] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    26.646] (WW) NVIDIA(0): The EDID for VIZ VX32L HDTV10A (DFP-0) contradicts itself:
[    26.646] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    26.646] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-70.000 kHz) would
[    26.646] (WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    26.646] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    26.650] (WW) NVIDIA(0): The EDID for VIZ VX32L HDTV10A (DFP-0) contradicts itself:
[    26.650] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    26.650] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-70.000 kHz) would
[    26.650] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    26.650] (WW) NVIDIA(0):     HorizSync check for mode "720x576".
[    26.651] (WW) NVIDIA(0): The EDID for VIZ VX32L HDTV10A (DFP-0) contradicts itself:
[    26.651] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    26.651] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-70.000 kHz) would
[    26.651] (WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    26.651] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    26.679] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    26.679] (==) NVIDIA(0): 
[    26.679] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    26.679] (==) NVIDIA(0):     will be used as the requested mode.
[    26.679] (==) NVIDIA(0): 
[    26.679] (II) NVIDIA(0): Validated modes:
[    26.679] (II) NVIDIA(0):     "nvidia-auto-select"
[    26.679] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 720
[    26.720] (--) NVIDIA(0): DPI set to (46, 46); computed from "UseEdidDpi" X config
[    26.720] (--) NVIDIA(0):     option
[    26.720] (==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
[    26.870] (--) Depth 24 pixmap format is 32 bpp
[    27.834] (II) NVIDIA(0): Initialized GPU GART.
[    27.847] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    28.134] (II) Loading extension NV-GLX
[    28.343] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    28.387] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    28.388] (==) NVIDIA(0): Backing store disabled
[    28.388] (==) NVIDIA(0): Silken mouse enabled
[    28.399] (**) NVIDIA(0): DPMS enabled
[    28.400] (II) Loading extension NV-CONTROL
[    28.402] (==) RandR enabled
[    28.402] (II) Initializing built-in extension Generic Event Extension
[    28.402] (II) Initializing built-in extension SHAPE
[    28.402] (II) Initializing built-in extension MIT-SHM
[    28.402] (II) Initializing built-in extension XInputExtension
[    28.403] (II) Initializing built-in extension XTEST
[    28.403] (II) Initializing built-in extension BIG-REQUESTS
[    28.403] (II) Initializing built-in extension SYNC
[    28.403] (II) Initializing built-in extension XKEYBOARD
[    28.403] (II) Initializing built-in extension XC-MISC
[    28.403] (II) Initializing built-in extension SECURITY
[    28.403] (II) Initializing built-in extension XINERAMA
[    28.403] (II) Initializing built-in extension XFIXES
[    28.403] (II) Initializing built-in extension RENDER
[    28.403] (II) Initializing built-in extension RANDR
[    28.403] (II) Initializing built-in extension COMPOSITE
[    28.403] (II) Initializing built-in extension DAMAGE
[    28.403] (II) Initializing built-in extension GESTURE
[    28.412] (II) Initializing extension GLX
[    28.528] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.573] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.573] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.573] (II) LoadModule: "evdev"
[    28.574] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.618] (II) Module evdev: vendor="X.Org Foundation"
[    28.618]    compiled for 1.10.0.902, module version = 2.6.0
[    28.619]    Module class: X.Org XInput Driver
[    28.619]    ABI class: X.Org XInput driver, version 12.3
[    28.619] (II) Using input driver 'evdev' for 'Power Button'
[    28.619] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.619] (**) Power Button: always reports core events
[    28.619] (**) Power Button: Device: "/dev/input/event1"
[    28.632] (--) Power Button: Found keys
[    28.633] (II) Power Button: Configuring as keyboard
[    28.633] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    28.633] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.633] (**) Option "xkb_rules" "evdev"
[    28.633] (**) Option "xkb_model" "pc105"
[    28.633] (**) Option "xkb_layout" "us"
[    28.648] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    28.648] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.648] (II) Using input driver 'evdev' for 'Power Button'
[    28.648] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.648] (**) Power Button: always reports core events
[    28.648] (**) Power Button: Device: "/dev/input/event0"
[    28.661] (--) Power Button: Found keys
[    28.661] (II) Power Button: Configuring as keyboard
[    28.661] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    28.661] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.662] (**) Option "xkb_rules" "evdev"
[    28.662] (**) Option "xkb_model" "pc105"
[    28.664] (**) Option "xkb_layout" "us"
[    28.701] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (045e:006d) (/dev/input/event4)
[    28.702] (**) Media Center Ed. eHome Infrared Remote Transceiver (045e:006d): Applying InputClass "evdev keyboard catchall"
[    28.702] (II) Using input driver 'evdev' for 'Media Center Ed. eHome Infrared Remote Transceiver (045e:006d)'
[    28.702] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.702] (**) Media Center Ed. eHome Infrared Remote Transceiver (045e:006d): always reports core events
[    28.702] (**) Media Center Ed. eHome Infrared Remote Transceiver (045e:006d): Device: "/dev/input/event4"
[    28.716] (--) Media Center Ed. eHome Infrared Remote Transceiver (045e:006d): Found keys
[    28.716] (II) Media Center Ed. eHome Infrared Remote Transceiver (045e:006d): Configuring as keyboard
[    28.716] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/rc/rc0/input4/event4"
[    28.716] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (045e:006d)" (type: KEYBOARD)
[    28.717] (**) Option "xkb_rules" "evdev"
[    28.717] (**) Option "xkb_model" "pc105"
[    28.717] (**) Option "xkb_layout" "us"
[    28.721] (II) config/udev: Adding input device Cypress Sem PS2/USB Browser Combo Mouse (/dev/input/event3)
[    28.722] (**) Cypress Sem PS2/USB Browser Combo Mouse: Applying InputClass "evdev pointer catchall"
[    28.722] (II) Using input driver 'evdev' for 'Cypress Sem PS2/USB Browser Combo Mouse'
[    28.722] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.722] (**) Cypress Sem PS2/USB Browser Combo Mouse: always reports core events
[    28.722] (**) Cypress Sem PS2/USB Browser Combo Mouse: Device: "/dev/input/event3"
[    28.744] (--) Cypress Sem PS2/USB Browser Combo Mouse: Found 9 mouse buttons
[    28.744] (--) Cypress Sem PS2/USB Browser Combo Mouse: Found scroll wheel(s)
[    28.744] (--) Cypress Sem PS2/USB Browser Combo Mouse: Found relative axes
[    28.744] (--) Cypress Sem PS2/USB Browser Combo Mouse: Found x and y relative axes
[    28.744] (II) Cypress Sem PS2/USB Browser Combo Mouse: Configuring as mouse
[    28.744] (II) Cypress Sem PS2/USB Browser Combo Mouse: Adding scrollwheel support
[    28.745] (**) Cypress Sem PS2/USB Browser Combo Mouse: YAxisMapping: buttons 4 and 5
[    28.745] (**) Cypress Sem PS2/USB Browser Combo Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.745] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-3/2-3:1.0/input/input3/event3"
[    28.745] (II) XINPUT: Adding extended input device "Cypress Sem PS2/USB Browser Combo Mouse" (type: MOUSE)
[    28.745] (II) Cypress Sem PS2/USB Browser Combo Mouse: initialized for relative axes.
[    28.745] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) keeping acceleration scheme 1
[    28.745] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) acceleration profile 0
[    28.745] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) acceleration factor: 2.000
[    28.745] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) acceleration threshold: 4
[    28.747] (II) config/udev: Adding input device Cypress Sem PS2/USB Browser Combo Mouse (/dev/input/mouse0)
[    28.748] (II) No input driver/identifier specified (ignoring)
[    28.753] (II) config/udev: Adding input device Key Tronic Keytronic USB Keyboard (/dev/input/event2)
[    28.753] (**) Key Tronic Keytronic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    28.753] (II) Using input driver 'evdev' for 'Key Tronic Keytronic USB Keyboard'
[    28.753] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.753] (**) Key Tronic Keytronic USB Keyboard: always reports core events
[    28.753] (**) Key Tronic Keytronic USB Keyboard: Device: "/dev/input/event2"
[    28.764] (--) Key Tronic Keytronic USB Keyboard: Found keys
[    28.764] (II) Key Tronic Keytronic USB Keyboard: Configuring as keyboard
[    28.764] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.1/usb3/3-3/3-3:1.0/input/input2/event2"
[    28.764] (II) XINPUT: Adding extended input device "Key Tronic Keytronic USB Keyboard" (type: KEYBOARD)
[    28.764] (**) Option "xkb_rules" "evdev"
[    28.764] (**) Option "xkb_model" "pc105"
[    28.764] (**) Option "xkb_layout" "us"
[    45.859] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    85.797] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    91.131] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   170.774] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   277.800] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   300.795] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   376.247] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   468.711] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   540.713] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   549.777] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   619.190] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   720.343] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   883.558] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
```

---

