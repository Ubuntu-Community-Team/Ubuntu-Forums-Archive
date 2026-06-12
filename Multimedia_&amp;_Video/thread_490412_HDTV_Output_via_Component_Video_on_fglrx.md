---
title: "HDTV Output via Component Video on fglrx"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by block1of4 on 2007-07-02
I have a Radeon 9500 Pro and am trying to get tv-out to work w/ fglrx. I am using the component video dongle to connect it to an Toshiba LCD TV w/ 1280x720 native resolution. 

The screen comes out black & white at 1024x768. I think it could be a problem w/ EDID detection (the 1280x720 resolution isn't being reported). The IgnoreEDID option is ignored for some reason on X bootup.

Here's the relevant sections in my xorg.conf:
```
Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
        Driver          "fglrx"
        Option          "NoTV"          "no"
        Option          "TVFormat"      "NTSC-M"
        Option          "TVStandard"    "VIDEO"
        Option          "DesktopSetup"  "clone mode"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "IgnoreEDID"    "true"
        Option          "UseEdidFreqs"  "false"
        Option          "NoDDC"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Toshiba"
        Modelname       "27HL95"
        Option          "DPMS"
        Horizsync       15-46
        Vertrefresh     59-61
        Modeline        "1280x720p60" 74.48 1280 1336 1472 1664 720 721 724 746 -HSync +Vsync
        Option          "IgnoreEDID"    "true"
        Option          "UseEdidFreqs"  "false"
        Option          "NoDDC"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
        Monitor         "Toshiba"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth           24
                Modes           "1280x720p60"
        EndSubSection
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


```


The xorg log file is reporting EDID data for the monitor, but it only reports 640x480, 800x600, and 1024x768. It's native resolution isn't listed (1280x720). Can I get X to ignore the EDID or DDC data?

I've tried doing this w/ a VGA connection, also, and I can get color but only at 1152x864, which the TV can't handle.

---

### Post by block1of4 on 2007-07-02
anyone? can i force the resolution and/or ignore edid/ddc? in the log it says that those options are ignored.

---

### Post by block1of4 on 2007-07-03
bueller?

---

