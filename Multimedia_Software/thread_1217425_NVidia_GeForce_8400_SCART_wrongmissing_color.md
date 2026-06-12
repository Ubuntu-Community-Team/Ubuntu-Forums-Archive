---
title: "NVidia GeForce 8400 SCART wrong/missing color"
date: 2009-07-19
forum: Multimedia Software
---

### Post by petzler on 2009-07-19
Hi,

I'm using the GeForce 8400 with a SVIDEO to SCART Cable Adapter with the following xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen @HD160XT+" 0 0
    Screen      1  "Screen @SDTV" 800 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "DontZap" "False"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "HD160XT+ Monitor"
    VendorName     "HAI"
    ModelName      "HAI SG7"
    HorizSync       31.0 - 60.0
    VertRefresh     60.0
    DisplaySize     150 90 # mm 
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "SDTV"
    VendorName     "Generic"
    ModelName      "TV-0"
    HorizSync       31.0 - 60.0
    VertRefresh     60.0
    DisplaySize     290 220 # mm 
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "NoLogo"                "True"
    Option         "RenderAccel"           "True"
    Option         "UseEvents"             "True"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "NoLogo"                "True"
    Option         "RenderAccel"           "True"
    Option         "UseEvents"             "True"
    # see ch. 16 /usr/share/doc/nvidia-glx-180/README.txt.gz
    Option         "TVOutFormat"           "SCART"
    Option         "TVStandard"            "PAL-B"
    Option         "UseDisplayDevice"      "TV"
EndSection

Section "Screen"
    Identifier     "Screen @HD160XT+"
    Device         "Device0"
    Monitor        "HD160XT+ Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    #Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    Option         "metamodes" "CRT: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen @SDTV"
    Device         "Device1"
    Monitor        "SDTV"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    Option         "UseEDID" "False"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The TV device is a SDTV CRT. I do have colors, even with TVOutFormat=SCART,SVIDEO,COMPOSITE. But I miss the blue color. The brilliance of the color is missing therefore. Using nvidia-seetings doesn't change to color to the right. As reference I'm using the GIF from [http://www.mythtv.org/wiki/Image:Testimage.gif](http://www.mythtv.org/wiki/Image:Testimage.gif). The cable length is about 2 meter, should be OK.

What can I do to check e.g. the settings, hardware to get the colors right?

Some informations:

$ uname -a
Linux tux64 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

Thanks,
Olaf

---

### Post by petzler on 2009-07-21
no ideas?

---

