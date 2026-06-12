---
title: "Dual monitors with onboard + s3 gfx"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by zipf on 2007-12-11
Hi all,

I'm having issues with running dual monitors in Gutsy.

```
lspci | grep -i vga
00:0f.0 VGA compatible controller: S3 Inc. 86c968 [Vision 968 VRAM] rev 0
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```

xorg.conf
```
Section "device"
        Identifier      "card1"
        Boardname       "SiS 650"
        Busid           "PCI:1:0:0"
        Driver          "sis"
        Screen
        Vendorname      "SiS"
EndSection

Section "Device"
        Identifier      "card2"
        Boardname       "vesa"
        Busid           "PCI:0:15:0"
        Driver          "vesa"
        Screen
EndSection

Section "Monitor"
        Identifier      "monitor1"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 940T/940B/940Fn(Digital)"
        Horizsync       30-81
        Vertrefresh     56-75
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "card1"
        Monitor         "monitor1"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@75"   "1280x960@60"  "1400x1050@60"   "1280x1024@75"  "1600x1200@65"  "1152x864@75"   "1600x1200@60" "1024x768@60"    "1024x768@70"   "1024x768@75"   "832x624@75"    "800x600@60"   "800x600@75"     "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"   "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  	Screen "screen1"
  	Screen "screen2" rightof "screen1"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection

Section "screen"
        Identifier      "screen2"
        Device          "card2"
        Defaultdepth    24
        Monitor         "monitor2"
        SubSection "Display"
                Depth   24
                Modes           "1024x768@60"   "1152x864@75"   "1024x768@70"  "1280x1024@75"   "1024x768@75"   "1280x960@60"   "832x624@75"    "1280x1024@60" "800x600@60"     "1280x960@75"   "800x600@75"    "1400x1050@60"  "800x600@72"   "1400x1050@75"   "800x600@56"    "1600x1200@65"  "640x480@75"    "1600x1200@60" "640x480@72"     "640x480@60"
        EndSubSection
EndSection

Section "monitor"
        Identifier      "monitor2"
        Vendorname      "Philips"
        Modelname       "Philips 170C5 (17inch)"
        Horizsync       30.0-82.0
        Vertrefresh     56.0-76.0
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "false"
EndSection
```

The only outcome of moving my mouse to the secondary screen is a thick line at the top of the primary screen which changes as the mouse moves on the secondary screen. The only output I can get across to the secondary monitor is if in Gnome I go to Administration > Screens and Graphics > Test, but this clones the desktop of the Samsung screen, and I still have the same mouse problem. 

I've read through numerous threads, wikis and other random articles, but nothing seems to have worked.

Any suggestions?

---

