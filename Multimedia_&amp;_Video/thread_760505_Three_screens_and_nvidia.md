---
title: "Three screens and nvidia"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by J4nus on 2008-04-20
Dear,

I have an Asus M2NPV-VM motherboard with a GeForce 6150 built-in.
I added a new card in pci-e, another GeForce 8800 GT 512 MB.

As you can see below, both cards are known by the system.

janus@cobra:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
janus@cobra:~$


My goal is to use 3 screens.
Two screens connected to the GeForce 8800 (both 20', 1680x1050) and one screen connected to the GeForce 6150 (via VGA HPL1520e 1024x768).


I tried a lot of possibilities but nothing works.


Here is my configuration file:


> 
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0"
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "Xinerama" "true"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Generic Keyboard"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2016W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 86.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:3:0:0"
    Option         "RandRRotation" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    BusID          "PCI:0:5:0"
    Option         "RandRRotation" "true"
EndSection


Section "Screen"
# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: 1680x1050 +1680+0, DFP: 1680x1050 +0+0; CRT: 1600x1024 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 1024x768 +1280+0, DFP: nvidia-auto-select +0+0"
EndSection

Section "Screen"
# Removed Option "metamodes" "640x480 +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
#    Option         "TwinView" "0"
#    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection






The error message:

> (II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-1
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1680x1050+1680+0,DFP:1680x1050+0+0"
(II) NVIDIA(0):     "CRT:1600x1024+1280+0,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0):     "CRT:1024x768+1280+0,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 3360 x 1050
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "RandRRotation" "true"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(GPU-1): No display devices connected; falling back to: CRT-0
(WW) NVIDIA(GPU-1): Unable to read EDID for display device CRT-0
(II) NVIDIA(1): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-1)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.51.22.33.07
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(1):     CRT-0
(--) NVIDIA(1): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(1): Assigned Display Device: CRT-0
(WW) NVIDIA(1): No valid modes for "1024x768"; removing.
(WW) NVIDIA(1): No valid modes for "832x624"; removing.
(WW) NVIDIA(1): No valid modes for "800x600"; removing.
(WW) NVIDIA(1): No valid modes for "720x400"; removing.
(EE) NVIDIA(1): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(1):     MetaMode "640x480" is not supported on this GPU.
(WW) NVIDIA(1):
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1):
(EE) NVIDIA(1): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(1):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(1):     GPU.
(EE) NVIDIA(1): Unable to use default mode "nvidia-auto-select".
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"



When I try to use xrandr:
janus@cobra:~/xorg_config$ xrandr
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing
janus@cobra:~/xorg_config$


Thanks a lot for your feedback!

---

### Post by toaster.waffle on 2008-05-13
I have the same motherboard, and an nVidia 7900 GS.  I'm trying to get an LCD monitor on the 7900GS and a TV on the onboard video out (composite, but eventually s-video).

I get a similar error:

> (II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.33.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(0):     GPU.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(0):     GPU.
(EE) NVIDIA(0): Unable to use default mode "nvidia-auto-select".



Is this a failed attempt to auto-configure the modes for the TV given there are none set in my xorg.conf?

---

