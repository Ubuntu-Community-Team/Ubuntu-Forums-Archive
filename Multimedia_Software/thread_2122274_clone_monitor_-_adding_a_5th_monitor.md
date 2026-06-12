---
title: "clone monitor - adding a 5th monitor"
date: 2013-03-04
forum: Multimedia Software
---

### Post by phoen1x on 2013-03-04
Hi,

i recently set up a new system with 4 Monitors (identical benq gw2750) and 2 video cards (identical Radeon HD 6450). After reading some manuals and toying around for some time the 4 Monitors happily do their work on the 4 DVI Ports.

The real fun starts with the 5th monitor which I want in "clone" mode. It has to show exactly the same screen, as one of the 4 benq gw2750, because it is a TV and it is normally switched off.

According to manual the xorg.conf the Section "ServerLayout" can do** RightOf, LeftOf, Above, Below, Relative** but no "clone"??? 

Can somebody please point me to a manual or add to my xorg.conf to show me how it is done?

**Cool fact:** If I boot up the system into Ubuntu and then connect the TV. My TV will "clone" Screen0 or Screen2 according to which video card I plug it into.
**Sad fact:** If I forget to turn of the TV before rebooting. The TV will become Screen1 or Screen3 and two benq gw2750 will "clone" each other.

**Driver**:
```

Name: fglrx
Version: 9.1.11
Date: Dec 19 2012
Desc: AMD FireGL DRM kernel module

```

**/etc/X11/xorg.conf**
```

####################################################################################
# Layout - How Screens are presented
#
# To DEBUG: assign all Screens with LeftOf 
# ----> Mouse will start at Screen 0. Moving left will show screen 1,2,...,n
#       yellow Post-it's on monitors / cables help in RL too. ;-)
#
####################################################################################

Section "ServerLayout"
    Identifier "Layout0"
    Screen 0 "Screen0" 0 0
    Screen 1 "Screen1" LeftOf  "Screen0"
    Screen 2 "Screen2" LeftOf  "Screen1"
    Screen 3 "Screen3" Above   "Screen2"
    Option "Xinerama" "1"
EndSection


####################################################################################
# Monitors - Available Monitor Hardware
####################################################################################

Section "Monitor"
    Identifier    "Monitor0"
    Option        "Primary" "true"
    Option        "VendorName" "Benq"
    Option        "ModelName" "BenqGW2750"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Option        "VendorName" "Benq"
    Option        "ModelName" "BenqGW2750"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier    "Monitor2"
    Option        "VendorName" "Benq"
    Option        "ModelName" "BenqGW2750"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier    "Monitor3"
    Option        "VendorName" "Benq"
    Option        "ModelName" "BenqGW2750"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


####################################################################################
# Devices - Mapping garphics card "BusID" to "Identifier" / "virtual device"
#
# bash commands
# -------------   
# to determine BusID:  lscpi | grep VGA
####################################################################################

Section "Device"
    Identifier "Device0"
    Driver "fglrx"
    VendorName "ATI"
    BoardName "Radeon HD 6450"
    BusID "PCI:1:0:0"
    Screen 0
EndSection

Section "Device"
    Identifier "Device1"
    Driver "fglrx"
    VendorName "ATI"
    BoardName "Radeon HD 6450"
    BusID "PCI:1:0:0"
    Screen 1
EndSection

Section "Device"
    Identifier "Device2"
    Driver "fglrx"
    VendorName "ATI"
    BoardName "Radeon HD 6450"
    BusID "PCI:2:0:0"
    Screen 0
EndSection

Section "Device"
    Identifier "Device3"
    Driver "fglrx"
    VendorName "ATI"
    BoardName "Radeon HD 6450"
    BusID "PCI:2:0:0"
    Screen 1
EndSection


####################################################################################
# Screen definition for Layout
####################################################################################


Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "Device1"
    Monitor "Monitor1"
    DefaultDepth 24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device "Device2"
    Monitor "Monitor2"
    DefaultDepth 24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device "Device3"
    Monitor "Monitor3"
    DefaultDepth 24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

```

Thanks for your help,
PhOeniX

---

