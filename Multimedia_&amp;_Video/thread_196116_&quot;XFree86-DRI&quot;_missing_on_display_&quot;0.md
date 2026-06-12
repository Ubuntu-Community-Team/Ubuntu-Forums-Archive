---
title: "&quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by xolot1 on 2006-06-13
i have a new hp dv8210us with an ati radeon xpress 200m

i installed fglrx, but after restarting i get:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

heres some info i thought might be helpful:
from etc/x11/xorg.conf
```
Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

```

```
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver      "ati"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection
Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1440x900"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1440x900"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1440x900"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1440x900"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1440x900"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1440x900"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
  EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

any suggestions?
what other info may help?

thanks

---

