---
title: "Intel onboard + ATI r128"
date: 2009-11-22
forum: Multimedia Software
---

### Post by macanudo on 2009-11-22
Im running Ubuntu 9.10 (karmic) and I have an Intel DG33TLM motherboard, which has VGA+DVI out.. and an old ATI all in wonder card with rage 128. I want to use 3 monitors (which I can in windows with this setup) but Im hitting a snag. Im able to get the 2 Intel displays going, or the ATI display, but not all 3. If I change the BIOS setting for the default video, thats how I can switch between ATI and intel displays. 

Heres the lspci output:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
06:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG
```

In System->Preferences->Display Im only seeing the 2 displays..

Any thoughts? Help!

---

### Post by macanudo on 2009-11-22
Im totally new to this.. but I generated an xorg.conf file if this helps anyone to help me..

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    Load  "dri"
    Load  "glx"
    Load  "record"
    Load  "dbe"
    Load  "dri2"
    Load  "extmod"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
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
    VendorName  "Intel Corporation"
    BoardName   "82G33/G31 Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "ForcePCIMode"           # [<bool>]
        #Option     "CCEPIOMode"             # [<bool>]
        #Option     "CCENoSecurity"          # [<bool>]
        #Option     "CCEusecTimeout"         # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "Display"                # <str>
        #Option     "PanelWidth"             # <i>
        #Option     "PanelHeight"            # <i>
        #Option     "ProgramFPRegs"          # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "ShowCache"              # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
    Identifier  "Card1"
    Driver      "r128"
    VendorName  "ATI Technologies Inc"
    BoardName   "Rage 128 RE/SG"
    BusID       "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by macanudo on 2009-11-23
Well no replies but I sorta solved my problem.. I had a GeForce 9500GS card in another system not being used, so I pulled it and went a bought a cheap GeForce 6200 card. Both have DVI+VGA out so Ive got 4 displays working. Now I just need to figure out how to get them all in the same X session and Ill be good to go.

---

