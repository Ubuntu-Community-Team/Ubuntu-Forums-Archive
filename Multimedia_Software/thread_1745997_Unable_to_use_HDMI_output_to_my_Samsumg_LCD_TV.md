---
title: "Unable to use HDMI output to my Samsumg LCD TV"
date: 2011-05-01
forum: Multimedia Software
---

### Post by fsallstrom on 2011-05-01
Hi
I am unable to use HDMI output to my Samsung LE40 F7 LCD TV.  I am using Ubuntu 11.04 on an Asus eeebox pc EB1012 (Nvidia EON2 video chipset). When connecting through the VGA interface I get full 1080 resolution on my LCD TV but I thought that I'd rather use HDMI since both the TV and the PC support HDMI.

I have installed the proprietary Nvidia driver through System->Administration->additional drivers
```

fredrik@Burken:~$ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)
```Now I am connecting a 19-inch LG monitor though the VGA input and the Samsung LCD TV through the HDMI input but even though the nvidia control panel seems to detect both of them (after many attempts and a few reboots), the LCD TV does not detect any signal what so ever. I know my LCD TV is a bit sensitive to the input signal, but it works just fine through VGA. I have enabled the samsung LCD in the nvidia control panel and have tried both twinview and separate x-window settings but none works. 

Here is my Xorg.log:

```
fredrik@Burken:~$ less /var/log/Xorg.0.log | grep NVIDIA
[    19.245] (II) Module glx: vendor="NVIDIA Corporation"
[    19.275] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    19.672] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.704] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    19.898] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.137] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    20.137] (==) NVIDIA(0): RGB weight 888
[    20.137] (==) NVIDIA(0): Default visual is TrueColor
[    20.137] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.137] (**) NVIDIA(0): Option "TwinView" "0"
[    20.138] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0; CRT: 1280x1024_75 +0+0"
[    20.138] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    21.339] (II) NVIDIA(GPU-0): Display (LG Electronics L1980Q (CRT-0)) does not support
[    21.339] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    21.373] (II) NVIDIA(GPU-0): Display (SAMSUNG LCD (DFP-0)) does not support NVIDIA 3D
[    21.373] (II) NVIDIA(GPU-0):     Vision stereo.
[    21.381] (II) NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:2:0:0 (GPU-0)
[    21.381] (--) NVIDIA(0): Memory: 524288 kBytes
[    21.381] (--) NVIDIA(0): VideoBIOS: 70.18.5a.00.11
[    21.381] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[    21.381] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.381] (--) NVIDIA(0): Connected display device(s) on ION at PCI:2:0:0
[    21.381] (--) NVIDIA(0):     LG Electronics L1980Q (CRT-0)
[    21.381] (--) NVIDIA(0):     SAMSUNG LCD (DFP-0)
[    21.381] (--) NVIDIA(0): LG Electronics L1980Q (CRT-0): 400.0 MHz maximum pixel clock
[    21.382] (--) NVIDIA(0): SAMSUNG LCD (DFP-0): 165.0 MHz maximum pixel clock
[    21.382] (--) NVIDIA(0): SAMSUNG LCD (DFP-0): Internal Single Link TMDS
[    21.383] (II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
[    21.412] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    21.412] (II) NVIDIA(0): Validated modes:
[    21.412] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
[    21.412] (II) NVIDIA(0):     "CRT:1280x1024_75+0+0"
[    21.413] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    21.443] (--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
[    21.443] (--) NVIDIA(0):     option
[    21.443] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    21.443] (==) NVIDIA(1): RGB weight 888
[    21.443] (==) NVIDIA(1): Default visual is TrueColor
[    21.443] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    21.444] (**) NVIDIA(1): Option "TwinView" "0"
[    21.444] (**) NVIDIA(1): Option "MetaModes" "DFP: nvidia-auto-select +0+0"
[    21.444] (II) NVIDIA(1): NVIDIA GPU ION (GT218) at PCI:2:0:0 (GPU-0)
[    21.444] (--) NVIDIA(1): Memory: 524288 kBytes
[    21.444] (--) NVIDIA(1): VideoBIOS: 70.18.5a.00.11
[    21.444] (II) NVIDIA(1): Detected PCI Express Link width: 1X
[    21.444] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    21.444] (--) NVIDIA(1): Connected display device(s) on ION at PCI:2:0:0
[    21.444] (--) NVIDIA(1):     LG Electronics L1980Q (CRT-0)
[    21.444] (--) NVIDIA(1):     SAMSUNG LCD (DFP-0)
[    21.444] (--) NVIDIA(1): LG Electronics L1980Q (CRT-0): 400.0 MHz maximum pixel clock
[    21.444] (--) NVIDIA(1): SAMSUNG LCD (DFP-0): 165.0 MHz maximum pixel clock
[    21.444] (--) NVIDIA(1): SAMSUNG LCD (DFP-0): Internal Single Link TMDS
[    21.446] (II) NVIDIA(1): Display Device found referenced in MetaMode: DFP-0
[    21.587] (II) NVIDIA(1): Assigned Display Device: DFP-0
[    21.587] (II) NVIDIA(1): Validated modes:
[    21.587] (II) NVIDIA(1):     "DFP:nvidia-auto-select+0+0"
[    21.587] (II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
[    21.603] (--) NVIDIA(1): DPI set to (304, 304); computed from "UseEdidDpi" X config
[    21.603] (--) NVIDIA(1):     option
[    21.603] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    21.612] (II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
[    21.768] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.768] (==) NVIDIA(0): Backing store disabled
[    21.768] (==) NVIDIA(0): Silken mouse enabled
[    21.769] (**) NVIDIA(0): DPMS enabled
[    21.771] (II) NVIDIA(0): [DRI2] Setup complete
[    21.779] (II) NVIDIA(1): Setting mode "DFP:nvidia-auto-select+0+0"
[    22.069] (==) NVIDIA(1): Disabling shared memory pixmaps
[    22.069] (==) NVIDIA(1): Backing store disabled
[    22.069] (==) NVIDIA(1): Silken mouse enabled
[    22.069] (==) NVIDIA(1): DPMS enabled
[    22.072] (II) NVIDIA(1): [DRI2] Setup complete
```and my xorg.conf:
```

fredrik@Burken:~$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@roseapple)  Fri Feb 25 14:43:24 UTC 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

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
    ModelName      "LG Electronics L1980Q"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SAMSUNG LCD"
    HorizSync       15.0 - 68.0
    VertRefresh     49.0 - 61.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "1920x1080_60 +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: 1280x1024_75 +0+0, DFP: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "1280x1024_75 +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0; 1280x1024_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0; CRT: 1280x1024_75 +0+0"
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
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```Perhaps I need to manually edit a modeline settings for my TV, I don't know if it is capable of presnting a valid edid setting. I have previously used the following modeline for it:
```

Modeline  "1920x1080@60" 138.5 1920 1960 1995 2083 1080 1082 1087 1109 +hsync -vsync 
```That I entered through xrandr but I don't know how to put that into the xorg.conf file. I don't want to mess around with manual xrandr settings, I rather use the nvidia control panel. 


I really appreciate your help. 

//Fredrik

---

