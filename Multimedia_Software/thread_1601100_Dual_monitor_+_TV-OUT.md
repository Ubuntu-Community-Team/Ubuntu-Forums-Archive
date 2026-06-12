---
title: "Dual monitor + TV-OUT"
date: 2010-10-19
forum: Multimedia Software
---

### Post by theselby on 2010-10-19
Hi everyone.

I want to achieve something on a computer I have.

**First, the system specs**
1. Ubuntu 10.04 LTS - the Lucid Lynx
2. NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0) -- [http://www.nvidia.com/object/geforce_8500_tech_specs.html](http://www.nvidia.com/object/geforce_8500_tech_specs.html)
3. 2 LCDs and one TV

**Second, what I want to achieve, if possible**
I currently successfully run 2 displays in separate X screens and I work on both but I'd like to have the TV-our working too (if possible) to put some cartoons there for my kid so he'll watch them and I'll work "in peace" :)

If possible or not, please let me know... I desperately tried today for more than 3-4 hours already and no success yet :(

Here's my X config:
```
# nvidia-settings:  version 256.29  (buildd@promethium)  Sun May 30 23:58:57 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" LeftOf "Screen0"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load        "glx"
    Load        "dbe"   # Double buffer extension

EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ G2000W"
    HorizSync       31.0 - 83.0
    VertRefresh     55.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG W1941"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Television"
    VendorName     "Unknown"
    ModelName      "Unknown TV"
    HorizSync      30-50
    VertRefresh    50
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "TVOutFormat" "SVIDEO" 
    Option         "TVStandard" "PAL-B" 
#    Option        "TVOverScan" "1.0"
    Option         "ConnectedMonitor" "Television" 
    BusID          "PCI:1:0:0"
    Option         "IgnoreEDID" "True"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Television"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    DefaultDepth   24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    SubSection "Display"
        Depth      24
        Modes      "1024x768_60"
    EndSubSection
EndSection
```

This is the X log file, after restarting GDM:
```
root@mainserver:/home# cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux mainserver 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64
Kernel command line: root=UUID=9c888865-cbb9-435f-b54d-6368f1654283 ro quiet splash 
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 20 00:14:46 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Television"
(**) |   |-->Device "Device2"
(**) Option "DontZap" "False"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0421:1043:8256 nVidia Corporation G86 [GeForce 8500 GT] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Oct 20 00:14:46 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 20 00:14:46 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 20 00:14:46 NVIDIA(0):     enabled.
(II) Oct 20 00:14:47 NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Oct 20 00:14:47 NVIDIA(0): Memory: 524288 kBytes
(--) Oct 20 00:14:47 NVIDIA(0): VideoBIOS: 60.86.39.00.00
(II) Oct 20 00:14:47 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 20 00:14:47 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 20 00:14:47 NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) Oct 20 00:14:47 NVIDIA(0):     LG W2242 (CRT-0)
(--) Oct 20 00:14:47 NVIDIA(0):     LG W1941 (CRT-1)
(--) Oct 20 00:14:47 NVIDIA(0): LG W2242 (CRT-0): 400.0 MHz maximum pixel clock
(--) Oct 20 00:14:47 NVIDIA(0): LG W1941 (CRT-1): 400.0 MHz maximum pixel clock
(II) Oct 20 00:14:47 NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) Oct 20 00:14:47 NVIDIA(0): Assigned Display Device: CRT-0
(II) Oct 20 00:14:47 NVIDIA(0): Validated modes:
(II) Oct 20 00:14:47 NVIDIA(0):     "CRT-0:nvidia-auto-select+0+0"
(II) Oct 20 00:14:47 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Oct 20 00:14:47 NVIDIA(0): DPI set to (87, 83); computed from "UseEdidDpi" X config
(--) Oct 20 00:14:47 NVIDIA(0):     option
(==) Oct 20 00:14:47 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "CRT-1: 1360x768 +0+0"
(**) Oct 20 00:14:47 NVIDIA(1): Enabling RENDER acceleration
(II) Oct 20 00:14:47 NVIDIA(1): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Oct 20 00:14:47 NVIDIA(1): Memory: 524288 kBytes
(--) Oct 20 00:14:47 NVIDIA(1): VideoBIOS: 60.86.39.00.00
(II) Oct 20 00:14:47 NVIDIA(1): Detected PCI Express Link width: 16X
(--) Oct 20 00:14:47 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Oct 20 00:14:47 NVIDIA(1): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) Oct 20 00:14:47 NVIDIA(1):     LG W2242 (CRT-0)
(--) Oct 20 00:14:47 NVIDIA(1):     LG W1941 (CRT-1)
(--) Oct 20 00:14:47 NVIDIA(1): LG W2242 (CRT-0): 400.0 MHz maximum pixel clock
(--) Oct 20 00:14:47 NVIDIA(1): LG W1941 (CRT-1): 400.0 MHz maximum pixel clock
(II) Oct 20 00:14:47 NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
(II) Oct 20 00:14:47 NVIDIA(1): Assigned Display Device: CRT-1
(II) Oct 20 00:14:47 NVIDIA(1): Validated modes:
(II) Oct 20 00:14:47 NVIDIA(1):     "CRT-1:1360x768+0+0"
(II) Oct 20 00:14:47 NVIDIA(1): Virtual screen size determined to be 1360 x 768
(--) Oct 20 00:14:47 NVIDIA(1): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) Oct 20 00:14:47 NVIDIA(1):     option
(==) Oct 20 00:14:47 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "ConnectedMonitor" "TV"
(**) NVIDIA(2): Option "TVStandard" "PAL-B"
(**) NVIDIA(2): Option "TVOutFormat" "COMPOSITE"
(**) Oct 20 00:14:47 NVIDIA(2): Enabling RENDER acceleration
(**) Oct 20 00:14:47 NVIDIA(2): Forcing COMPOSITE video output
(**) Oct 20 00:14:47 NVIDIA(2): TV Standard string: "PAL-B"
(II) Oct 20 00:14:47 NVIDIA(2): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Oct 20 00:14:47 NVIDIA(2): Memory: 524288 kBytes
(--) Oct 20 00:14:47 NVIDIA(2): VideoBIOS: 60.86.39.00.00
(II) Oct 20 00:14:47 NVIDIA(2): Detected PCI Express Link width: 16X
(--) Oct 20 00:14:47 NVIDIA(2): Interlaced video modes are supported on this GPU
[COLOR=Red][B](--) Oct 20 00:14:47 NVIDIA(2): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) Oct 20 00:14:47 NVIDIA(2):     LG W2242 (CRT-0)
(--) Oct 20 00:14:47 NVIDIA(2):     LG W1941 (CRT-1)
(--) Oct 20 00:14:47 NVIDIA(2): LG W2242 (CRT-0): 400.0 MHz maximum pixel clock
(--) Oct 20 00:14:47 NVIDIA(2): LG W1941 (CRT-1): 400.0 MHz maximum pixel clock
(EE) Oct 20 00:14:47 NVIDIA(2): Unable to find available Display Devices for screen 2.
(EE) Oct 20 00:14:47 NVIDIA(2): No display devices found for this X screen.[/B][/COLOR]
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 20 00:14:47 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Oct 20 00:14:47 NVIDIA(0): Initialized GPU GART.
(II) Oct 20 00:14:47 NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Oct 20 00:14:47 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 20 00:14:47 NVIDIA(0): Initialized X Rendering Acceleration
[...stripped_off...]
```

---

### Post by 0bso on 2010-10-19
> **theselby said:**
> 
If possible or not, please let me know... 


Not possible. That video card (and just about every other I've ran across) can only use 2 of the outputs at a time. Easiest way to accomplish what you are trying is to add another video card with tv out.

---

### Post by theselby on 2010-10-20
> **0bso said:**
> Not possible. Easiest way to accomplish what you are trying is to add another video card with tv out.

Ok, thank you... I will go and purchase a second one :) haha... maybe another display soon too :D Thanks

---

### Post by P4man on 2010-10-20
You probably want another nvidia card then (and even then I dont promise anything). I just tried with an ATI and nVidia card to drive 2 independant screens (one for xbmc on tv, other for light gaming) , and after a LOT of tinkering I had it somewhat working but only with the opensource drivers for both. Installing restricted drivers for either nvidia or ati completely breaks xorg. Compiz is also a no go, even on the oss drivers.

I suspect 2 nvidia (or ati) cards would work, but havent tested that yet.

---

### Post by theselby on 2010-10-20
Hi.. ok, I bought another card... now a bit of help if you are kind, please... as I can't seem to succeed by myself.

So now I have:
 22" display and tv-out on old videoboard
 19" display on the new videoboard

my current Xorg.conf:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

# Settings: X configuration file generated by nvidia-settings

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "dbe"   # Double buffer extension
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"                                                                                                                                                                                                         
    Option         "Device" "/dev/psaux"                                                                                                                                                                                                     
    Option         "Emulate3Buttons" "no"                                                                                                                                                                                                    
    Option         "ZAxisMapping" "4 5"                                                                                                                                                                                                      
EndSection                                                                                                                                                                                                                                   
                                                                                                                                                                                                                                             
Section "Monitor"                                                                                                                                                                                                                            
    Identifier     "Monitor0"                                                                                                                                                                                                                
    VendorName     "Unknown"                                                                                                                                                                                                                 
    ModelName      "LG W2242"                                                                                                                                                                                                                
    HorizSync       30.0 - 83.0                                                                                                                                                                                                              
    VertRefresh     56.0 - 75.0                                                                                                                                                                                                              
    Option         "DPMS"                                                                                                                                                                                                                    
EndSection                                                                                                                                                                                                                                   
                                                                                                                                                                                                                                             
Section "Monitor"                                                                                                                                                                                                                            
    Identifier     "Monitor1"                                                                                                                                                                                                                
    VendorName     "Unknown"                                                                                                                                                                                                                 
    ModelName      "LG W1941"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    HorizSync       30.0 - 50.0
    VertRefresh     50.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
    BusID          "PCI:4:0:0"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-B"
    Option         "TVOverScan" "1.0"
    Option         "ConnectedMonitor" "CRT, TV"
    Option         "IgnoreEDID" "True"
    BusID          "PCI:1:0:0"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "TwinView" "0"
#    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_50"
    EndSubSection
EndSection

```



This is the LOG output:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux mainserver 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64
Kernel command line: root=UUID=9c888865-cbb9-435f-b54d-6368f1654283 ro quiet splash 
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 20 17:52:31 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "DontZap" "False"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0421:1043:8256 nVidia Corporation G86 [GeForce 8500 GT] rev 161, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI: (0:4:0:0) 10de:0a65:10de:066d nVidia Corporation GT218 [GeForce 210] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(EE) Screen 2 deleted because of no matching config section.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Oct 20 17:52:31 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 20 17:52:31 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 20 17:52:31 NVIDIA(0):     enabled.
(II) Oct 20 17:52:32 NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Oct 20 17:52:32 NVIDIA(0): Memory: 524288 kBytes
(--) Oct 20 17:52:32 NVIDIA(0): VideoBIOS: 60.86.39.00.00
(II) Oct 20 17:52:32 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 20 17:52:32 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 20 17:52:32 NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) Oct 20 17:52:32 NVIDIA(0):     LG W2242 (CRT-0)
(--) Oct 20 17:52:32 NVIDIA(0): LG W2242 (CRT-0): 400.0 MHz maximum pixel clock
(II) Oct 20 17:52:32 NVIDIA(0): Assigned Display Device: CRT-0
(II) Oct 20 17:52:32 NVIDIA(0): Validated modes:
(II) Oct 20 17:52:32 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Oct 20 17:52:32 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Oct 20 17:52:32 NVIDIA(0): DPI set to (87, 83); computed from "UseEdidDpi" X config
(--) Oct 20 17:52:32 NVIDIA(0):     option
(==) Oct 20 17:52:32 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
(**) Oct 20 17:52:32 NVIDIA(1): Enabling RENDER acceleration
(II) Oct 20 17:52:32 NVIDIA(1): NVIDIA GPU GeForce 210 (GT218) at PCI:4:0:0 (GPU-1)
(--) Oct 20 17:52:32 NVIDIA(1): Memory: 1048576 kBytes
(--) Oct 20 17:52:32 NVIDIA(1): VideoBIOS: 70.18.2c.00.04
(II) Oct 20 17:52:32 NVIDIA(1): Detected PCI Express Link width: 4X
(--) Oct 20 17:52:32 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Oct 20 17:52:32 NVIDIA(1): Connected display device(s) on GeForce 210 at PCI:4:0:0:
(--) Oct 20 17:52:32 NVIDIA(1):     LG W1941 (CRT-0)
(--) Oct 20 17:52:32 NVIDIA(1): LG W1941 (CRT-0): 400.0 MHz maximum pixel clock
(II) Oct 20 17:52:32 NVIDIA(1): Assigned Display Device: CRT-0
(II) Oct 20 17:52:32 NVIDIA(1): Validated modes:
(II) Oct 20 17:52:32 NVIDIA(1):     "nvidia-auto-select+0+0"
(II) Oct 20 17:52:32 NVIDIA(1): Virtual screen size determined to be 1360 x 768
(--) Oct 20 17:52:32 NVIDIA(1): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) Oct 20 17:52:32 NVIDIA(1):     option
(==) Oct 20 17:52:32 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 20 17:52:32 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Oct 20 17:52:32 NVIDIA(0): Initialized GPU GART.
(II) Oct 20 17:52:32 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Oct 20 17:52:32 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 20 17:52:32 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Oct 20 17:52:32 NVIDIA(1): Initialized GPU GART.
(II) Oct 20 17:52:32 NVIDIA(1): Setting mode "nvidia-auto-select+0+0"
(II) Oct 20 17:52:32 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Oct 20 17:52:32 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0


```


Thanks. Any help would be kindly appreciated.

---

### Post by P4man on 2010-10-21
Not that Im a xorg expert, but your xorg seems wrong to me. YOu have 3 devices for the videocards, you "only" have 2 cards. That 8500 is in there twice, which I think is incorrect. Try removing one entry for it and then fix the mapping with the screens.

---

### Post by theselby on 2010-10-21
Hi,

New news from my side.

1. ALL monitors and the TV are detected (2 LCDs and the TV)
2. The 3rd X screen gets "prepared" as I can move the mouse "in" it but nothing displayed on the TV.

Can any expert take a look into this and let me know if I can fix something?


Ok, here are the config and the logs:

```
root@mainserver:~# cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux mainserver 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64
Kernel command line: root=UUID=9c888865-cbb9-435f-b54d-6368f1654283 ro quiet splash 
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 21 23:28:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "DontZap" "False"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:                                                                                                                                                                                                                        
        /usr/share/fonts/X11/misc,                                                                                                                                                                                                           
        /usr/share/fonts/X11/100dpi/:unscaled,                                                                                                                                                                                               
        /usr/share/fonts/X11/75dpi/:unscaled,                                                                                                                                                                                                
        /usr/share/fonts/X11/Type1,                                                                                                                                                                                                          
        /usr/share/fonts/X11/100dpi,                                                                                                                                                                                                         
        /usr/share/fonts/X11/75dpi,                                                                                                                                                                                                          
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,                                                                                                                                                                                    
        built-ins                                                                                                                                                                                                                            
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"                                                                                                                                                                   
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.                                                                                                                                              
(WW) Disabling Keyboard0                                                                                                                                                                                                                     
(WW) Disabling Mouse0                                                                                                                                                                                                                        
(II) Loader magic: 0x7ca300                                                                                                                                                                                                                  
(II) Module ABI versions:                                                                                                                                                                                                                    
        X.Org ANSI C Emulation: 0.4                                                                                                                                                                                                          
        X.Org Video Driver: 6.0                                                                                                                                                                                                              
        X.Org XInput driver : 7.0                                                                                                                                                                                                            
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0421:1043:8256 nVidia Corporation G86 [GeForce 8500 GT] rev 161, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI: (0:4:0:0) 10de:0a65:10de:066d nVidia Corporation GT218 [GeForce 210] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "crt,tv"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Oct 21 23:28:05 NVIDIA(0): Enabling RENDER acceleration
(**) Oct 21 23:28:05 NVIDIA(0): ConnectedMonitor string: "crt,tv"
(II) Oct 21 23:28:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 21 23:28:05 NVIDIA(0):     enabled.
(II) Oct 21 23:28:06 NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Oct 21 23:28:06 NVIDIA(0): Memory: 524288 kBytes
(--) Oct 21 23:28:06 NVIDIA(0): VideoBIOS: 60.86.39.00.00
(II) Oct 21 23:28:06 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 21 23:28:06 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 21 23:28:06 NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) Oct 21 23:28:06 NVIDIA(0):     LG W2242 (CRT-0)
(--) Oct 21 23:28:06 NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) Oct 21 23:28:06 NVIDIA(0): LG W2242 (CRT-0): 400.0 MHz maximum pixel clock
(--) Oct 21 23:28:06 NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) Oct 21 23:28:06 NVIDIA(0): TV encoder: NVIDIA
(II) Oct 21 23:28:06 NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) Oct 21 23:28:06 NVIDIA(0): Assigned Display Device: CRT-0
(II) Oct 21 23:28:06 NVIDIA(0): Validated modes:
(II) Oct 21 23:28:06 NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
(II) Oct 21 23:28:06 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Oct 21 23:28:06 NVIDIA(0): DPI set to (87, 83); computed from "UseEdidDpi" X config
(--) Oct 21 23:28:06 NVIDIA(0):     option
(==) Oct 21 23:28:06 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
(**) NVIDIA(1): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Oct 21 23:28:06 NVIDIA(1): Enabling RENDER acceleration
(II) Oct 21 23:28:06 NVIDIA(1): NVIDIA GPU GeForce 210 (GT218) at PCI:4:0:0 (GPU-1)
(--) Oct 21 23:28:06 NVIDIA(1): Memory: 1048576 kBytes
(--) Oct 21 23:28:06 NVIDIA(1): VideoBIOS: 70.18.2c.00.04
(II) Oct 21 23:28:06 NVIDIA(1): Detected PCI Express Link width: 4X
(--) Oct 21 23:28:06 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Oct 21 23:28:06 NVIDIA(1): Connected display device(s) on GeForce 210 at PCI:4:0:0:
(--) Oct 21 23:28:06 NVIDIA(1):     LG W1941 (CRT-0)
(--) Oct 21 23:28:06 NVIDIA(1): LG W1941 (CRT-0): 400.0 MHz maximum pixel clock
(II) Oct 21 23:28:06 NVIDIA(1): Assigned Display Device: CRT-0
(II) Oct 21 23:28:06 NVIDIA(1): Validated modes:
(II) Oct 21 23:28:06 NVIDIA(1):     "nvidia-auto-select+0+0"
(II) Oct 21 23:28:06 NVIDIA(1): Virtual screen size determined to be 1360 x 768
(--) Oct 21 23:28:06 NVIDIA(1): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) Oct 21 23:28:06 NVIDIA(1):     option
(==) Oct 21 23:28:06 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "ConnectedMonitor" "tv"
(**) NVIDIA(2): Option "TVStandard" "PAL-B"
(**) NVIDIA(2): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(2): Option "TwinView" "0"
(**) NVIDIA(2): Option "MetaModes" "TV: nvidia-auto-select +0+0"
(**) NVIDIA(2): Option "TVOverScan" "1.0"
(**) Oct 21 23:28:06 NVIDIA(2): Enabling RENDER acceleration
(**) Oct 21 23:28:06 NVIDIA(2): Forcing SVIDEO output
(**) Oct 21 23:28:06 NVIDIA(2): TV Standard string: "PAL-B"
(II) Oct 21 23:28:06 NVIDIA(2): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Oct 21 23:28:06 NVIDIA(2): Memory: 524288 kBytes
(--) Oct 21 23:28:06 NVIDIA(2): VideoBIOS: 60.86.39.00.00
(II) Oct 21 23:28:06 NVIDIA(2): Detected PCI Express Link width: 16X
(--) Oct 21 23:28:06 NVIDIA(2): Interlaced video modes are supported on this GPU
(--) Oct 21 23:28:06 NVIDIA(2): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) Oct 21 23:28:06 NVIDIA(2):     LG W2242 (CRT-0)
(--) Oct 21 23:28:06 NVIDIA(2):     NVIDIA TV Encoder (TV-0)
(--) Oct 21 23:28:06 NVIDIA(2): LG W2242 (CRT-0): 400.0 MHz maximum pixel clock
(--) Oct 21 23:28:06 NVIDIA(2): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) Oct 21 23:28:06 NVIDIA(2): TV encoder: NVIDIA
(II) Oct 21 23:28:06 NVIDIA(2): Display Device found referenced in MetaMode: TV-0
(II) Oct 21 23:28:06 NVIDIA(2): Assigned Display Device: TV-0
(II) Oct 21 23:28:06 NVIDIA(2): Validated modes:
(II) Oct 21 23:28:06 NVIDIA(2):     "TV:nvidia-auto-select+0+0"
(II) Oct 21 23:28:06 NVIDIA(2): Virtual screen size determined to be 1024 x 768
(==) Oct 21 23:28:06 NVIDIA(2): DPI set to (75, 75); computed from built-in default
(==) Oct 21 23:28:06 NVIDIA(2): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 21 23:28:06 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Oct 21 23:28:06 NVIDIA(0): Initialized GPU GART.
(II) Oct 21 23:28:06 NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Oct 21 23:28:06 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 21 23:28:06 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Oct 21 23:28:06 NVIDIA(1): Initialized GPU GART.
(II) Oct 21 23:28:06 NVIDIA(1): Setting mode "nvidia-auto-select+0+0"
(II) Oct 21 23:28:06 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Oct 21 23:28:06 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Oct 21 23:28:06 NVIDIA(2): Initialized GPU GART.
(II) Oct 21 23:28:06 NVIDIA(2): Setting mode "TV:nvidia-auto-select+0+0"
(II) Oct 21 23:28:06 NVIDIA(2): Initialized OpenGL Acceleration
(==) NVIDIA(2): Disabling shared memory pixmaps
(II) Oct 21 23:28:06 NVIDIA(2): Initialized X Rendering Acceleration
(==) NVIDIA(2): Backing store disabled
(==) NVIDIA(2): Silken mouse enabled
(==) NVIDIA(2): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
(**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Genius Optical Mouse: always reports core events
(**) Genius Optical Mouse: Device: "/dev/input/event4"
(II) Genius Optical Mouse: Found 3 mouse buttons
(II) Genius Optical Mouse: Found scroll wheel(s)
(II) Genius Optical Mouse: Found relative axes
(II) Genius Optical Mouse: Found x and y relative axes
(II) Genius Optical Mouse: Configuring as mouse
(**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
(II) Genius Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
root@mainserver:~# 
```

```
# XOrg configuration

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2242"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG W1941"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "ConnectedMonitor" "crt,tv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
    BusID          "PCI:4:0:0"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "ConnectedMonitor" "tv"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-B"
    Option         "TVOverScan" "1.0"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```



@P4man - actually it seems that 3 devices are required... I've tried only with 2 and no success :) I know that at some point you had right, but the devices represent actually the output connector and not the videoboard itself.


Thanks for your support!

---

### Post by theselby on 2010-10-24
Hi... any new advices here? Please?

---

