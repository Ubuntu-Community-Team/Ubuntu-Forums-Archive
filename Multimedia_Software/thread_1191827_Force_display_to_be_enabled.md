---
title: "Force display to be enabled?"
date: 2009-06-19
forum: Multimedia Software
---

### Post by jurgen24 on 2009-06-19
How do I force the display card to be enabled even if the 'monitor' is turned off? The only way I can get the display card to re-enable itself, is to turn on the 'monitor' and then logout (restart X).

I have a GeForce 8300 connected via HDMI to DENON-AVAMP. I have worked out how to lock in the resolution (by modifying xorg.conf); however when the amp is turned off the display is disabled. I can see the following diff in the Xorg.0.log files (the < is amp off, the > is amp on)

> <  (II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0
< (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
198,200c196,199
< (--) NVIDIA(0):     CRT-0
< (--) NVIDIA(0): CRT-0: 300.0 MHz maximum pixel clock
< (II) NVIDIA(0): Assigned Display Device: CRT-0
---
> (--) NVIDIA(0):     DON DENON-AVAMP (DFP-0)
> (--) NVIDIA(0): DON DENON-AVAMP (DFP-0): 165.0 MHz maximum pixel clock
> (--) NVIDIA(0): DON DENON-AVAMP (DFP-0): Internal Single Link TMDS
> (II) NVIDIA(0): Assigned Display Device: DFP-0xorg.conf

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DON DENON-AVAMP"
    HorizSync       15.0 - 68.0
    VertRefresh     23.0 - 61.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseEvents" "1"
    Option         "DPI" "100x100"
    Option         "NoLogo" "1"
EndSection
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8300"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSectionThanks!

---

### Post by ryscar on 2009-08-03
Were you ever able to find a solution for this?  I have been struggling with this problem for over a year and I still don't know a work around.

---

