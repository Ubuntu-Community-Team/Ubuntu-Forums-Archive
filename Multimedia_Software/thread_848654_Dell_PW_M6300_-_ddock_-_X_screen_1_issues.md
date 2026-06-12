---
title: "Dell PW M6300 - d/dock - X screen 1 issues"
date: 2008-07-03
forum: Multimedia Software
---

### Post by blacdard on 2008-07-03
I have two configurations on my Dell laptop (Precision Workstation M6300):

1) Docked on D/Dock, w/DVI-2 and CRT-0 interface flat panels @ 1280x1024.
2) Undocked, w/DVI-0 LCD @ 1920x1200.

I have to manually toggle the screen assignments in the ServerLayout section between

Screen 0 "Screen0"
Screen 1 "Screen1"

and

Screen 1 "Screen0"
Screen 0 "Screen1"

when I dock/undock else I get two issues, but ONLY ON SCREEN 1:

1) menus are really slow unless I run "compiz --only-current-screen &"  I'm not sure how to automate this, as "compiz --display :0.1 &" didn't seem to solve the slowness.
2) When using screen 1 The mouse cursor disappears when it touches the right or bottom edges of the screen.  It never comes back.  I was using Alt-Ctrl-Backspace ALL the time before I gave up and just started editing the xorg.conf file every time I switched.
3) If the LCD is screen 1, then the resolution is forced to 1280x1024.


Any ideas?  Here's my xorg.conf:

> Section "Module"
    Load           "glx"
EndSection

#Section "ServerFlags"
#    Option         "Xinerama" "0"
#EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Default Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Default LCD Panel"
    HorizSync       30.0 - 81.0
    VertRefresh     60.0 - 75.0
    modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1600M"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024"
    Option         "UseDisplayDevice" "CRT-0, DFP-2"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1600M"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "UseDisplayDevice" "DFP-0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"

    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView"
    Subsection "Display"
        Depth      24
        Modes          "1280x1024"
    EndSubsection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Subsection "Display"
        Depth      24
        Modes          "1920x1200"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         0 "Screen0"
    Screen         1 "Screen1"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection


---

