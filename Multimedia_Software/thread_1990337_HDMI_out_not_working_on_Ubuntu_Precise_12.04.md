---
title: "HDMI out not working on Ubuntu Precise 12.04"
date: 2012-05-29
forum: Multimedia Software
---

### Post by crazykatz on 2012-05-29
I have a very frustrating problem I've been working on for several days. I am trying to get the HDMI out to work on my laptop. First, the system specs are:  Ubuntu Precise 12.04 64- bit, HP G60 laptop, AMD Athlon X2 2.0 Gig dual core processor, 3 Gb ram, nvidia 8200m g onboard graphics running driver version 295.53.  When the HDMI cable is connected from the laptop to the tv, the nvidia control panel sees the tv and lets me enable it. When I check the tv for a picture, it says no signal. I have spent lots of time going through every post I found on Google and trying every solution related to this problem and nothing works. I have edited my xorg.conf file many times with different configurations.  Any suggestions on how to get this working?

A couple notes- I noticed nvidia shows the tv when it's connected, but the Ubuntu display manager is unable to detect the tv. Xrandr only shows output for one screen.  I get EDID errors in the log file - maybe part of the problem? 



Here's the output of my Xorg.0.log file:


[    29.639] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    29.639] X Protocol Version 11, Revision 0
[    29.639] Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
[    29.639] Current Operating System: Linux jennifer-HP-G60-Notebook-PC 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64
[    29.639] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=e8c473bf-1af3-4cda-80d6-66b8120e949b ro quiet splash vt.handoff=7
[    29.639] Build Date: 07 May 2012  11:43:21PM
[    29.639] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.639] Current version of pixman: 0.24.4
[    29.639]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    29.639] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.639] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 29 15:38:56 2012
[    29.683] (==) Using config file: "/etc/X11/xorg.conf"
[    29.683] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.788] (==) ServerLayout "Layout0"
[    29.788] (**) |-->Screen "Screen0" (0)
[    29.788] (**) |   |-->Monitor "Monitor0"
[    29.831] (**) |   |-->Device "Device0"
[    29.831] (**) |-->Screen "Screen1" (1)
[    29.831] (**) |   |-->Monitor "Monitor1"
[    29.832] (**) |   |-->Device "Device1"
[    29.833] (**) |-->Input Device "Keyboard0"
[    29.833] (**) |-->Input Device "Mouse0"
[    29.833] (**) Option "Xinerama" "0"
[    29.833] (==) Automatically adding devices
[    29.833] (==) Automatically enabling devices
[    29.850] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.850]     Entry deleted from font path.
[    29.850] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.850]     Entry deleted from font path.
[    29.850] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.850]     Entry deleted from font path.
[    29.936] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.936]     Entry deleted from font path.
[    29.936] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.936]     Entry deleted from font path.
[    29.936] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.937]     Entry deleted from font path.
[    29.937] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.937] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.937] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    29.937] (WW) Disabling Keyboard0
[    29.937] (WW) Disabling Mouse0
[    29.937] (II) Loader magic: 0x7fbdab4e5b00
[    29.937] (II) Module ABI versions:
[    29.937]     X.Org ANSI C Emulation: 0.4
[    29.937]     X.Org Video Driver: 11.0
[    29.937]     X.Org XInput driver : 16.0
[    29.937]     X.Org Server Extension : 6.0
[    29.938] (--) PCI:*(0:2:0:0) 10de:0845:103c:360a rev 162, Mem @ 0xc1000000/16777216, 0xd0000000/268435456, 0xc4000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/131072
[    29.938] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.938] (II) LoadModule: "extmod"
[    30.133] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.148] (II) Module extmod: vendor="X.Org Foundation"
[    30.148]     compiled for 1.11.3, module version = 1.0.0
[    30.148]     Module class: X.Org Server Extension
[    30.148]     ABI class: X.Org Server Extension, version 6.0
[    30.148] (II) Loading extension MIT-SCREEN-SAVER
[    30.148] (II) Loading extension XFree86-VidModeExtension
[    30.148] (II) Loading extension XFree86-DGA
[    30.148] (II) Loading extension DPMS
[    30.148] (II) Loading extension XVideo
[    30.148] (II) Loading extension XVideo-MotionCompensation
[    30.148] (II) Loading extension X-Resource
[    30.148] (II) LoadModule: "dbe"
[    30.149] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.167] (II) Module dbe: vendor="X.Org Foundation"
[    30.167]     compiled for 1.11.3, module version = 1.0.0
[    30.167]     Module class: X.Org Server Extension
[    30.167]     ABI class: X.Org Server Extension, version 6.0
[    30.167] (II) Loading extension DOUBLE-BUFFER
[    30.167] (II) LoadModule: "glx"
[    30.167] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    31.551] (II) Module glx: vendor="NVIDIA Corporation"
[    31.563]     compiled for 4.0.2, module version = 1.0.0
[    31.563]     Module class: X.Org Server Extension
[    31.563] (II) NVIDIA GLX Module  295.53  Fri May 11 23:49:08 PDT 2012
[    31.563] (II) Loading extension GLX
[    31.563] (II) LoadModule: "record"
[    31.563] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    31.773] (II) Module record: vendor="X.Org Foundation"
[    31.773]     compiled for 1.11.3, module version = 1.13.0
[    31.773]     Module class: X.Org Server Extension
[    31.773]     ABI class: X.Org Server Extension, version 6.0
[    31.773] (II) Loading extension RECORD
[    31.773] (II) LoadModule: "dri"
[    31.774] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    31.788] (II) Module dri: vendor="X.Org Foundation"
[    31.788]     compiled for 1.11.3, module version = 1.0.0
[    31.788]     ABI class: X.Org Server Extension, version 6.0
[    31.788] (II) Loading extension XFree86-DRI
[    31.788] (II) LoadModule: "dri2"
[    31.788] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.791] (II) Module dri2: vendor="X.Org Foundation"
[    31.791]     compiled for 1.11.3, module version = 1.2.0
[    31.791]     ABI class: X.Org Server Extension, version 6.0
[    31.791] (II) Loading extension DRI2
[    31.792] (II) LoadModule: "nvidia"
[    31.792] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    31.982] (II) Module nvidia: vendor="NVIDIA Corporation"
[    31.997]     compiled for 4.0.2, module version = 1.0.0
[    31.997]     Module class: X.Org Video Driver
[    32.044] (II) NVIDIA dlloader X Driver  295.53  Fri May 11 23:29:56 PDT 2012
[    32.044] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    32.044] (++) using VT number 7

[    32.046] (II) Loading sub module "fb"
[    32.046] (II) LoadModule: "fb"
[    32.046] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.056] (II) Module fb: vendor="X.Org Foundation"
[    32.056]     compiled for 1.11.3, module version = 1.0.0
[    32.056]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.056] (II) Loading sub module "wfb"
[    32.056] (II) LoadModule: "wfb"
[    32.056] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    32.068] (II) Module wfb: vendor="X.Org Foundation"
[    32.068]     compiled for 1.11.3, module version = 1.0.0
[    32.068]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.068] (II) Loading sub module "ramdac"
[    32.068] (II) LoadModule: "ramdac"
[    32.068] (II) Module "ramdac" already built-in
[    32.081] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    32.081] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    32.081] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.092] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    32.092] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    32.092] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.093] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    32.093] (==) NVIDIA(0): RGB weight 888
[    32.093] (==) NVIDIA(0): Default visual is TrueColor
[    32.093] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.093] (**) NVIDIA(0): Option "TwinView" "0"
[    32.093] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
[    32.093] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[    32.093] (**) NVIDIA(0): Enabling 2D acceleration
[    32.862] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    32.862] (II) NVIDIA(GPU-0):     Vision stereo.
[    32.930] (II) NVIDIA(GPU-0): Display (SANYO LCD (DFP-1)) does not support NVIDIA 3D Vision
[    32.930] (II) NVIDIA(GPU-0):     stereo.
[    32.992] (II) NVIDIA(0): NVIDIA GPU GeForce 8200M G (C77) at PCI:2:0:0 (GPU-0)
[    32.992] (--) NVIDIA(0): Memory: 524288 kBytes
[    32.992] (--) NVIDIA(0): VideoBIOS: 62.77.2f.00.07
[    32.992] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    32.993] (--) NVIDIA(0): Connected display device(s) on GeForce 8200M G at PCI:2:0:0
[    32.993] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[    32.993] (--) NVIDIA(0):     SANYO LCD (DFP-1)
[    32.993] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    32.993] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    32.993] (--) NVIDIA(0): SANYO LCD (DFP-1): 165.0 MHz maximum pixel clock
[    32.993] (--) NVIDIA(0): SANYO LCD (DFP-1): Internal Single Link TMDS
[    32.993] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
[    32.994] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    32.994] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    32.994] (**) NVIDIA(0):     been enabled on all display devices.)
[    33.016] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    33.016] (II) NVIDIA(0): Validated modes:
[    33.016] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
[    33.016] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    34.073] (--) NVIDIA(0): DPI set to (102, 102); computed from "UseEdidDpi" X config
[    34.073] (--) NVIDIA(0):     option
[    34.073] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    34.073] (==) NVIDIA(1): RGB weight 888
[    34.073] (==) NVIDIA(1): Default visual is TrueColor
[    34.073] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    34.073] (**) NVIDIA(1): Option "TwinView" "1"
[    34.073] (**) NVIDIA(1): Option "MetaModes" "DFP-1: 1920x1080_60 +0+0"
[    34.073] (II) NVIDIA(1): NVIDIA GPU GeForce 8200M G (C77) at PCI:2:0:0 (GPU-0)
[    34.073] (--) NVIDIA(1): Memory: 524288 kBytes
[    34.073] (--) NVIDIA(1): VideoBIOS: 62.77.2f.00.07
[    34.073] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    34.074] (--) NVIDIA(1): Connected display device(s) on GeForce 8200M G at PCI:2:0:0
[    34.074] (--) NVIDIA(1):     Seiko/Epson (DFP-0)
[    34.075] (--) NVIDIA(1):     SANYO LCD (DFP-1)
[    34.075] (--) NVIDIA(1): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    34.075] (--) NVIDIA(1): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    34.075] (--) NVIDIA(1): SANYO LCD (DFP-1): 165.0 MHz maximum pixel clock
[    34.075] (--) NVIDIA(1): SANYO LCD (DFP-1): Internal Single Link TMDS
[    34.075] (**) NVIDIA(1): TwinView enabled
[    34.075] (II) NVIDIA(1): Display Device found referenced in MetaMode: DFP-1
[    34.075] (WW) NVIDIA(1): TwinView requested, but only 1 display devices found.
[    34.075] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    34.075] (**) NVIDIA(1):     device SANYO LCD (DFP-1) (Using EDID frequencies has been
[    34.075] (**) NVIDIA(1):     enabled on all display devices.)
[    34.075] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[    34.075] (WW) NVIDIA(1):     "1920x1080" is specified in the EDID; however, the EDID's
[    34.075] (WW) NVIDIA(1):     valid HorizSync range (15.000-46.000 kHz) would exclude
[    34.075] (WW) NVIDIA(1):     this mode's HorizSync (67.5 kHz); ignoring HorizSync check
[    34.075] (WW) NVIDIA(1):     for mode "1920x1080".
[    34.075] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[    34.075] (WW) NVIDIA(1):     "1920x1080" is specified in the EDID; however, the EDID's
[    34.075] (WW) NVIDIA(1):     valid HorizSync range (15.000-46.000 kHz) would exclude
[    34.075] (WW) NVIDIA(1):     this mode's HorizSync (67.4 kHz); ignoring HorizSync check
[    34.075] (WW) NVIDIA(1):     for mode "1920x1080".
[    34.075] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[    34.075] (WW) NVIDIA(1):     "1024x768" is specified in the EDID; however, the EDID's
[    34.075] (WW) NVIDIA(1):     valid HorizSync range (15.000-46.000 kHz) would exclude
[    34.075] (WW) NVIDIA(1):     this mode's HorizSync (48.4 kHz); ignoring HorizSync check
[    34.075] (WW) NVIDIA(1):     for mode "1024x768".
[    34.075] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[    34.075] (WW) NVIDIA(1):     "1920x1080" is specified in the EDID; however, the EDID's
[    34.075] (WW) NVIDIA(1):     valid HorizSync range (15.000-46.000 kHz) would exclude
[    34.075] (WW) NVIDIA(1):     this mode's HorizSync (67.5 kHz); ignoring HorizSync check
[    34.075] (WW) NVIDIA(1):     for mode "1920x1080".
[    34.077] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[    34.077] (WW) NVIDIA(1):     "1920x1080" is specified in the EDID; however, the EDID's
[    34.077] (WW) NVIDIA(1):     valid HorizSync range (15.000-46.000 kHz) would exclude
[    34.077] (WW) NVIDIA(1):     this mode's HorizSync (67.4 kHz); ignoring HorizSync check
[    34.077] (WW) NVIDIA(1):     for mode "1920x1080".
[    34.080] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[    34.080] (WW) NVIDIA(1):     "1024x768" is specified in the EDID; however, the EDID's
[    34.080] (WW) NVIDIA(1):     valid HorizSync range (15.000-46.000 kHz) would exclude
[    34.080] (WW) NVIDIA(1):     this mode's HorizSync (48.4 kHz); ignoring HorizSync check
[    34.080] (WW) NVIDIA(1):     for mode "1024x768".
[    34.124] (II) NVIDIA(1): Assigned Display Device: DFP-1
[    34.124] (II) NVIDIA(1): Validated modes:
[    34.124] (II) NVIDIA(1):     "DFP-1:1920x1080_60+0+0"
[    34.124] (II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
[    34.132] (WW) NVIDIA(1): Cannot find size of first mode for Seiko/Epson (DFP-0); cannot
[    34.132] (WW) NVIDIA(1):     compute DPI from Seiko/Epson (DFP-0)'s EDID.
[    34.132] (==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
[    34.132] (--) Depth 24 pixmap format is 32 bpp
[    34.133] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    34.149] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+0+0"
[    34.605] (II) Loading extension NV-GLX
[    34.719] (==) NVIDIA(0): Disabling shared memory pixmaps
[    34.719] (==) NVIDIA(0): Backing store disabled
[    34.719] (==) NVIDIA(0): Silken mouse enabled
[    34.719] (**) NVIDIA(0): DPMS enabled
[    34.719] (II) Loading extension NV-CONTROL
[    34.720] (II) Loading extension XINERAMA
[    34.720] (II) Loading sub module "dri2"
[    34.720] (II) LoadModule: "dri2"
[    34.720] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    34.720] (II) Module dri2: vendor="X.Org Foundation"
[    34.720]     compiled for 1.11.3, module version = 1.2.0
[    34.720]     ABI class: X.Org Server Extension, version 6.0
[    34.720] (II) NVIDIA(0): [DRI2] Setup complete
[    34.720] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    34.721] (==) RandR enabled
[    34.735] (II) NVIDIA(1): Setting mode "DFP-1:1920x1080_60+0+0"
[    34.884] (==) NVIDIA(1): Disabling shared memory pixmaps
[    34.884] (==) NVIDIA(1): Backing store disabled
[    34.884] (==) NVIDIA(1): Silken mouse enabled
[    34.885] (**) NVIDIA(1): DPMS enabled
[    34.885] (II) Loading sub module "dri2"
[    34.885] (II) LoadModule: "dri2"
[    34.886] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    34.886] (II) Module dri2: vendor="X.Org Foundation"
[    34.886]     compiled for 1.11.3, module version = 1.2.0
[    34.886]     ABI class: X.Org Server Extension, version 6.0
[    34.886] (II) NVIDIA(1): [DRI2] Setup complete
[    34.886] (II) NVIDIA(1): [DRI2]   VDPAU driver: nvidia
[    34.886] (==) RandR enabled
[    34.886] (II) Initializing built-in extension Generic Event Extension
[    34.886] (II) Initializing built-in extension SHAPE
[    34.886] (II) Initializing built-in extension MIT-SHM
[    34.886] (II) Initializing built-in extension XInputExtension
[    34.886] (II) Initializing built-in extension XTEST
[    34.886] (II) Initializing built-in extension BIG-REQUESTS
[    34.886] (II) Initializing built-in extension SYNC
[    34.886] (II) Initializing built-in extension XKEYBOARD
[    34.886] (II) Initializing built-in extension XC-MISC
[    34.886] (II) Initializing built-in extension SECURITY
[    34.886] (II) Initializing built-in extension XINERAMA
[    34.886] (II) Initializing built-in extension XFIXES
[    34.886] (II) Initializing built-in extension RENDER
[    34.886] (II) Initializing built-in extension RANDR
[    34.886] (II) Initializing built-in extension COMPOSITE
[    34.886] (II) Initializing built-in extension DAMAGE
[    34.888] (II) Initializing extension GLX
[    35.286] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    35.302] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    35.302] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.302] (II) LoadModule: "evdev"
[    35.302] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.514] (II) Module evdev: vendor="X.Org Foundation"
[    35.514]     compiled for 1.11.3, module version = 2.7.0
[    35.514]     Module class: X.Org XInput Driver
[    35.514]     ABI class: X.Org XInput driver, version 16.0
[    35.514] (II) Using input driver 'evdev' for 'Power Button'
[    35.514] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.514] (**) Power Button: always reports core events
[    35.514] (**) evdev: Power Button: Device: "/dev/input/event3"
[    35.514] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.514] (--) evdev: Power Button: Found keys
[    35.514] (II) evdev: Power Button: Configuring as keyboard
[    35.514] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    35.514] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    35.514] (**) Option "xkb_rules" "evdev"
[    35.514] (**) Option "xkb_model" "pc105"
[    35.514] (**) Option "xkb_layout" "us"
[    35.515] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    35.515] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.515] (II) Using input driver 'evdev' for 'Video Bus'
[    35.515] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.515] (**) Video Bus: always reports core events
[    35.515] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    35.515] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    35.515] (--) evdev: Video Bus: Found keys
[    35.515] (II) evdev: Video Bus: Configuring as keyboard
[    35.515] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10/LNXVIDEO:00/input/input5/event5"
[    35.515] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    35.515] (**) Option "xkb_rules" "evdev"
[    35.515] (**) Option "xkb_model" "pc105"
[    35.515] (**) Option "xkb_layout" "us"
[    35.516] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    35.516] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.516] (II) Using input driver 'evdev' for 'Power Button'
[    35.516] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.516] (**) Power Button: always reports core events
[    35.516] (**) evdev: Power Button: Device: "/dev/input/event2"
[    35.516] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.516] (--) evdev: Power Button: Found keys
[    35.516] (II) evdev: Power Button: Configuring as keyboard
[    35.516] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    35.516] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id
[    35.516] (**) Option "xkb_rules" "evdev"
[    35.517] (**) Option "xkb_model" "pc105"
[    35.517] (**) Option "xkb_layout" "us"
[    35.517] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    35.517] (II) No input driver specified, ignoring this device.
[    35.517] (II) This device may have been added with another device file.
[    35.518] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    35.518] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    35.518] (II) Using input driver 'evdev' for 'Sleep Button'
[    35.518] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.518] (**) Sleep Button: always reports core events
[    35.518] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    35.518] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    35.518] (--) evdev: Sleep Button: Found keys
[    35.518] (II) evdev: Sleep Button: Configuring as keyboard
[    35.518] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    35.518] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    35.518] (**) Option "xkb_rules" "evdev"
[    35.518] (**) Option "xkb_model" "pc105"
[    35.518] (**) Option "xkb_layout" "us"
[    35.519] (II) config/udev: Adding input device CNF7047 (/dev/input/event)
[    35.519] (**) CNF7047: Applying InputClass "evdev keyboard catchall"
[    35.519] (II) Using input driver 'evdev' for 'CNF7047'
[    35.519] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.519] (**) CNF7047: always reports core events
[    35.519] (**) evdev: CNF7047: Device: "/dev/input/event8"
[    35.519] (--) evdev: CNF7047: Vendor 0x4f2 Product 0xb091
[    35.519] (--) evdev: CNF7047: Found keys
[    35.519] (II) evdev: CNF7047: Configuring as keyboard
[    35.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input8/event8"
[    35.519] (II) XINPUT: Adding extended input device "CNF7047" (type: KEYBOARD, id 10)
[    35.519] (**) Option "xkb_rules" "evdev"
[    35.519] (**) Option "xkb_model" "pc105"
[    35.519] (**) Option "xkb_layout" "us"
[    35.520] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event10)
[    35.520] (II) No input driver specified, ignoring this device.
[    35.520] (II) This device may have been added with another device file.
[    35.520] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event9)
[    35.520] (II) No input driver specified, ignoring this device.
[    35.520] (II) This device may have been added with another device file.
[    35.521] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    35.521] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.521] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    35.521] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.521] (**) AT Translated Set 2 keyboard: always reports core events
[    35.521] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    35.521] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    35.521] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    35.521] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    35.521] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    35.521] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    35.521] (**) Option "xkb_rules" "evdev"
[    35.521] (**) Option "xkb_model" "pc105"
[    35.521] (**) Option "xkb_layout" "us"
[    35.522] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    35.522] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    35.522] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    35.522] (II) LoadModule: "synaptics"
[    35.522] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    35.550] (II) Module synaptics: vendor="X.Org Foundation"
[    35.550]     compiled for 1.11.3, module version = 1.6.0
[    35.550]     Module class: X.Org XInput Driver
[    35.550]     ABI class: X.Org XInput driver, version 16.0
[    35.550] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    35.550] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    35.550] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    35.550] (**) Option "Device" "/dev/input/event7"
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5592
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4916
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    35.616] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    35.616] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    35.644] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input7/event7"
[    35.644] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    35.644] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    35.644] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    35.644] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    35.644] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    35.644] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    35.644] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    35.644] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    35.644] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    35.645] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    35.645] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    35.647] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    35.647] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    35.647] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    35.647] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.647] (**) HP WMI hotkeys: always reports core events
[    35.647] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event6"
[    35.648] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    35.648] (--) evdev: HP WMI hotkeys: Found keys
[    35.648] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    35.648] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    35.648] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    35.648] (**) Option "xkb_rules" "evdev"
[    35.648] (**) Option "xkb_model" "pc105"
[    35.648] (**) Option "xkb_layout" "us"
[    59.496] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm




Here's the most recent version of my xorg.conf file:



#original xorg.conf file contents below
#Section "Device"
    #Identifier    "Default Device"
    #Option    "NoLogo"    "True"
#EndSection

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 13:37:33 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SANYO LCD"
    HorizSync       15.0 - 48.8
    VertRefresh     59.0 - 63.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8200M G"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8200M G"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-1: 1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



Suggestions are welcome. Thanks for your time.

---

### Post by papibe on 2012-05-29
Hi crazykatz.

```
[ 34.075] (WW) NVIDIA(1): The EDID for SANYO LCD (DFP-1) contradicts itself: mode
[ 34.075] (WW) NVIDIA(1): "1920x1080" is specified in the EDID; however, the EDID's
[ 34.075] (WW) NVIDIA(1): valid HorizSync range (15.000-46.000 kHz) would exclude
[ 34.075] (WW) NVIDIA(1): this mode's HorizSync (67.5 kHz); ignoring HorizSync check
[ 34.075] (WW) NVIDIA(1): for mode "1920x1080".
```
How did you generate your xorg.conf?

It looks like the frequencies defined in the monitor section, contradicts the one the driver is getting from the TV (EDID).

I would generate the configuration file again:

Start by backing up what you have:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then generate the new one:
```
sudo nvidia-xconfig
```
Make sure you are getting differnet vaules for your TV's HorizSync.

If it is not set already, I would set the default TV resolution to as 'nvidia-auto-select' as the monitor0:
```
Section "Screen"
    Identifier "Screen1"
    Device "Device1"
    Monitor "Monitor1"
    DefaultDepth 24
    Option "TwinView" "1"
    Option "metamodes" [COLOR="Red"]**"DFP-1: nvidia-auto-select +0+0"**[/COLOR]
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection
```
Then restart.

Tell us how it goes.
Regards.

---

### Post by crazykatz on 2012-05-29
Thanks for the suggestion. Just tried it, still get black screen with the words "no signal" on the tv. The log file still shows the EDID error message same as before. Here's the updated xorg.conf file contents:


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 13:37:33 UTC 2012

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.53  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Sat May 12 00:34:20 PDT 2012
#original xorg.conf file contents below
#Section "Device"
    #Identifier    "Default Device"
    #Option    "NoLogo"    "True"
#EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SANYO LCD"
    HorizSync       15.0 - 46.0
    VertRefresh     59.0 - 63.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8200M G"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8200M G"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-1: 1920x1080_60 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0; DFP-1: 1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by crazykatz on 2012-06-12
Anyone else have a suggestion?

Just a quick update. I botched up my system and had to boot from the live cd to fix it. Unknowingly, my tv was attached to the laptop via HDMI. I looked at the tv and noticed it showed output- what was on my laptop screen showed on my tv. So I checked the live cd log file and compared it with my log file. The only difference was the video driver. The cd uses nouveau and I was using nvidia.  This tells me the hdmi out to tv can work with Ubuntu. So I completely uninstalled the nvidia driver and installed the nouveau driver. Unfortunately, I am using the nouveau driver and still have the same problem- tv reports no signal. I checked xrandr, and it now shows both the tv and the laptop monitors. It did not with nvidia drivers. The xorg logfile now shows no errors. It is posted at the bottom of this message. I now have no xorg.conf file in my /etc/X11 folder.


xorg.0.log file contents:

[    19.697] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.698] X Protocol Version 11, Revision 0
[    19.698] Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
[    19.698] Current Operating System: Linux jennifer-HP-G60-Notebook-PC 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64
[    19.698] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=e8c473bf-1af3-4cda-80d6-66b8120e949b ro quiet splash vt.handoff=7
[    19.698] Build Date: 07 May 2012  11:43:21PM
[    19.698] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.698] Current version of pixman: 0.24.4
[    19.698]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    19.698] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.698] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 12 16:27:31 2012
[    19.733] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.734] (==) No Layout section.  Using the first Screen section.
[    19.734] (==) No screen section available. Using defaults.
[    19.734] (**) |-->Screen "Default Screen Section" (0)
[    19.734] (**) |   |-->Monitor "<default monitor>"
[    19.734] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.734] (==) Automatically adding devices
[    19.734] (==) Automatically enabling devices
[    19.734] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.734]     Entry deleted from font path.
[    19.734] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.734]     Entry deleted from font path.
[    19.734] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.734]     Entry deleted from font path.
[    19.734] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.734]     Entry deleted from font path.
[    19.734] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.734]     Entry deleted from font path.
[    19.734] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.734]     Entry deleted from font path.
[    19.734] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.734] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.734] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.734] (II) Loader magic: 0x7f3a6d47cb00
[    19.734] (II) Module ABI versions:
[    19.734]     X.Org ANSI C Emulation: 0.4
[    19.734]     X.Org Video Driver: 11.0
[    19.734]     X.Org XInput driver : 16.0
[    19.734]     X.Org Server Extension : 6.0
[    19.736] (--) PCI:*(0:2:0:0) 10de:0845:103c:360a rev 162, Mem @ 0xc1000000/16777216, 0xd0000000/268435456, 0xc4000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/131072
[    19.736] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.736] (II) LoadModule: "extmod"
[    19.748] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.748] (II) Module extmod: vendor="X.Org Foundation"
[    19.748]     compiled for 1.11.3, module version = 1.0.0
[    19.748]     Module class: X.Org Server Extension
[    19.748]     ABI class: X.Org Server Extension, version 6.0
[    19.748] (II) Loading extension MIT-SCREEN-SAVER
[    19.748] (II) Loading extension XFree86-VidModeExtension
[    19.748] (II) Loading extension XFree86-DGA
[    19.748] (II) Loading extension DPMS
[    19.748] (II) Loading extension XVideo
[    19.748] (II) Loading extension XVideo-MotionCompensation
[    19.748] (II) Loading extension X-Resource
[    19.748] (II) LoadModule: "dbe"
[    19.749] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.749] (II) Module dbe: vendor="X.Org Foundation"
[    19.749]     compiled for 1.11.3, module version = 1.0.0
[    19.749]     Module class: X.Org Server Extension
[    19.749]     ABI class: X.Org Server Extension, version 6.0
[    19.749] (II) Loading extension DOUBLE-BUFFER
[    19.749] (II) LoadModule: "glx"
[    19.749] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.750] (II) Module glx: vendor="X.Org Foundation"
[    19.750]     compiled for 1.11.3, module version = 1.0.0
[    19.750]     ABI class: X.Org Server Extension, version 6.0
[    19.750] (==) AIGLX enabled
[    19.750] (II) Loading extension GLX
[    19.750] (II) LoadModule: "record"
[    19.750] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.750] (II) Module record: vendor="X.Org Foundation"
[    19.750]     compiled for 1.11.3, module version = 1.13.0
[    19.750]     Module class: X.Org Server Extension
[    19.750]     ABI class: X.Org Server Extension, version 6.0
[    19.750] (II) Loading extension RECORD
[    19.750] (II) LoadModule: "dri"
[    19.750] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.751] (II) Module dri: vendor="X.Org Foundation"
[    19.751]     compiled for 1.11.3, module version = 1.0.0
[    19.751]     ABI class: X.Org Server Extension, version 6.0
[    19.751] (II) Loading extension XFree86-DRI
[    19.751] (II) LoadModule: "dri2"
[    19.751] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.751] (II) Module dri2: vendor="X.Org Foundation"
[    19.751]     compiled for 1.11.3, module version = 1.2.0
[    19.751]     ABI class: X.Org Server Extension, version 6.0
[    19.751] (II) Loading extension DRI2
[    19.751] (==) Matched nvidia as autoconfigured driver 0
[    19.751] (==) Matched nouveau as autoconfigured driver 1
[    19.751] (==) Matched nv as autoconfigured driver 2
[    19.751] (==) Matched vesa as autoconfigured driver 3
[    19.751] (==) Matched fbdev as autoconfigured driver 4
[    19.751] (==) Assigned the driver to the xf86ConfigLayout
[    19.751] (II) LoadModule: "nvidia"
[    19.752] (WW) Warning, couldn't open module nvidia
[    19.752] (II) UnloadModule: "nvidia"
[    19.752] (II) Unloading nvidia
[    19.752] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    19.752] (II) LoadModule: "nouveau"
[    19.752] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.752] (II) Module nouveau: vendor="X.Org Foundation"
[    19.752]     compiled for 1.11.3, module version = 0.0.16
[    19.752]     Module class: X.Org Video Driver
[    19.752]     ABI class: X.Org Video Driver, version 11.0
[    19.753] (II) LoadModule: "nv"
[    19.753] (WW) Warning, couldn't open module nv
[    19.753] (II) UnloadModule: "nv"
[    19.753] (II) Unloading nv
[    19.753] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.753] (II) LoadModule: "vesa"
[    19.753] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.753] (II) Module vesa: vendor="X.Org Foundation"
[    19.753]     compiled for 1.11.3, module version = 2.3.0
[    19.753]     Module class: X.Org Video Driver
[    19.753]     ABI class: X.Org Video Driver, version 11.0
[    19.753] (II) LoadModule: "fbdev"
[    19.754] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.754] (II) Module fbdev: vendor="X.Org Foundation"
[    19.754]     compiled for 1.11.3, module version = 0.4.2
[    19.754]     ABI class: X.Org Video Driver, version 11.0
[    19.754] (==) Matched nvidia as autoconfigured driver 0
[    19.754] (==) Matched nouveau as autoconfigured driver 1
[    19.754] (==) Matched nv as autoconfigured driver 2
[    19.754] (==) Matched vesa as autoconfigured driver 3
[    19.754] (==) Matched fbdev as autoconfigured driver 4
[    19.754] (==) Assigned the driver to the xf86ConfigLayout
[    19.754] (II) LoadModule: "nvidia"
[    19.754] (WW) Warning, couldn't open module nvidia
[    19.754] (II) UnloadModule: "nvidia"
[    19.754] (II) Unloading nvidia
[    19.754] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    19.754] (II) LoadModule: "nouveau"
[    19.755] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.755] (II) Module nouveau: vendor="X.Org Foundation"
[    19.755]     compiled for 1.11.3, module version = 0.0.16
[    19.755]     Module class: X.Org Video Driver
[    19.755]     ABI class: X.Org Video Driver, version 11.0
[    19.755] (II) UnloadModule: "nouveau"
[    19.755] (II) Unloading nouveau
[    19.755] (II) Failed to load module "nouveau" (already loaded, 0)
[    19.755] (II) LoadModule: "nv"
[    19.755] (WW) Warning, couldn't open module nv
[    19.755] (II) UnloadModule: "nv"
[    19.755] (II) Unloading nv
[    19.755] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.755] (II) LoadModule: "vesa"
[    19.756] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.756] (II) Module vesa: vendor="X.Org Foundation"
[    19.756]     compiled for 1.11.3, module version = 2.3.0
[    19.756]     Module class: X.Org Video Driver
[    19.756]     ABI class: X.Org Video Driver, version 11.0
[    19.756] (II) UnloadModule: "vesa"
[    19.756] (II) Unloading vesa
[    19.756] (II) Failed to load module "vesa" (already loaded, 0)
[    19.756] (II) LoadModule: "fbdev"
[    19.756] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.756] (II) Module fbdev: vendor="X.Org Foundation"
[    19.756]     compiled for 1.11.3, module version = 0.4.2
[    19.756]     ABI class: X.Org Video Driver, version 11.0
[    19.756] (II) UnloadModule: "fbdev"
[    19.756] (II) Unloading fbdev
[    19.756] (II) Failed to load module "fbdev" (already loaded, 0)
[    19.756] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    19.756] (II) NOUVEAU driver for NVIDIA chipset families :
[    19.756]     RIVA TNT        (NV04)
[    19.756]     RIVA TNT2       (NV05)
[    19.756]     GeForce 256     (NV10)
[    19.756]     GeForce 2       (NV11, NV15)
[    19.756]     GeForce 4MX     (NV17, NV1
[    19.756]     GeForce 3       (NV20)
[    19.756]     GeForce 4Ti     (NV25, NV2
[    19.756]     GeForce FX      (NV3x)
[    19.756]     GeForce 6       (NV4x)
[    19.756]     GeForce 7       (G7x)
[    19.756]     GeForce 8       (G8x)
[    19.756]     GeForce GTX 200 (NVA0)
[    19.756]     GeForce GTX 400 (NVC0)
[    19.756] (II) VESA: driver for VESA chipsets: vesa
[    19.756] (II) FBDEV: driver for framebuffer: fbdev
[    19.756] (++) using VT number 7

[    19.757] drmOpenDevice: node name is /dev/dri/card0
[    19.757] drmOpenDevice: open result is 8, (OK)
[    19.757] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    19.757] drmOpenDevice: node name is /dev/dri/card0
[    19.757] drmOpenDevice: open result is 8, (OK)
[    19.757] drmOpenByBusid: drmOpenMinor returns 8
[    19.757] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    19.757] (II) [drm] nouveau interface version: 0.0.16
[    19.757] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.757] (WW) Falling back to old probe method for vesa
[    19.757] (WW) Falling back to old probe method for fbdev
[    19.757] (II) Loading sub module "fbdevhw"
[    19.757] (II) LoadModule: "fbdevhw"
[    19.757] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.758] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.758]     compiled for 1.11.3, module version = 0.0.2
[    19.758]     ABI class: X.Org Video Driver, version 11.0
[    19.758] (II) Loading sub module "dri"
[    19.758] (II) LoadModule: "dri"
[    19.758] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.758] (II) Module dri: vendor="X.Org Foundation"
[    19.758]     compiled for 1.11.3, module version = 1.0.0
[    19.758]     ABI class: X.Org Server Extension, version 6.0
[    19.758] (II) NOUVEAU(0): Loaded DRI module
[    19.758] drmOpenDevice: node name is /dev/dri/card0
[    19.758] drmOpenDevice: open result is 9, (OK)
[    19.758] drmOpenDevice: node name is /dev/dri/card0
[    19.758] drmOpenDevice: open result is 9, (OK)
[    19.758] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    19.758] drmOpenDevice: node name is /dev/dri/card0
[    19.758] drmOpenDevice: open result is 9, (OK)
[    19.758] drmOpenByBusid: drmOpenMinor returns 9
[    19.758] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    19.758] (II) [drm] DRM interface version 1.4
[    19.758] (II) [drm] DRM open master succeeded.
[    19.758] (--) NOUVEAU(0): Chipset: "NVIDIA NVaa"
[    19.758] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    19.758] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    19.758] (==) NOUVEAU(0): RGB weight 888
[    19.758] (==) NOUVEAU(0): Default visual is TrueColor
[    19.759] (==) NOUVEAU(0): Using HW cursor
[    19.759] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    19.759] (==) NOUVEAU(0): Page flipping enabled
[    20.196] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[    20.293] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    20.499] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[    20.605] (II) NOUVEAU(0): EDID for output LVDS-1
[    20.605] (II) NOUVEAU(0): Manufacturer: SEC  Model: 3451  Serial#: 0
[    20.605] (II) NOUVEAU(0): Year: 2008  Week: 0
[    20.605] (II) NOUVEAU(0): EDID Version: 1.3
[    20.605] (II) NOUVEAU(0): Digital Display Input
[    20.605] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    20.605] (II) NOUVEAU(0): Gamma: 2.20
[    20.605] (II) NOUVEAU(0): No DPMS capabilities specified
[    20.605] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.605] (II) NOUVEAU(0): First detailed timing is preferred mode
[    20.605] (II) NOUVEAU(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    20.605] (II) NOUVEAU(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    20.606] (II) NOUVEAU(0): Manufacturer's mask: 0
[    20.606] (II) NOUVEAU(0): Supported detailed timing:
[    20.606] (II) NOUVEAU(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    20.606] (II) NOUVEAU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1480 h_border: 0
[    20.606] (II) NOUVEAU(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 780 v_border: 0
[    20.606] (II) NOUVEAU(0): Unknown vendor-specific block f
[    20.606] (II) NOUVEAU(0):  SAMSUNG
[    20.606] (II) NOUVEAU(0):  156AT01-H01
[    20.606] (II) NOUVEAU(0): EDID (in hex):
[    20.606] (II) NOUVEAU(0):     00ffffffffffff004ca3513400000000
[    20.606] (II) NOUVEAU(0):     00120103802213780a87f594574f8c27
[    20.606] (II) NOUVEAU(0):     27505400000001010101010101010101
[    20.606] (II) NOUVEAU(0):     010101010101121b567250000c303020
[    20.606] (II) NOUVEAU(0):     250058c2100000190000000f00000000
[    20.606] (II) NOUVEAU(0):     00000000001eb4027400000000fe0053
[    20.606] (II) NOUVEAU(0):     414d53554e470a2020202020000000fe
[    20.606] (II) NOUVEAU(0):     00313536415430312d4830310a20001b
[    20.606] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    20.606] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    20.606] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    20.606] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[    20.606] (II) NOUVEAU(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    20.606] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    20.606] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    20.606] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    20.606] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[    20.606] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[    20.606] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[    20.703] (II) NOUVEAU(0): EDID for output VGA-1
[    20.906] (II) Quirked EDID physical size to 2x1 cm
[    20.906] (II) NOUVEAU(0): EDID for output HDMI-1
[    20.906] (II) NOUVEAU(0): Manufacturer: SAN  Model: a01  Serial#: 16843009
[    20.906] (II) NOUVEAU(0): Year: 2008  Week: 0
[    20.906] (II) NOUVEAU(0): EDID Version: 1.3
[    20.906] (II) NOUVEAU(0): Digital Display Input
[    20.906] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 2  vert.: 1
[    20.906] (II) NOUVEAU(0): Gamma: 2.20
[    20.906] (II) NOUVEAU(0): No DPMS capabilities specified
[    20.906] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.906] (II) NOUVEAU(0): First detailed timing is preferred mode
[    20.906] (II) NOUVEAU(0): redX: 0.640 redY: 0.329   greenX: 0.289 greenY: 0.600
[    20.906] (II) NOUVEAU(0): blueX: 0.149 blueY: 0.060   whiteX: 0.279 whiteY: 0.289
[    20.906] (II) NOUVEAU(0): Supported established timings:
[    20.906] (II) NOUVEAU(0): 640x480@60Hz
[    20.906] (II) NOUVEAU(0): 800x600@60Hz
[    20.906] (II) NOUVEAU(0): 1024x768@60Hz
[    20.906] (II) NOUVEAU(0): Manufacturer's mask: 0
[    20.906] (II) NOUVEAU(0): Supported detailed timing:
[    20.906] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  16 x 9 mm
[    20.906] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    20.906] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    20.906] (II) NOUVEAU(0): Supported detailed timing:
[    20.906] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  16 x 9 mm
[    20.906] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    20.906] (II) NOUVEAU(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    20.906] (II) NOUVEAU(0): Ranges: V min: 59 V max: 63 Hz, H min: 15 H max: 46 kHz, PixClock max 165 MHz
[    20.906] (II) NOUVEAU(0): Monitor name: SANYO LCD
[    20.906] (II) NOUVEAU(0): Supported detailed timing:
[    20.907] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  16 x 9 mm
[    20.907] (II) NOUVEAU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    20.907] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    20.907] (II) NOUVEAU(0): Supported detailed timing:
[    20.907] (II) NOUVEAU(0): clock: 27.0 MHz   Image Size:  16 x 9 mm
[    20.907] (II) NOUVEAU(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    20.907] (II) NOUVEAU(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    20.907] (II) NOUVEAU(0): Supported detailed timing:
[    20.907] (II) NOUVEAU(0): clock: 27.0 MHz   Image Size:  16 x 9 mm
[    20.907] (II) NOUVEAU(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[    20.907] (II) NOUVEAU(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[    20.907] (II) NOUVEAU(0): Supported detailed timing:
[    20.907] (II) NOUVEAU(0): clock: 25.2 MHz   Image Size:  4 x 3 mm
[    20.907] (II) NOUVEAU(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    20.907] (II) NOUVEAU(0): v_active: 480  v_sync: 490  v_sync_end 492 v_blanking: 525 v_border: 0
[    20.907] (II) NOUVEAU(0): Supported detailed timing:
[    20.907] (II) NOUVEAU(0): clock: 27.0 MHz   Image Size:  4 x 3 mm
[    20.907] (II) NOUVEAU(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    20.907] (II) NOUVEAU(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    20.907] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[    20.907] (II) NOUVEAU(0): EDID (in hex):
[    20.907] (II) NOUVEAU(0):     00ffffffffffff004c2e010a01010101
[    20.907] (II) NOUVEAU(0):     00120103801009780ad258a3544a9926
[    20.907] (II) NOUVEAU(0):     0f474a21080001010101010101010101
[    20.907] (II) NOUVEAU(0):     010101010101023a801871382d40582c
[    20.907] (II) NOUVEAU(0):     450010090000001e011d8018711c1620
[    20.907] (II) NOUVEAU(0):     582c250010090000009e000000fd003b
[    20.907] (II) NOUVEAU(0):     3f0f2e10000a202020202020000000fc
[    20.907] (II) NOUVEAU(0):     0053414e594f204c43440a2020200114
[    20.907] (II) NOUVEAU(0): Printing probed modes for output HDMI-1
[    20.907] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    20.907] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    20.907] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.907] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.907] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.907] (II) NOUVEAU(0): Output LVDS-1 connected
[    20.907] (II) NOUVEAU(0): Output VGA-1 disconnected
[    20.907] (II) NOUVEAU(0): Output HDMI-1 connected
[    20.907] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[    20.907] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1024x768
[    20.907] (II) NOUVEAU(0): Output HDMI-1 using initial mode 1024x768
[    20.907] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.907] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[    20.907] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[    20.907] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    20.907] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[    20.907] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    20.907] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[    20.907] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    20.907] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[    20.907] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[    20.907] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[    20.907] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[    20.907] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[    20.907] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[    20.907] (**) NOUVEAU(0):  Driver mode "1366x768": 69.3 MHz (scaled from 0.0 MHz), 46.8 kHz, 60.0 Hz
[    20.907] (II) NOUVEAU(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    20.907] (**) NOUVEAU(0): Display dimensions: (340, 190) mm
[    20.907] (**) NOUVEAU(0): DPI set to (76, 102)
[    20.907] (II) Loading sub module "fb"
[    20.907] (II) LoadModule: "fb"
[    20.908] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.908] (II) Module fb: vendor="X.Org Foundation"
[    20.908]     compiled for 1.11.3, module version = 1.0.0
[    20.908]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.908] (II) Loading sub module "exa"
[    20.908] (II) LoadModule: "exa"
[    20.908] (II) Loading /usr/lib/xorg/modules/libexa.so
[    20.909] (II) Module exa: vendor="X.Org Foundation"
[    20.909]     compiled for 1.11.3, module version = 2.5.0
[    20.909]     ABI class: X.Org Video Driver, version 11.0
[    20.909] (II) Loading sub module "shadowfb"
[    20.909] (II) LoadModule: "shadowfb"
[    20.909] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    20.909] (II) Module shadowfb: vendor="X.Org Foundation"
[    20.909]     compiled for 1.11.3, module version = 1.0.0
[    20.909]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.909] (II) UnloadModule: "vesa"
[    20.909] (II) Unloading vesa
[    20.909] (II) UnloadModule: "fbdev"
[    20.909] (II) Unloading fbdev
[    20.909] (II) UnloadModule: "fbdevhw"
[    20.909] (II) Unloading fbdevhw
[    20.909] (--) Depth 24 pixmap format is 32 bpp
[    21.067] (II) NOUVEAU(0): Opened GPU channel 2
[    21.067] (II) NOUVEAU(0): [DRI2] Setup complete
[    21.067] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    21.067] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    21.089] (II) NOUVEAU(0): GART: 64MiB available
[    21.111] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    21.111] (II) EXA(0): Driver allocated offscreen pixmaps
[    21.111] (II) EXA(0): Driver registered support for the following operations:
[    21.111] (II)         Solid
[    21.111] (II)         Copy
[    21.111] (II)         Composite (RENDER acceleration)
[    21.111] (II)         UploadToScreen
[    21.111] (II)         DownloadFromScreen
[    21.111] (==) NOUVEAU(0): Backing store disabled
[    21.111] (==) NOUVEAU(0): Silken mouse enabled
[    21.111] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    21.111] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    21.111] (==) NOUVEAU(0): DPMS enabled
[    21.111] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.111] (--) RandR disabled
[    21.112] (II) Initializing built-in extension Generic Event Extension
[    21.112] (II) Initializing built-in extension SHAPE
[    21.112] (II) Initializing built-in extension MIT-SHM
[    21.112] (II) Initializing built-in extension XInputExtension
[    21.112] (II) Initializing built-in extension XTEST
[    21.112] (II) Initializing built-in extension BIG-REQUESTS
[    21.112] (II) Initializing built-in extension SYNC
[    21.112] (II) Initializing built-in extension XKEYBOARD
[    21.112] (II) Initializing built-in extension XC-MISC
[    21.112] (II) Initializing built-in extension SECURITY
[    21.112] (II) Initializing built-in extension XINERAMA
[    21.112] (II) Initializing built-in extension XFIXES
[    21.112] (II) Initializing built-in extension RENDER
[    21.112] (II) Initializing built-in extension RANDR
[    21.112] (II) Initializing built-in extension COMPOSITE
[    21.112] (II) Initializing built-in extension DAMAGE
[    21.256] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.256] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.256] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.256] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.258] (II) AIGLX: Loaded and initialized nouveau
[    21.258] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.325] (II) NOUVEAU(0): NVEnterVT is called.
[    22.667] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[    22.667] resize called 1024 768
[    22.679] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.684] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    22.684] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.684] (II) LoadModule: "evdev"
[    22.684] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.685] (II) Module evdev: vendor="X.Org Foundation"
[    22.685]     compiled for 1.11.3, module version = 2.6.99
[    22.685]     Module class: X.Org XInput Driver
[    22.685]     ABI class: X.Org XInput driver, version 16.0
[    22.685] (II) Using input driver 'evdev' for 'Power Button'
[    22.685] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.685] (**) Power Button: always reports core events
[    22.685] (**) evdev: Power Button: Device: "/dev/input/event3"
[    22.685] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.685] (--) evdev: Power Button: Found keys
[    22.685] (II) evdev: Power Button: Configuring as keyboard
[    22.685] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    22.685] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.685] (**) Option "xkb_rules" "evdev"
[    22.685] (**) Option "xkb_model" "pc105"
[    22.685] (**) Option "xkb_layout" "us"
[    22.686] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    22.686] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.686] (II) Using input driver 'evdev' for 'Video Bus'
[    22.686] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.686] (**) Video Bus: always reports core events
[    22.686] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    22.686] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.686] (--) evdev: Video Bus: Found keys
[    22.686] (II) evdev: Video Bus: Configuring as keyboard
[    22.686] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10/LNXVIDEO:00/input/input5/event5"
[    22.686] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    22.686] (**) Option "xkb_rules" "evdev"
[    22.686] (**) Option "xkb_model" "pc105"
[    22.686] (**) Option "xkb_layout" "us"
[    22.687] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    22.687] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.687] (II) Using input driver 'evdev' for 'Power Button'
[    22.687] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.687] (**) Power Button: always reports core events
[    22.687] (**) evdev: Power Button: Device: "/dev/input/event2"
[    22.687] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.687] (--) evdev: Power Button: Found keys
[    22.687] (II) evdev: Power Button: Configuring as keyboard
[    22.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    22.687] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 
[    22.687] (**) Option "xkb_rules" "evdev"
[    22.687] (**) Option "xkb_model" "pc105"
[    22.688] (**) Option "xkb_layout" "us"
[    22.688] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    22.688] (II) No input driver specified, ignoring this device.
[    22.688] (II) This device may have been added with another device file.
[    22.689] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    22.689] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.689] (II) Using input driver 'evdev' for 'Sleep Button'
[    22.689] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.689] (**) Sleep Button: always reports core events
[    22.689] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    22.689] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    22.689] (--) evdev: Sleep Button: Found keys
[    22.689] (II) evdev: Sleep Button: Configuring as keyboard
[    22.689] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    22.689] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    22.689] (**) Option "xkb_rules" "evdev"
[    22.689] (**) Option "xkb_model" "pc105"
[    22.689] (**) Option "xkb_layout" "us"
[    22.690] (II) config/udev: Adding input device CNF7047 (/dev/input/event6)
[    22.690] (**) CNF7047: Applying InputClass "evdev keyboard catchall"
[    22.690] (II) Using input driver 'evdev' for 'CNF7047'
[    22.690] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.690] (**) CNF7047: always reports core events
[    22.690] (**) evdev: CNF7047: Device: "/dev/input/event6"
[    22.690] (--) evdev: CNF7047: Vendor 0x4f2 Product 0xb091
[    22.690] (--) evdev: CNF7047: Found keys
[    22.690] (II) evdev: CNF7047: Configuring as keyboard
[    22.690] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input6/event6"
[    22.690] (II) XINPUT: Adding extended input device "CNF7047" (type: KEYBOARD, id 10)
[    22.690] (**) Option "xkb_rules" "evdev"
[    22.690] (**) Option "xkb_model" "pc105"
[    22.690] (**) Option "xkb_layout" "us"
[    22.691] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event10)
[    22.691] (II) No input driver specified, ignoring this device.
[    22.691] (II) This device may have been added with another device file.
[    22.691] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event9)
[    22.691] (II) No input driver specified, ignoring this device.
[    22.691] (II) This device may have been added with another device file.
[    22.692] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    22.692] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.692] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.692] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.692] (**) AT Translated Set 2 keyboard: always reports core events
[    22.692] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    22.692] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    22.692] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    22.692] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    22.692] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    22.692] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    22.692] (**) Option "xkb_rules" "evdev"
[    22.692] (**) Option "xkb_model" "pc105"
[    22.692] (**) Option "xkb_layout" "us"
[    22.693] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event
[    22.693] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.693] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.693] (II) LoadModule: "synaptics"
[    22.694] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.694] (II) Module synaptics: vendor="X.Org Foundation"
[    22.694]     compiled for 1.11.3, module version = 1.6.0
[    22.694]     Module class: X.Org XInput Driver
[    22.694]     ABI class: X.Org XInput driver, version 16.0
[    22.694] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    22.694] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.694] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.694] (**) Option "Device" "/dev/input/event8"
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5592
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4916
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    22.728] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    22.728] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.732] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[    22.732] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    22.732] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    22.732] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    22.732] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    22.732] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.732] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    22.732] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.732] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.732] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    22.733] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    22.733] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.735] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    22.735] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    22.735] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    22.735] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.735] (**) HP WMI hotkeys: always reports core events
[    22.735] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    22.735] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    22.735] (--) evdev: HP WMI hotkeys: Found keys
[    22.735] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    22.735] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    22.735] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    22.736] (**) Option "xkb_rules" "evdev"
[    22.736] (**) Option "xkb_model" "pc105"
[    22.736] (**) Option "xkb_layout" "us"
[    24.418] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    24.418] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    24.418] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    24.717] (II) Quirked EDID physical size to 2x1 cm
[    26.261] resize called 2944 1080
[    27.834] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    27.834] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    27.834] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    28.134] (II) Quirked EDID physical size to 2x1 cm
[    30.267] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    30.267] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    30.267] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    30.567] (II) Quirked EDID physical size to 2x1 cm
[    31.866] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    35.256] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    35.256] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    35.256] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    35.575] (II) Quirked EDID physical size to 2x1 cm
[    48.347] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    48.347] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    48.347] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    48.652] (II) Quirked EDID physical size to 2x1 cm
[    58.045] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    58.045] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    58.045] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    58.346] (II) Quirked EDID physical size to 2x1 cm
[   169.479] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[   169.479] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   169.479] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[   170.893] resize called 1366 768

---

