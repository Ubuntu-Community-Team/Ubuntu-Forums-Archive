---
title: "Ubuntu 7.10 (Gutsy Gibbon) + ATI Radeon X1300 + WXGA Monitor: Resolution 1280x800??"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by bs.venkatesh on 2007-12-06
Dear Friends,

I searched a lot but was unsuccessful in finding a solution for my problem. Problem is:
Config:
- OS: Ubuntu 7.10 (Gutsy Gibbon) 
- Video Card: ATI Radeon X1300 
- Monitor:  WXGA Monitor

I have set resolution to 1280x800@60 Hz but it is NOT actually looking like that. It looks better in Windows under the same resolution. 


**/etc/X11/xorg.conf**
```

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/encodings"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"

    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection


Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules"  "xorg"
    Option      "XkbModel"  "pc105"
    Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "CorePointer"
    Option      "Device"        "/dev/input/mice"
    Option      "Protocol"      "ImPS/2"
    Option      "ZAxisMapping"      "4 5"
    Option      "Emulate3Buttons"   "true"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"        "/dev/psaux"
    Option      "Protocol"      "auto-dev"
    Option      "HorizScrollDelta"  "0"
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "stylus"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "stylus"
    Option      "ForceDevice"   "ISDV4"     # Tablet PC ONLY
EndSection

Section "InputDevice"Section "InputDevice"
    Driver      "wacom"
    Identifier  "cursor"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "cursor"
    Option      "ForceDevice"   "ISDV4"     # Tablet PC ONLY
EndSection

Section "Device"
    Identifier  "Generic Video Card"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Extensions"
    Option      "Composite" "0"
    #Option     "Composite" "disable"
EndSection

Section "Monitor"
    Identifier  "Generic Monitor"
    Option      "DPMS"
    HorizSync   31.5-94Section "Screen"
    Identifier  "Default Screen"
    Device      "Generic Video Card"
    Monitor     "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth       1
        Modes       "1280x800" "1280x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       4
        Modes       "1280x800" "1280x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       8
        Modes       "1280x800" "1280x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       15
        Modes       "1280x800" "1280x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       16
        Modes       "1280x800" "1280x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       24
        Modes       "1280x800" "1280x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "Default Screen"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

    VertRefresh 50-90
    ModeLine    "1280×800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

    Driver      "wacom"
    Identifier  "eraser"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "eraser"
    Option      "ForceDevice"   "ISDV4"     # Tablet PC ONLY
EndSection

```

**fglrxinfo**
```

vbs@inspiron-e1505:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6473 (8.37.6)
vbs@inspiron-e1505:~$ 

```

Thanks for your time!

best,
Venkatesh.

---

### Post by eilu on 2007-12-11
this may be of help: [http://ubuntuforums.org/showthread.php?t=517506](http://ubuntuforums.org/showthread.php?t=517506)

---

### Post by bs.venkatesh on 2008-01-03
Hi Eilu,

Thanks for the reply but the thread you mentioned is for video card with intel chip set. I have an ATI (manufactured by AMD) video card. :(

---

