---
title: "1080i output through dvi-hdmi cable"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Phoenix7000 on 2009-12-07
Hey Everyone,

I've been looking around here a bit and trying to find a solution with no success so far, so I thought I'd open it up to greater minds.

I've just installed 9.10 on a machine with a Radeon 9200.  I'm using the open source ati driver, and I'm trying to set up my monitor to be a Philips 30PW9100D/37B, which supports 480P and 1080i.  480P is enabled in the set by default, and in the monitor settings dialouge I can choose 1920x540, which I'm assuming is the 1080i as 540 should be the pre-interlaced number of pixels.  However, if I switch to this setting the screen acts as though it is not getting an input, and displays nothing.  I've managed to pull the EDID settings off of a windows box if that's helpful for everyone, so here they are:

```
Monitor
  Model name............... L05HD
  Manufacturer............. Philips
  Plug and Play ID......... PHL5057
  Serial number............ 1
  Manufacture date......... 2005, ISO week 1
  -------------------------
  EDID revision............ 1.3
  Input signal type........ Digital
  Color bit depth.......... Undefined
  Display type............. RGB color
  Screen size.............. 590 x 340 mm (26.8 in)
  Power management......... Not supported
  Extension blocs.......... 1 (Reserved - 0x00)
  -------------------------
  DDC/CI................... Not supported

Color characteristics
  Default color space...... Non-sRGB
  Display gamma............ 2.20
  Red chromaticity......... Rx 0.625 - Ry 0.340
  Green chromaticity....... Gx 0.280 - Gy 0.595
  Blue chromaticity........ Bx 0.155 - By 0.070
  White point (default).... Wx 0.283 - Wy 0.298
  Additional descriptors... None

Timing characteristics
  Horizontal scan range.... 15-46kHz
  Vertical scan range...... 59-61Hz
  Video bandwidth.......... 80MHz
  CVT standard............. Not supported
  GTF standard............. Not supported
  Additional descriptors... None
  Preferred timing......... Yes
  Native/preferred timing.. 1920x1080i at 60Hz 
    Modeline............... "1920x1080" 74.250 1920 2008 2052 2200 1080 1084 1094 1124 interlace +hsync +vsync
  Detailed timing #1....... 720x480p at 60Hz 

    Modeline............... "720x480" 27.000 720 736 798 858 480 489 495 525 -hsync -vsync

Standard timings supported
     640 x  480p at  60Hz - IBM VGA

Report information
  Date generated........... 12/7/2009
  Software revision........ 2.42.0.820
  Operating system......... 6.1.7600.2

Raw data
  00,FF,FF,FF,FF,FF,FF,00,41,0C,57,50,01,00,00,00,01,0F,01,03,80,3B,22,78,0A,0D,C9,A0,57,47,98,27,
  12,48,4C,20,00,00,01,01,01,01,01,01,01,01,01,01,01,01,01,01,01,01,01,1D,80,18,71,1C,16,20,58,2C,
  25,00,49,4F,21,00,00,9E,8C,0A,D0,8A,20,E0,2D,10,10,3E,96,00,49,4F,21,00,00,18,00,00,00,FC,00,4C,
  30,35,48,44,0A,20,20,20,20,20,20,20,00,00,00,FD,00,3B,3D,0F,2E,08,00,0A,20,20,20,20,20,20,01,F2

```Here's my xorg.conf, some things are commented out because either because there was no effect, or they interfered with me using an lcd monitor in the meantime.

```
Section "Monitor"
    Identifier   "Configured Monitor"
    #    HorizSync 15-46
    #    VertRefresh 59-61
    #    ModeLine "1920x1080" 74.250 1920 2008 2052 2200 1080 1084 1094 1124 interlace +hsync +vsync
    #    ModeLine "720x480" 27.000 720 736 798 858 480 489 495 525 -hsync -vsync
EndSection

Section "Screen"
    Identifier     "Monitor"
    Device         "Radeon 9200"
    Monitor        "Configured Monitor"
    #    DefaultDepth 16
    #    SubSection "Display"
    #        Depth 24
    #        Modes "1920x1080"
    #        Modes "720x480"
    #    EndSubSection
    SubSection "Display"
        Virtual    2320 1050
    EndSubSection
EndSection

Section "Device"
    Driver        "ati"
    Identifier  "Radeon 9200"
    Option "BusType" "PCI"
    Option "AccelMethod" "EXA"
    Option "MigrationHeuristic" "greedy"
    Option "AGPSize" "64"
    Option "TVStandard" "1080i"
EndSection
```I've tried setting the modelines in my xorg.conf, but it hasn't had any effect as far as I can tell.  If anyone's got any ideas, I'd love to hear them!

---

