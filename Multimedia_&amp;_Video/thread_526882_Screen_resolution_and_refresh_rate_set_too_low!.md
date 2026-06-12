---
title: "Screen resolution and refresh rate set too low!"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by Good Ol' Ramos on 2007-08-16
I assume that it's also in 24-bit color versus the desired 32-bit. I've tried changing things in xorg.conf, I've tried uninstalling and reinstalling the video driver... I'm at wit's end here. What's going on?

---

### Post by alterpinguin on 2007-08-16
you may need to read a bit more, there are graphics-cards setting their own way to use the plugged in monitor. For example there is the option:
Option          "IgnoreEDID" "True"
Option          "UseEdidFreqs" "false"
to be set in the xorg.conf (Device Section of the graphics device) to make X11 ignore some of those graphics-card-suggestions. But, like told, you have to read a bit more to make up your mind if the graphics-card should have better options. You may need to put a list of mode lines in if you want to override the defaults of the graphics card. 

here is one thats usable for me -- keep in mind, it works for me and my hardware!!:
part of xorg.conf:
......
.......
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option          "UseEdidDpi" "false"
        Option          "UseEdidFreqs" "false"
        Option          "IgnoreEDID" "True"
#       Option          "ExactModeTimingsDVI" "True"
        Option          "DPI" "100x100"
EndSection

Section "Monitor"
        Identifier      "Standardbildschirm"
        VendorName      "--> VESA"
        ModelName       "1280X1024@60HZ"
        Option          "DPMS"
#       Option          "TargetRefresh" "60"
        UseModes        "Modes[0]"
#       Horizsync       28-51
        Horizsync       28-64
#       Vertrefresh     43-60
        Vertrefresh     58-62
        DisplaySize     380 300
#       DisplaySize     336 269
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline      "1280x1024" 105.15 1280 1360 1496 1712 1024 1025 1028 1059
  Modeline      "1280x960" 97.68 1280 1352 1488 1696 960 961 964 993
  Modeline      "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
  Modeline      "1152x864" 78.82 1152 1216 1336 1520 864 865 868 894
  Modeline      "1280x768" 77.37 1280 1344 1480 1680 768 769 772 794
  Modeline      "1024x768" 61.89 1024 1080 1184 1344 768 769 772 794
  Modeline      "800x600" 36.88 800 832 912 1024 600 601 604 621
  Modeline      "768x576" 33.74 768 792 872 976 576 577 580 596
  Modeline      "640x480" 23.06 640 656 720 800 480 481 484 497
  Modeline      "1280x1024" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync
 +vsync
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600]"
        Monitor         "Standardbildschirm"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024" "1024x768"  "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024" "1024x768"  "800x600"       "640x480"
        EndSubSection
EndSection

......
.......

---

### Post by Good Ol' Ramos on 2007-08-16
Alright, so I guess the question is, then, why does this happen? What screws up in Ubuntu that forces me to have to manually set the resolutions and refresh rates?

---

