---
title: "Missing resolution, unkown monitor on 10.04 [ddcprobe/xorg"
date: 2010-09-29
forum: Multimedia Software
---

### Post by idhw on 2010-09-29
Hey,

I've spent most of the day trying to figure out why in the world the ubuntu 10.04 installation on our IBM Thinkcentre 8109-71G doesn't seem to want to detect the samsung monitor and present us with the proper screen resolutions. 

I've tried all sorts of things like generating an xorg and editing it, doing a dpkg-reconfigure xserver-xorg (which doesn't even seem to do anything at all in 10.04 and only asks me some keyboard questions on an old 9.04 livecd) fiddling about with xrandr, etc. Nothing so far has worked beside getting forcing xrandr to go into my desired resolution (1680x1050) by adding the mode and using it on my VGA1 output. This however, does not fix the whole "monitor is unknown" issue. 

This is driving me absolutely bonkers...

Anyway, here is some data I imagine you guys will need:

```
idhw@CLIIDH95:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  

```xorg:

```

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
    Load  "glx"
    Load  "record"
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
Identifier "Monitor0"
VendorName "Samsung"
ModelName "Samsung"
HorizSync 30.0 - 120.0
VertRefresh 55.0 - 75.0
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
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
    BoardName   "82915G/GV/910GL Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth 24
        Modes "1680x1050" "1024x768"
    EndSubSection

```ddcprobe:

```

root@CLIIDH95:/home/idhw# ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)915G/915GV/910GL Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)915G/915GV/910GL Graphics Controller Hardware Version 0.0
memory: 7872kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail
```
Any help would be greatly appreciated.

Thanks,

Dean Vaessen.

---

### Post by idhw on 2010-10-04
*bump*

---

### Post by idhw on 2010-10-06
Anyone at all?

---

