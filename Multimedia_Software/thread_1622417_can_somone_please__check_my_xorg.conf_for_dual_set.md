---
title: "can somone please  check my xorg.conf for dual setup.."
date: 2010-11-15
forum: Multimedia Software
---

### Post by olifu02 on 2010-11-15
So im trying to set up to my HannG monitor and this is whats in my xorg.conf right.  When i reboot with this it just gets hung up on the black screen before login, im not sure whats wrong.  Also, im not sure how to put my graphics card in the xorg.conf.  According to lspci it is 

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Here is my xorg.conf

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
    Load  "record"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "LCD"
    VendorName   "Hanns-G"
    ModelName    "HH251"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "LCD"
    Device     "Intel Corporation Mobile 4 Series Chipset                 Integrated Graphics Controller (rev 07)"
    Monitor    "LCD"
    DefaultDepth 24
    SubSection "Display"
        Depth     1
        Modes "1920x1080" "1680x1050" "1280x800"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes "1920x1080" "1680x1050" "1280x800"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes "1920x1080" "1680x1050" "1280x800"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes "1920x1080" "1680x1050" "1280x800"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes "1920x1080" "1680x1050" "1280x800"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes "1920x1080" "1680x1050" "1280x800"
    EndSubSection
EndSection

---

