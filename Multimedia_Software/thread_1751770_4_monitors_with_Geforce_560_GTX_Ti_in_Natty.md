---
title: "4 monitors with Geforce 560 GTX Ti in Natty"
date: 2011-05-07
forum: Multimedia Software
---

### Post by Despot on 2011-05-07
Hi y'all, 

Wanted to share my experiences getting 4 monitors on my working with a fresh installation of Natty with a Geforce 560 GTX Ti from MSI, in the hopes that it'd be helpful to somebody out there. The secondary card is an old 9500 GT I had lying about.

I was unable to configure more than two monitors using the FOSS [FONT="Courier New"]nouveau[/FONT] driver (although I applaud their efforts--two monitors worked quite well). The 560 family of cards isn't supported by the version of the [FONT="Courier New"]nvidia[/FONT] driver that shipped with Natty, so I had to use the 270 series of drivers available in the [X Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

The Unity interface didn't seem to be happy with multiple monitors, so I disabled it (select the Classic Gnome session at the login screen). The compositing effects did not play nicely with Xinerama (there's a warning related to this in Xorg.log if you have both Xinerama and compositing enabled), so I disabled compositing in xorg.conf, and selected the Classic Gnome (No Effects) session in the login manager.

Finally, in my case there are special considerations because the nvidia driver thinks the EDID from one of my monitors is corrupt, so I have to override the auto-detected resolution.

Below is the working xorg.conf file. Note the mixed use of absolute and relative positioning; this was necessary to achieve the layout I wanted. Relative positioning switched the positions of some screens.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 3200 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" 1280 0 
    Screen      3  "Screen3" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HannStar Display Corp Hanns.G HG281"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1920x1200_60.00" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Westinghouse Digital Electronics WDE LCM-17w7"
    HorizSync       30.0 - 61.0
    VertRefresh     55.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560 Ti"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560 Ti"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Device"

    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"

    Identifier     "Device3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "IgnoreEDIDChecksum" "DFP-0"
    Option         "ExactModeTimingsDVI" "TRUE"
    Option         "ModeValidation" "NoDFPNativeResolutionCheck"
    Option         "TwinView" "0"
    #Option         "metamodes" "DFP-2: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
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
    #Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Device3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

---

### Post by TuxLyn on 2011-05-15
Using Xinerama without compositing enabled is not fun. It's so annoying that I would rather use older version of linux just because of it.

---

