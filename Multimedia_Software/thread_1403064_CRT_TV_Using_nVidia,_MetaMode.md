---
title: "CRT TV Using nVidia, MetaMode?"
date: 2010-02-09
forum: Multimedia Software
---

### Post by Epidural on 2010-02-09
I'm a total noobie with this stuff, like to get that out right off the bat. I have an old-ish television (32" CRT, nothing special) with only component inputs. Currently, I'm using an nVidia 9800GT running 2 "Seperate X Window" displays (both LCD computer moniters). I'm trying to get my TV set up in much the same way, but would be happy with any configuration (Twin/Seperate). Whenever I go to apply the TwinView setting to the TV in nVidia's controlpanel, it tells me:
> Failed to set MetaMode (1) 'TV-0: nvidia-auto-select @1024x768 +1680+0, DFP-0: nvidia-auto-select @1680x1050 +0+0' (Mode 2704x1050, id: 50) on X screen 0.
If I set it to Seperate X Screen, it logs out of Ubuntu and resumes my original settings (I have not saved to X Configuration file for either trial, simple hit apply).

The TV is plugged into composite via an adapter from S-Video to composite video. Here is my xorg.conf:
> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1024 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
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
    ModelName      "Acer X223W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL1511"
    HorizSync       30.0 - 63.0
    VertRefresh     55.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:8:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:8:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: 1024x768_75 +0+0; CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1024x768_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Help would be greatly appreciated, or even a grim diagnoses: something that lets me end my struggles.

---

