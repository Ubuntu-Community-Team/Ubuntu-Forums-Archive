---
title: "enable widescreen with hp2009m and nvidia 5200"
date: 2009-11-09
forum: Multimedia Software
---

### Post by chumley1970 on 2009-11-09
hi,

i am trying to get my new monitor to be in widescreen mode, 1600 x 900. i have tried playing around in xorg.conf and adding in the 1600x900 in the "screen" and "modes" section, but thats not working for me. the nvidia x server settings program from 'system->preferences->display still only go up to 1280x960. also, the xorg.conf file says my monitor is a sylvania generic crt display. here is a snippet from xorg.conf. i edited the horz and vsync for my hp monitor and added in the 1600x900@75, otherwise it is unmolested:

----------------------- snip --------------

Section "Device"
    Identifier    "nVidia Corporation NV34 [GeForce FX 5200]"
    Boardname    "NVIDIA GeForce FX (generic)"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
    Vendorname    "NVIDIA"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Sylvania"
    Vendorname    "Generic CRT Display"
    Modelname    "Monitor 1024x768"
    Horizsync    24-85
    Vertrefresh    48-76
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sylvania"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    960
        Modes    "1600x900@75"    "1024x768@60"    "1280x960@60"    "1024x768@70"    "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

------------------------- snip ---------------------

thanks for any help

---

