---
title: "kubuntu - GeForce 6200 - TwinView Problem"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by krysyrk on 2007-01-15
Hi!

I have the following problem:
Got a GeForce 6200 gfx-card which has two outputs (DVI/CRT). Connected two monitors to it and configured xorg.conf to use twinview. But, when I start X, then I only get a picture on one Monitor - the second one stays blank! Strange thing is, that Xorg.0.log says, that both monitors were found! Nevertheless, it can't initialize the second one! Here is the messages I receive:

```

.....
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0, CRT-0"
(**) NVIDIA(0): Option "CursorShadow" "TRUE"
(**) NVIDIA(0): Option "CursorShadowAlpha" "64"
(**) NVIDIA(0): Option "CursorShadowXOffset" "2"
(**) NVIDIA(0): Option "CursorShadowYOffset" "2"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1600x1200, 1600x1200"
(**) NVIDIA(0): Option "NoTwinViewXineramaInfo" "True"
(**) NVIDIA(0): Option "HorizSync" "CRT-0: 31-81; DFP-0: 28-80"
(**) NVIDIA(0): Option "VertRefresh" "CRT-0: 56-75; DFP-0: 43-60"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Enabling cursor shadow
(**) NVIDIA(0): Cursor shadow alpha = 64
(**) NVIDIA(0): Cursor shadow offset = 2
(**) NVIDIA(0): Cursor shadow offset = 2
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP-0, CRT-0"
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.52
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     Maxdata (RogenTech) B101715 (CRT-0)
(--) NVIDIA(0):     Iiyama PLE511 (DFP-0)
(--) NVIDIA(0): Maxdata (RogenTech) B101715 (CRT-0): 400.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Iiyama PLE511 (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Iiyama PLE511 (DFP-0): Internal Single Link TMDS
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description "1600x1200"
(WW) NVIDIA(0): Not using mode description "1600x1200"; unable to map to
(WW) NVIDIA(0):     display device
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200,1600x1200"
......

```

And here is my xorg.conf file:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
#       Option          "DPMS"
    Identifier     "Iiyama ProLite H511S"
    VendorName     "Iiyama"
    ModelName      "ProLite H511S"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Device"

#       Option          "UseEDID"               "FALSE"
#       Option          "MetaModes"             "1600x1200, 1280x1024 @1600x1200; 1280x1024, 1280x1024; 1024x768, 1024x768"
#       Option          "MetaModes"             "1600x1200, 1280x1024; 1280x1024, 1280x1024; 1024x768, 1024x768"
#       Option          "SecondMonitorVertRefresh"      "56-75"
    Identifier     "NVIDIA GeForce 6200"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6200"
    Monitor        "Iiyama ProLite H511S"
    DefaultDepth    24
    Option         "NoLogo"
    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    Option         "UseDisplayDevice" "DFP-0"
    Option         "HorizSync" "CRT-0: 31-81; DFP-0: 28-80"
    Option         "VertRefresh" "CRT-0: 56-75; DFP-0: 43-60"
#       Option          "SecondMonitorHorizSync"        "31-81"
    Option         "TwinView" "True"
    Option         "NoTwinViewXineramaInfo" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
#    Option         "MetaModes" "1024x768, 1024x768"
    Option         "MetaModes" "1600x1200, 1600x1200"
        Option          "CursorShadow"          "TRUE"
        Option          "CursorShadowXOffset"   "2"
        Option          "CursorShadowYOffset"   "2"
        Option          "CursorShadowAlpha"     "64"

    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Can anyone figure out, what this is about...been playing with it since yesterday and are getting desperate....

Greetings,
krysyrk

PS: sorry for the "fuzz" in my xorg.conf file, but currently, it's a construction yard...;)

---

### Post by alibobar on 2007-08-10
I have the exact same problem!

[http://ubuntuforums.org/showthread.php?t=522066](http://ubuntuforums.org/showthread.php?t=522066)

---

