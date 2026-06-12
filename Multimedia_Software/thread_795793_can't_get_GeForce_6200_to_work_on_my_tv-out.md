---
title: "can't get GeForce 6200 to work on my tv-out"
date: 2008-05-15
forum: Multimedia Software
---

### Post by buddhabadboy on 2008-05-15
Hello all,
I thought I'd try and see if anyone here can help.
I've had it working on and off: but that was based on a simple monitor, and my HD TV as an extended.

But now that i try just to run my 52" HDTV on the Nvidia 6200, via the DVI, it doesn't work properly. I can get it to work in safe mode, but that's about it. I tried tweaks, etc.  Can anyone make a suggestion?
----------------------
Section "ServerLayout"
    Identifier     "Layout0"
    Screen 1  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NV44A [GeForce 6200]"
    #BoardName      "GeForce 6200"
    BusID          "PCI:1:0:0"
    Screen 0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NV44A [GeForce 6200]"
    BusID          "PCI:1:0:0"
    Screen 1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdidFreqs" "false"
    Option         "ConnectedMonitor" "TV"
    Option         "TvOutFormat" "Component"
    Option         "TVStandard" "HD1080i"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TVStandard" "NTSC"
    #Option        "ModeValidation" "NoDFPNativeResolutionCheck, NoEdidModes, NoMaxPClkCheck"
    #Option        "ModeValidation" "AllowNon60HzDFPModes, NoVesaModes, NoXServerModes, NoPredefinedModes"
    #Option         "metamodes" "DFP: 1920x1080 +0+0"
    #Option "ExactModeTimingsDVI" "true"
    #Option "ModeValidation" "NoEdidMaxPClkCheck,NoDFPNativeResolutionCheck"
    #Option "UseEDIDDpi" "FALSE"
    Option         "metamodes" "DFP: 1920x1080_60i +0+0; DFP: 1920x1080 @1920x1080 +0+0; DFP: 1024x768 +0+0; DFP: 720X480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes       "1920x1080_60i" "1920x1080" "1920x540" "1024x768" "720X480"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HITACHI PTV"
    HorizSync       15.0 - 620.0
    VertRefresh     15.0 - 600.0
    #Modeline "1920x540" 74.250 1920 2008 2052 2200 540 542 547 562 +hsync +vsync
    Modeline "1920x1080" 74.2 1920 2008 2056 2200 1080 1084 1094 1124 +hsync +vsync interlace
    Option         "DPMS"
EndSection

---

