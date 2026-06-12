---
title: "GLX on ATI Rage XL and Nvidia GeForce 6600 GT Tri Head"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by a2b2 on 2007-01-07
I've just done a fresh install of Edgy in an attempt to get GLX to work (and maybe later xgl later) across my tri head setup. The current hardware is

AMD 4200x2 (only 1 core online ATM as I've not recompiled the kernel yet)
Onboard ATI Rage XL (4Mb I think) on a Rev 1 Tyan S2865 (meaning no way to disable the onboard video)
PCI Express nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) using the restricted drivers.

rghf@liquidfusion:~$ uname -a 
Linux liquidfusion 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

I've got a xinerama display working using the following xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Right Screen" 0 0
    Screen      1  "Left Screen" RightOf "Middle Screen"
    Screen      2  "Middle Screen" RightOf "Right Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "Xinerama" "On"
    Option         "Clone" "off"
EndSection

Section "Files"

    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "Auto"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
   Option "Buttons" "5"
EndSection
EndSection

Section "Monitor"
    Identifier     "hp f1703"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA 2"
    Driver         "nvidia"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "NVIDIA 1"
    Driver         "nvidia"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "ATI"
    Driver         "ati"
    BusID          "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier     "Right Screen"
    Device         "ATI"
    Monitor        "hp f1723"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Middle Screen"
    Device         "NVIDIA 2"
    Monitor        "hp f1723"
    DefaultDepth    24
    Option         "TwinView"
    Option         "TwinViewOrientation" "RightOf"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Left Screen"
    Device         "NVIDIA 1"
    Monitor        "hp f1703"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" 
    EndSubSection
EndSection

Section "Extensions"
          Option  "Composite" "Disable"

          Option  "AllowGLXWithComposite" "Enable"
EndSection


```

If I run with just the NVidia heads glxgears / glxinfo works. However when I bring the ATI head online 

```

$ glxinfo 
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault (core dumped)

```

Any ideas where to start on this one? I've read through loads of stuff but got no where quick

---

