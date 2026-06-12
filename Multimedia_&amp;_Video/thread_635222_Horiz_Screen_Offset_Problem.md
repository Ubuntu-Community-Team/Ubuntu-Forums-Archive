---
title: "Horiz Screen Offset Problem"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by jbinc1 on 2007-12-08
Hello,

I can't seem to get my screen to stay in correct horiz position after a reboot. I've tried the method I've seen posted using xvidtune and after editing xorg.config to add a Modeline as suggested, my screen returns to the same offset position it was in before the reboot. Here is a copy of my xorg.config file.

```
Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "SyncMaster"
    Option        "DPMS"Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "SyncMaster"
    Option        "DPMS"
    Modeline "1280x1024"   108.00   1280 1348 1460 1688   1024 1025 1028 1066 +hsync +vsync 
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection
    Modeline "1280x1024"   108.00   1280 1348 1460 1688   1024 1025 1028 1066 +hsync +vsync 
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection
```If anyone can see I'm doing something wrong or has any input, I would really appreciate it. Thanks in advance.

---

