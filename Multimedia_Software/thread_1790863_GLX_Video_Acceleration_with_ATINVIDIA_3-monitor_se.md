---
title: "GLX Video Acceleration with ATI/NVIDIA 3-monitor setup?"
date: 2011-06-25
forum: Multimedia Software
---

### Post by WinstonChurchill on 2011-06-25
Hello all,

I'm currently running a three-monitor setup, two of the monitors being connected to an NVIDIA card, and the third being connected to the motherboard's onboard ATI adapter. This works, and it actually works quite well, but after installing the nvidia-current drivers (using the GNOME dialog), I am unable to get any video acceleration going. The GLX module doesn't seem to want to load, and while I'm actually quite impressed with the video performance I'm getting with the open-source drivers, I'd really like to have the OpenGL capability, as it does make things look prettier. 

Any ideas? Relevant configs and logs are below. Thanks!

**EDIT: **I should clarify - I don't care about the 3rd monitor on the ATI adapter; I'm only concerned with getting OpenGL working on the two on the NVIDIA - if that's possible, which it may not be...

System:```

Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011
Linux Beethoven 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```Video hardware:```

01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

```xorg.conf:```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" LeftOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option "Xinerama" "1"
    Option "AllowGLXWithComposite" "1"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    #Load  "dri2"
    #Load  "record"
    #Load  "dri"
    Load  "glx"
    #Load  "dbe"
    #Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option "Rotate" "left"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"  "1"          # <str>
    Option "ZaphodHeads" "1"
    Option "NoAccel" "0"
    Identifier  "Card0"
    Driver      "nvidia"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "HWcursor"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "WrappedFB"                 # [<bool>]
        #Option     "GLXVBlank"                 # [<bool>]
        #Option     "ZaphodHeads"  "1"           # <str>
        Option "ZaphodHeads" "1"
    Identifier  "Card01"
        Option "NoAccel" "0"
    Driver      "nvidia"
        BusID       "PCI:2:0:0"
    Screen      1
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"    "1"        # <str>
    Identifier  "Card1"
    Driver      "radeon"
    BusID       "PCI:1:5:0"
    Option "NoAccel" "1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card01"
    Monitor    "Monitor1"
        SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card1"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Xorg Logs:```

X.Org X Server 1.10.1
Release Date: 2011-04-15
[    41.407] X Protocol Version 11, Revision 0
[    41.407] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    41.407] Current Operating System: Linux Beethoven 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    41.407] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=07af6051-2d8e-4022-819c-101755e08448 ro quiet splash vt.handoff=7
[    41.407] Build Date: 21 May 2011  11:48:41AM
[    41.407] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    41.407] Current version of pixman: 0.20.2
[    41.407]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    41.407] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    41.407] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 25 16:00:08 2011
[    41.407] (==) Using config file: "/etc/X11/xorg.conf"
[    41.407] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    41.418] (==) ServerLayout "X.org Configured"
[    41.418] (**) |-->Screen "Screen0" (0)
[    41.418] (**) |   |-->Monitor "Monitor0"
[    41.419] (**) |   |-->Device "Card0"
[    41.419] (**) |-->Screen "Screen1" (1)
[    41.419] (**) |   |-->Monitor "Monitor1"
[    41.419] (**) |   |-->Device "Card01"
[    41.419] (**) |-->Screen "Screen2" (2)
[    41.419] (**) |   |-->Monitor "Monitor2"
[    41.419] (**) |   |-->Device "Card1"
[    41.419] (**) |-->Input Device "Mouse0"
[    41.419] (**) |-->Input Device "Keyboard0"
[    41.419] (**) Option "Xinerama" "1"
[    41.419] (==) Automatically adding devices
[    41.419] (==) Automatically enabling devices
[    41.419] (**) Xinerama: enabled
[    41.419] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    41.419]     Entry deleted from font path.
[    41.419] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    41.419] (**) ModulePath set to "/usr/lib/xorg/modules"
[    41.419] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    41.419] (WW) Disabling Mouse0
[    41.419] (WW) Disabling Keyboard0
[    41.419] (II) Loader magic: 0x7e0280
[    41.419] (II) Module ABI versions:
[    41.419]     X.Org ANSI C Emulation: 0.4
[    41.419]     X.Org Video Driver: 10.0
[    41.419]     X.Org XInput driver : 12.3
[    41.419]     X.Org Server Extension : 5.0
[    41.420] (--) PCI:*(0:1:5:0) 1002:9714:1458:d000 rev 0, Mem @ 0xd0000000/268435456, 0xfdee0000/65536, 0xfdd00000/1048576, I/O @ 0x0000be00/256
[    41.420] (--) PCI: (0:2:0:0) 10de:0614:1682:2372 rev 162, Mem @ 0xfa000000/16777216, 0xa0000000/536870912, 0xf8000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
[    41.420] (II) Open ACPI successful (/var/run/acpid.socket)
[    41.420] (II) "extmod" will be loaded by default.
[    41.420] (II) "dbe" will be loaded by default.
[    41.420] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    41.420] (II) "record" will be loaded by default.
[    41.420] (II) "dri" will be loaded by default.
[    41.420] (II) "dri2" will be loaded by default.
[    41.420] (II) LoadModule: "glx"
[    41.502] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    41.502] (II) Module glx: vendor="X.Org Foundation"
[    41.502]     compiled for 1.10.1, module version = 1.0.0
[    41.502]     ABI class: X.Org Server Extension, version 5.0
[    41.502] (==) AIGLX enabled
[    41.502] (II) Loading extension GLX
[    41.502] (II) LoadModule: "extmod"
[    41.503] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    41.503] (II) Module extmod: vendor="X.Org Foundation"
[    41.503]     compiled for 1.10.1, module version = 1.0.0
[    41.503]     Module class: X.Org Server Extension
[    41.503]     ABI class: X.Org Server Extension, version 5.0
[    41.503] (II) Loading extension MIT-SCREEN-SAVER
[    41.503] (II) Loading extension XFree86-VidModeExtension
[    41.503] (II) Loading extension XFree86-DGA
[    41.503] (II) Loading extension DPMS
[    41.503] (II) Loading extension XVideo
[    41.503] (II) Loading extension XVideo-MotionCompensation
[    41.503] (II) Loading extension X-Resource
[    41.503] (II) LoadModule: "dbe"
[    41.503] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    41.503] (II) Module dbe: vendor="X.Org Foundation"
[    41.503]     compiled for 1.10.1, module version = 1.0.0
[    41.503]     Module class: X.Org Server Extension
[    41.503]     ABI class: X.Org Server Extension, version 5.0
[    41.503] (II) Loading extension DOUBLE-BUFFER
[    41.503] (II) LoadModule: "record"
[    41.503] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    41.503] (II) Module record: vendor="X.Org Foundation"
[    41.503]     compiled for 1.10.1, module version = 1.13.0
[    41.503]     Module class: X.Org Server Extension
[    41.503]     ABI class: X.Org Server Extension, version 5.0
[    41.503] (II) Loading extension RECORD
[    41.503] (II) LoadModule: "dri"
[    41.503] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    41.503] (II) Module dri: vendor="X.Org Foundation"
[    41.503]     compiled for 1.10.1, module version = 1.0.0
[    41.503]     ABI class: X.Org Server Extension, version 5.0
[    41.503] (II) Loading extension XFree86-DRI
[    41.503] (II) LoadModule: "dri2"
[    41.504] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    41.504] (II) Module dri2: vendor="X.Org Foundation"
[    41.504]     compiled for 1.10.1, module version = 1.2.0
[    41.504]     ABI class: X.Org Server Extension, version 5.0
[    41.504] (II) Loading extension DRI2
[    41.504] (II) LoadModule: "nvidia"
[    41.504] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    41.636] (II) Module nvidia: vendor="NVIDIA Corporation"
[    41.978]     compiled for 4.0.2, module version = 1.0.0
[    41.978]     Module class: X.Org Video Driver
[    42.109] (II) LoadModule: "radeon"
[    42.109] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    42.110] (II) Module radeon: vendor="X.Org Foundation"
[    42.110]     compiled for 1.10.0, module version = 6.14.0
[    42.110]     Module class: X.Org Video Driver
[    42.110]     ABI class: X.Org Video Driver, version 10.0
[    42.110] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    42.110] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    42.110] (II) RADEON: Driver for ATI Radeon chipsets:
/* VERY LONG LIST OF SUPPORTED CARDS... */
[    42.113] (++) using VT number 7

[    42.113] (II) Loading sub module "fb"
[    42.113] (II) LoadModule: "fb"
[    42.113] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.113] (II) Module fb: vendor="X.Org Foundation"
[    42.113]     compiled for 1.10.1, module version = 1.0.0
[    42.113]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.113] (II) Loading sub module "wfb"
[    42.113] (II) LoadModule: "wfb"
[    42.114] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    42.182] (II) Module wfb: vendor="X.Org Foundation"
[    42.343]     compiled for 1.10.1, module version = 1.0.0
[    42.343]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.343] (II) Loading sub module "ramdac"
[    42.343] (II) LoadModule: "ramdac"
[    42.343] (II) Module "ramdac" already built-in
[    42.344] (WW) NVIDIA: The Composite and Xinerama extensions are both enabled, which
[    42.344] (WW) NVIDIA:     is an unsupported configuration.  The driver will continue
[    42.344] (WW) NVIDIA:     to load, but may behave strangely.
[    42.344] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    42.344] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    42.344] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.371] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    42.371] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    42.371] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.371] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    42.371] (II) [KMS] Kernel modesetting enabled.
[    42.371] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    42.371] (==) NVIDIA(0): RGB weight 888
[    42.371] (==) NVIDIA(0): Default visual is TrueColor
[    42.371] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[B][    42.371] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[    42.371] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[    42.371] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[    42.371] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[    42.371] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.[/B]
[    43.956] (II) NVIDIA(GPU-0): Display (HannStar Display Corp HZ281H (DFP-0)) does not
[    43.956] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    44.007] (II) NVIDIA(GPU-0): Display (Acer AL2216W (DFP-1)) does not support NVIDIA 3D
[    44.007] (II) NVIDIA(GPU-0):     Vision stereo.
[    44.009] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[    44.009] (--) NVIDIA(0): Memory: 524288 kBytes
[    44.009] (--) NVIDIA(0): VideoBIOS: 62.92.52.00.07
[    44.009] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    44.009] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    44.009] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[    44.009] (--) NVIDIA(0):     HannStar Display Corp HZ281H (DFP-0)
[    44.009] (--) NVIDIA(0):     Acer AL2216W (DFP-1)
[    44.009] (--) NVIDIA(0): HannStar Display Corp HZ281H (DFP-0): 330.0 MHz maximum pixel
[    44.009] (--) NVIDIA(0):     clock
[    44.009] (--) NVIDIA(0): HannStar Display Corp HZ281H (DFP-0): Internal Dual Link TMDS
[    44.009] (--) NVIDIA(0): Acer AL2216W (DFP-1): 330.0 MHz maximum pixel clock
[    44.009] (--) NVIDIA(0): Acer AL2216W (DFP-1): Internal Dual Link TMDS
[    44.259] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.259] (WW) NVIDIA(0):     itself: mode "1920x1080" is specified in the EDID;
[    44.259] (WW) NVIDIA(0):     however, the EDID's valid HorizSync range (30.000-85.000
[    44.259] (WW) NVIDIA(0):     kHz) would exclude this mode's HorizSync (28.1 kHz);
[    44.259] (WW) NVIDIA(0):     ignoring HorizSync check for mode "1920x1080".
[    44.259] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.259] (WW) NVIDIA(0):     itself: mode "720x480" is specified in the EDID; however,
[    44.259] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.259] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    44.259] (WW) NVIDIA(0):     HorizSync check for mode "720x480".
[    44.259] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.259] (WW) NVIDIA(0):     itself: mode "720x576" is specified in the EDID; however,
[    44.259] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.259] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    44.259] (WW) NVIDIA(0):     HorizSync check for mode "720x576".
[    44.259] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.259] (WW) NVIDIA(0):     itself: mode "720x480" is specified in the EDID; however,
[    44.259] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.259] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    44.259] (WW) NVIDIA(0):     HorizSync check for mode "720x480".
[    44.259] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.259] (WW) NVIDIA(0):     itself: mode "720x576" is specified in the EDID; however,
[    44.259] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.259] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    44.259] (WW) NVIDIA(0):     HorizSync check for mode "720x576".
[    44.261] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.261] (WW) NVIDIA(0):     itself: mode "1920x1080" is specified in the EDID;
[    44.261] (WW) NVIDIA(0):     however, the EDID's valid HorizSync range (30.000-85.000
[    44.261] (WW) NVIDIA(0):     kHz) would exclude this mode's HorizSync (28.1 kHz);
[    44.261] (WW) NVIDIA(0):     ignoring HorizSync check for mode "1920x1080".
[    44.262] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.262] (WW) NVIDIA(0):     itself: mode "720x480" is specified in the EDID; however,
[    44.262] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.262] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    44.262] (WW) NVIDIA(0):     HorizSync check for mode "720x480".
[    44.262] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.262] (WW) NVIDIA(0):     itself: mode "720x576" is specified in the EDID; however,
[    44.262] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.262] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    44.263] (WW) NVIDIA(0):     HorizSync check for mode "720x576".
[    44.264] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.264] (WW) NVIDIA(0):     itself: mode "720x480" is specified in the EDID; however,
[    44.264] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.264] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    44.264] (WW) NVIDIA(0):     HorizSync check for mode "720x480".
[    44.264] (WW) NVIDIA(0): The EDID for HannStar Display Corp HZ281H (DFP-0) contradicts
[    44.264] (WW) NVIDIA(0):     itself: mode "720x576" is specified in the EDID; however,
[    44.264] (WW) NVIDIA(0):     the EDID's valid HorizSync range (30.000-85.000 kHz) would
[    44.264] (WW) NVIDIA(0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    44.264] (WW) NVIDIA(0):     HorizSync check for mode "720x576".
[    44.296] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    44.296] (==) NVIDIA(0): 
[    44.296] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    44.296] (==) NVIDIA(0):     will be used as the requested mode.
[    44.296] (==) NVIDIA(0): 
[    44.296] (II) NVIDIA(0): Validated modes:
[    44.296] (II) NVIDIA(0):     "nvidia-auto-select"
[    44.296] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    44.304] (--) NVIDIA(0): DPI set to (82, 82); computed from "UseEdidDpi" X config
[    44.304] (--) NVIDIA(0):     option
[    44.304] (WW) NVIDIA(0): 32-bit ARGB GLX visuals are not currently supported with the
[    44.304] (WW) NVIDIA(0):     Xinerama extension.
[    44.304] (WW) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
[    44.305] (==) NVIDIA(1): Depth 24, (==) framebuffer bpp 32
[    44.305] (==) NVIDIA(1): RGB weight 888
[    44.305] (==) NVIDIA(1): Default visual is TrueColor
[    44.305] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    44.305] (**) NVIDIA(1): Option "Rotate" "left"
[    44.305] (**) NVIDIA(1): Using static 90-degree counterclockwise screen rotation.
[    44.305] (II) NVIDIA(1): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[    44.305] (--) NVIDIA(1): Memory: 524288 kBytes
[    44.305] (--) NVIDIA(1): VideoBIOS: 62.92.52.00.07
[    44.305] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[    44.305] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    44.305] (--) NVIDIA(1): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[    44.305] (--) NVIDIA(1):     HannStar Display Corp HZ281H (DFP-0)
[    44.305] (--) NVIDIA(1):     Acer AL2216W (DFP-1)
[    44.305] (--) NVIDIA(1): HannStar Display Corp HZ281H (DFP-0): 330.0 MHz maximum pixel
[    44.305] (--) NVIDIA(1):     clock
[    44.305] (--) NVIDIA(1): HannStar Display Corp HZ281H (DFP-0): Internal Dual Link TMDS
[    44.305] (--) NVIDIA(1): Acer AL2216W (DFP-1): 330.0 MHz maximum pixel clock
[    44.305] (--) NVIDIA(1): Acer AL2216W (DFP-1): Internal Dual Link TMDS
[    44.586] (II) NVIDIA(1): Assigned Display Device: DFP-1
[    44.586] (==) NVIDIA(1): 
[    44.586] (==) NVIDIA(1): No modes were requested; the default mode "nvidia-auto-select"
[    44.586] (==) NVIDIA(1):     will be used as the requested mode.
[    44.586] (==) NVIDIA(1): 
[    44.586] (II) NVIDIA(1): Validated modes:
[    44.586] (II) NVIDIA(1):     "nvidia-auto-select"
[    44.586] (II) NVIDIA(1): Virtual screen size determined to be 1680 x 1050
[    44.595] (--) NVIDIA(1): DPI set to (90, 88); computed from "UseEdidDpi" X config
[    44.595] (--) NVIDIA(1):     option
[    44.595] (II) NVIDIA(1): The RandR extension is not compatible with the Rotate option. 
[    44.595] (II) NVIDIA(1):     Disabling RandR.
[    44.595] (WW) NVIDIA(1): 32-bit ARGB GLX visuals are not currently supported with the
[    44.595] (WW) NVIDIA(1):     Xinerama extension.
[    44.595] (WW) NVIDIA(1): Disabling 32-bit ARGB GLX visuals.
[    44.595] (==) RADEON(2): Depth 24, (--) framebuffer bpp 32
[    44.595] (II) RADEON(2): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    44.595] (==) RADEON(2): Default visual is TrueColor
[    44.595] (**) RADEON(2): Option "NoAccel" "1"
[    44.595] (==) RADEON(2): RGB weight 888
[    44.595] (II) RADEON(2): Using 8 bits per RGB (8 bit DAC)
[    44.595] (--) RADEON(2): Chipset: "ATI Radeon HD 4290" (ChipID = 0x9714)
[    44.595] (II) RADEON(2): PCI card detected
[    44.595] drmOpenDevice: node name is /dev/dri/card0
[    44.595] drmOpenDevice: open result is 15, (OK)
[    44.595] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    44.595] drmOpenDevice: node name is /dev/dri/card0
[    44.595] drmOpenDevice: open result is 15, (OK)
[    44.595] drmOpenByBusid: drmOpenMinor returns 15
[    44.595] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    44.595] (II) RADEON(2): KMS Color Tiling: disabled
[    44.595] (II) RADEON(2): KMS Pageflipping: enabled
[    44.595] (II) RADEON(2): SwapBuffers wait for vsync: enabled
[    44.648] (II) RADEON(2): Output VGA-0 using monitor section Monitor2
[    44.652] (II) RADEON(2): Output HDMI-0 has no monitor section
[    44.705] (II) RADEON(2): EDID for output VGA-0
[    44.705] (II) RADEON(2): Manufacturer: ACR  Model: ad46  Serial#: 1900081733
[    44.705] (II) RADEON(2): Year: 2007  Week: 14
[    44.705] (II) RADEON(2): EDID Version: 1.3
[    44.705] (II) RADEON(2): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    44.705] (II) RADEON(2): Sync:  Separate
[    44.705] (II) RADEON(2): Max Image Size [cm]: horiz.: 34  vert.: 27
[    44.705] (II) RADEON(2): Gamma: 2.20
[    44.705] (II) RADEON(2): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    44.705] (II) RADEON(2): First detailed timing not preferred mode in violation of standard!
[    44.705] (II) RADEON(2): redX: 0.640 redY: 0.349   greenX: 0.284 greenY: 0.617
[    44.705] (II) RADEON(2): blueX: 0.142 blueY: 0.067   whiteX: 0.313 whiteY: 0.329
[    44.705] (II) RADEON(2): Supported established timings:
[    44.705] (II) RADEON(2): 720x400@70Hz
[    44.705] (II) RADEON(2): 640x480@60Hz
[    44.705] (II) RADEON(2): 640x480@67Hz
[    44.705] (II) RADEON(2): 640x480@72Hz
[    44.705] (II) RADEON(2): 640x480@75Hz
[    44.705] (II) RADEON(2): 800x600@56Hz
[    44.705] (II) RADEON(2): 800x600@60Hz
[    44.705] (II) RADEON(2): 800x600@72Hz
[    44.705] (II) RADEON(2): 800x600@75Hz
[    44.705] (II) RADEON(2): 832x624@75Hz
[    44.705] (II) RADEON(2): 1024x768@60Hz
[    44.705] (II) RADEON(2): 1024x768@70Hz
[    44.705] (II) RADEON(2): 1024x768@75Hz
[    44.706] (II) RADEON(2): 1280x1024@75Hz
[    44.706] (II) RADEON(2): Manufacturer's mask: 0
[    44.706] (II) RADEON(2): Supported detailed timing:
[    44.706] (II) RADEON(2): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    44.706] (II) RADEON(2): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    44.706] (II) RADEON(2): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    44.706] (II) RADEON(2): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    44.706] (II) RADEON(2): Serial No: L460C1484041
[    44.706] (II) RADEON(2): Monitor name: AL1706
[    44.706] (II) RADEON(2): EDID (in hex):
[    44.706] (II) RADEON(2):     00ffffffffffff00047246ad45f24071
[    44.706] (II) RADEON(2):     0e11010308221b78e8dc55a359489e24
[    44.706] (II) RADEON(2):     115054bfef0001010101010101010101
[    44.706] (II) RADEON(2):     010101010101302a009851002a403070
[    44.706] (II) RADEON(2):     1300520e1100001e000000fd00384b1e
[    44.706] (II) RADEON(2):     530e000a202020202020000000ff004c
[    44.706] (II) RADEON(2):     34363043313438343034310a000000fc
[    44.706] (II) RADEON(2):     00414c313730360a20202020202000d2
[    44.706] (II) RADEON(2): EDID vendor "ACR", prod id 44358
[    44.706] (II) RADEON(2):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
[    44.706] (II) RADEON(2): Using EDID range info for horizontal sync
[    44.706] (II) RADEON(2): Using EDID range info for vertical refresh
[    44.706] (II) RADEON(2): Printing DDC gathered Modelines:
[    44.706] (II) RADEON(2): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    44.706] (II) RADEON(2): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    44.706] (II) RADEON(2): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    44.706] (II) RADEON(2): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    44.706] (II) RADEON(2): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    44.706] (II) RADEON(2): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    44.706] (II) RADEON(2): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    44.706] (II) RADEON(2): Printing probed modes for output VGA-0
[    44.706] (II) RADEON(2): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    44.706] (II) RADEON(2): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    44.706] (II) RADEON(2): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    44.706] (II) RADEON(2): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    44.706] (II) RADEON(2): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    44.706] (II) RADEON(2): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    44.706] (II) RADEON(2): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    44.706] (II) RADEON(2): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    44.706] (II) RADEON(2): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    44.710] (II) RADEON(2): EDID for output HDMI-0
[    44.710] (II) RADEON(2): Output VGA-0 connected
[    44.710] (II) RADEON(2): Output HDMI-0 disconnected
[    44.710] (II) RADEON(2): Using exact sizes for initial modes
[    44.710] (II) RADEON(2): Output VGA-0 using initial mode 1280x1024
[    44.710] (II) RADEON(2): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    44.710] (II) RADEON(2): mem size init: gart size :1fdff000 vram size: s:27000000 visible:fac0000
[    44.710] (II) RADEON(2): EXA: Driver will allow EXA pixmaps in VRAM
[    44.710] (**) RADEON(2): Display dimensions: (340, 270) mm
[    44.710] (**) RADEON(2): DPI set to (95, 96)
[    44.710] (II) Loading sub module "fb"
[    44.710] (II) LoadModule: "fb"
[    44.710] (II) Loading /usr/lib/xorg/modules/libfb.so
[    44.710] (II) Module fb: vendor="X.Org Foundation"
[    44.710]     compiled for 1.10.1, module version = 1.0.0
[    44.710]     ABI class: X.Org ANSI C Emulation, version 0.4
[    44.710] (II) Loading sub module "ramdac"
[    44.710] (II) LoadModule: "ramdac"
[    44.710] (II) Module "ramdac" already built-in
[    44.710] (II) RADEON(2): GPU accel disabled or not working, using shadowfb for KMS
[    44.710] (II) Loading sub module "shadow"
[    44.710] (II) LoadModule: "shadow"
[    44.710] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    44.716] (II) Module shadow: vendor="X.Org Foundation"
[    44.716]     compiled for 1.10.1, module version = 1.1.0
[    44.716]     ABI class: X.Org ANSI C Emulation, version 0.4
[    44.716] (--) Depth 24 pixmap format is 32 bpp
[    44.716] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    44.725] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    44.761] (II) Loading extension NV-GLX
[    44.799] (==) NVIDIA(0): Disabling shared memory pixmaps
[    44.799] (==) NVIDIA(0): Backing store disabled
[    44.799] (==) NVIDIA(0): Silken mouse enabled
[    44.799] (==) NVIDIA(0): DPMS enabled
[    44.802] (II) Loading extension NV-CONTROL
[    44.803] (WW) NVIDIA(0): Option "ZaphodHeads" is not used
[    44.803] (WW) NVIDIA(0): Option "NoAccel" is not used
[    44.803] (II) Loading sub module "dri2"
[    44.803] (II) LoadModule: "dri2"
[    44.803] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    44.803] (II) Module dri2: vendor="X.Org Foundation"
[    44.803]     compiled for 1.10.1, module version = 1.2.0
[    44.803]     ABI class: X.Org Server Extension, version 5.0
[    44.803] (II) NVIDIA(0): [DRI2] Setup complete
[    44.803] (--) RandR disabled
[    44.806] (II) NVIDIA(1): Setting mode "nvidia-auto-select"
[    44.891] (==) NVIDIA(1): Disabling shared memory pixmaps
[    44.907] (==) NVIDIA(1): Backing store disabled
[    44.907] (==) NVIDIA(1): Silken mouse enabled
[    44.907] (==) NVIDIA(1): DPMS enabled
[    44.907] (WW) NVIDIA(1): Option "ZaphodHeads" is not used
[    44.907] (WW) NVIDIA(1): Option "NoAccel" is not used
[    44.907] (II) Loading sub module "dri2"
[    44.907] (II) LoadModule: "dri2"
[    44.907] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    44.908] (II) Module dri2: vendor="X.Org Foundation"
[    44.908]     compiled for 1.10.1, module version = 1.2.0
[    44.908]     ABI class: X.Org Server Extension, version 5.0
[    44.908] (II) NVIDIA(1): [DRI2] Setup complete
[    44.908] (--) RandR disabled
[    44.908] (II) RADEON(2): Front buffer size: 5120K
[    44.908] (II) RADEON(2): VRAM usage limit set to 226483K
[    44.908] (==) RADEON(2): Backing store disabled
[    44.908] (WW) RADEON(2): Direct rendering disabled
[    44.908] (II) RADEON(2): Acceleration disabled
[    44.908] (==) RADEON(2): DPMS enabled
[    44.908] (==) RADEON(2): Silken mouse enabled
[    44.908] (II) RADEON(2): RandR 1.2 enabled, ignore the following RandR disabled message.
[    44.908] (--) RandR disabled
[    44.908] (II) Initializing built-in extension Generic Event Extension
[    44.908] (II) Initializing built-in extension SHAPE
[    44.908] (II) Initializing built-in extension MIT-SHM
[    44.908] (II) Initializing built-in extension XInputExtension
[    44.908] (II) Initializing built-in extension XTEST
[    44.908] (II) Initializing built-in extension BIG-REQUESTS
[    44.908] (II) Initializing built-in extension SYNC
[    44.908] (II) Initializing built-in extension XKEYBOARD
[    44.908] (II) Initializing built-in extension XC-MISC
[    44.908] (II) Initializing built-in extension SECURITY
[    44.908] (II) Initializing built-in extension XINERAMA
[    44.908] (II) Initializing built-in extension XFIXES
[    44.908] (II) Initializing built-in extension RENDER
[    44.908] (II) Initializing built-in extension RANDR
[    44.908] (II) Initializing built-in extension COMPOSITE
[    44.908] (II) Initializing built-in extension DAMAGE
[    44.908] (II) Initializing built-in extension GESTURE
[    44.912] (II) AIGLX: Screen 0 is not DRI2 capable
[    44.912] (II) AIGLX: Screen 0 is not DRI capable
[    44.912] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    44.915] (II) AIGLX: Loaded and initialized swrast
[    44.915] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    44.915] (II) AIGLX: Screen 1 is not DRI2 capable
[    44.915] (II) AIGLX: Screen 1 is not DRI capable
[    44.915] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    44.915] (II) AIGLX: Loaded and initialized swrast
[    44.915] (II) GLX: Initialized DRISWRAST GL provider for screen 1
[    44.915] (II) AIGLX: Screen 2 is not DRI2 capable
[    44.915] (II) AIGLX: Screen 2 is not DRI capable
[    44.915] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    44.915] (II) AIGLX: Loaded and initialized swrast
[    44.915] (II) GLX: Initialized DRISWRAST GL provider for screen 2
[    44.916] (WW) NVIDIA(0): Xinerama is enabled, so RandR has likely been disabled by the
[    44.916] (WW) NVIDIA(0):     X server.
[    44.916] (WW) NVIDIA(1): Xinerama is enabled, so RandR has likely been disabled by the
[    44.916] (WW) NVIDIA(1):     X server.
[    45.023] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    45.029] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    45.029] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    45.029] (II) LoadModule: "evdev"
[    45.029] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    45.030] (II) Module evdev: vendor="X.Org Foundation"
[    45.030]     compiled for 1.10.0.902, module version = 2.6.0
[    45.030]     Module class: X.Org XInput Driver
[    45.030]     ABI class: X.Org XInput driver, version 12.3
[    45.030] (II) Using input driver 'evdev' for 'Power Button'
[    45.030] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    45.030] (**) Power Button: always reports core events
[    45.030] (**) Power Button: Device: "/dev/input/event1"
[    45.070] (--) Power Button: Found keys
[    45.070] (II) Power Button: Configuring as keyboard
[    45.070] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    45.070] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    45.070] (**) Option "xkb_rules" "evdev"
[    45.070] (**) Option "xkb_model" "pc105"
[    45.070] (**) Option "xkb_layout" "us"
[    45.071] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    45.071] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    45.071] (II) Using input driver 'evdev' for 'Power Button'
[    45.071] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    45.071] (**) Power Button: always reports core events
[    45.071] (**) Power Button: Device: "/dev/input/event0"
[    45.130] (--) Power Button: Found keys
[    45.130] (II) Power Button: Configuring as keyboard
[    45.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    45.130] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    45.130] (**) Option "xkb_rules" "evdev"
[    45.130] (**) Option "xkb_model" "pc105"
[    45.130] (**) Option "xkb_layout" "us"
[    45.134] (II) config/udev: Adding input device HP Laser Gaming Mouse with VoodooDNA (/dev/input/event3)
[    45.134] (**) HP Laser Gaming Mouse with VoodooDNA: Applying InputClass "evdev pointer catchall"
[    45.134] (II) Using input driver 'evdev' for 'HP Laser Gaming Mouse with VoodooDNA'
[    45.134] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    45.134] (**) HP Laser Gaming Mouse with VoodooDNA: always reports core events
[    45.134] (**) HP Laser Gaming Mouse with VoodooDNA: Device: "/dev/input/event3"
[    45.170] (--) HP Laser Gaming Mouse with VoodooDNA: Found 9 mouse buttons
[    45.170] (--) HP Laser Gaming Mouse with VoodooDNA: Found scroll wheel(s)
[    45.170] (--) HP Laser Gaming Mouse with VoodooDNA: Found relative axes
[    45.170] (--) HP Laser Gaming Mouse with VoodooDNA: Found x and y relative axes
[    45.170] (II) HP Laser Gaming Mouse with VoodooDNA: Configuring as mouse
[    45.170] (II) HP Laser Gaming Mouse with VoodooDNA: Adding scrollwheel support
[    45.170] (**) HP Laser Gaming Mouse with VoodooDNA: YAxisMapping: buttons 4 and 5
[    45.170] (**) HP Laser Gaming Mouse with VoodooDNA: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    45.170] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input3/event3"
[    45.170] (II) XINPUT: Adding extended input device "HP Laser Gaming Mouse with VoodooDNA" (type: MOUSE)
[    45.170] (II) HP Laser Gaming Mouse with VoodooDNA: initialized for relative axes.
[    45.170] (**) HP Laser Gaming Mouse with VoodooDNA: (accel) keeping acceleration scheme 1
[    45.170] (**) HP Laser Gaming Mouse with VoodooDNA: (accel) acceleration profile 0
[    45.170] (**) HP Laser Gaming Mouse with VoodooDNA: (accel) acceleration factor: 2.000
[    45.170] (**) HP Laser Gaming Mouse with VoodooDNA: (accel) acceleration threshold: 4
[    45.170] (II) config/udev: Adding input device HP Laser Gaming Mouse with VoodooDNA (/dev/input/mouse0)
[    45.170] (II) No input driver/identifier specified (ignoring)
[    45.172] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event4)
[    45.172] (II) No input driver/identifier specified (ignoring)
[    45.174] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    45.174] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    45.174] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    45.174] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    45.174] (**) AT Translated Set 2 keyboard: always reports core events
[    45.174] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    45.201] (--) AT Translated Set 2 keyboard: Found keys
[    45.201] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    45.201] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    45.201] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    45.201] (**) Option "xkb_rules" "evdev"
[    45.201] (**) Option "xkb_model" "pc105"
[    45.201] (**) Option "xkb_layout" "us"

```

---

### Post by BicyclerBoy on 2011-06-25
I was under the impression that xinerama did not work properly with openGL/GLX..this not from any personal experience..

Xinerama seems to be heading for the history books..possiblly no bad thing.

Your log file tells you that composite is not supported with xinerama.

From my limited understanding & the nVidia driver readme states:
1. the primary X screen must be a nVidia GPU.
2. identical GPUs are recommended.
3. The intersection of capabilities across GPUs is only advertised.
4. If a GPU is incompatible with the rest of the xinerama desktop then no openGL on that screen.
5. OpenGL acceleration is disabled on non nvidia X server screens.
6. max screen 8Kx8K for 9800GT ?

1. You can check for 1. seems okay
2. is not happening but is not a show stopper.
3. may be ATI driver is the cause  
there is a DRI load failure for the ATI card.
4. as you said this is okay
5. ditto

---

### Post by WinstonChurchill on 2011-06-25
> **BicyclerBoy said:**
> I was under the impression that xinerama did not work properly with openGL/GLX..this not from any personal experience..
That I know isn't true - on this same card, I used to use Xinerama across two screens, and I had OpenGL working. I actually tried this setup without Xinerama, and GLX wouldn't load successfully there either. The addition of the ATI card is the issue, I think... although one would think there would be a solution to that.

> **BicyclerBoy said:**
> Xinerama seems to be heading for the history books..possiblly no bad thing.
Is there an alternative way to configure multiple screens in such a way that you can drag windows across them? I was under the impression Xinerama was the only way to do that.

---

### Post by BicyclerBoy on 2011-06-25
I'm guessing that a survey would reveal the Xinerama does not work well.
There is an old survey about twinview, xinerama etc & results are fairly damning.

I would guess that nVidia will stop/has stopped support/bug fixing xinerama because there are bigger problems looming on the horizon with Xorg changes & then Wayland..

Everyone uses Twinview to solve the window dragging.
Dynamic twinview is used by nVidia to solve the hot plugNplay problems with Xorg.
I just use separate X screens.

Your xinerama setup is including the ATI card-screen is it not ?

Your log file tells you that composite is not supported with xinerama in this configuration.
[44.304] (WW) NVIDIA(0): 32-bit ARGB GLX visuals are not currently supported with the 
[    44.304] (WW) NVIDIA(0):     Xinerama extension.
This error is to do with composite & possible screen depth less than 24 bit

nvidia 275 readme...
The Composite extension is currently incompatible with Xinerama, due to limitations in the X.Org X server. Composite will be automatically disabled when Xinerama is enabled.

You do have errors with DRI on ATI card.

The option ZapfodHeads is a ATI only keyword not Xorg or nVidia.

---

