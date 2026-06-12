---
title: "Sluggish UI on one display with dual displays"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by Daelin on 2007-11-19
I recently started using Ubuntu as a result of my severe dislike of Vista. I've made the foray into Linux lands a few times before, but was never successful at making it a permanent thing.  This time, however, I've fallen in love with Ubuntu and have even forgone the dualboot with windows and am running just Ubuntu on my Dell XPS m1710.

So here's the problem, I have everything working for the most part.  I have the NVIDIA drivers for my GeForce GO 7900GS installed via Envy and have the fancy desktop cube going and all the fun stuff.  I even have WoW working in wine.  I just today decided to try dual displays as I was doing with Vista before I switched.  I have the dual displays working, and had some trouble with window decorations being missing on the 2nd display but that is solved now.  The primary display (the LCD on the laptop itself) its UI is very sluggish, the UI on the 2nd LCD is fine.  It's weird.  Now effects like wobbly windows and desktop cube and all that are just fine, no lag at all.  When I click on UI elements like right clicking the panel, or clicking "System" or right clicking the desktop, etc. it will pause about a second before opening, then when I mouse over an item with a submenu that will take a second to open too.  It only happens on the primary monitor.

I've looked for topics in google and on here for the past few hours to no avail.  If there's already a topic I missed on this I'd be more than happy to read that.

Here's my xorg.conf as it seems the thing to do:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1920x1200"
    HorizSync       31.5 - 74.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7900 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7900 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1920x1200@60" "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

	#  
    Identifier     "screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1280x1024 +0+0"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0; 1680x1050@60 +0+0; 1600x1024@60 +0+0; 1440x900@60 +0+0; 1280x800@60 +0+0; 1280x720@60 +0+0; 1280x768@60 +0+0; 800x600@60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1920x1200 +0+0; DFP-0: 1680x1050@60 +0+0; DFP-0: 1600x1024@60 +0+0; DFP-0: 1440x900@60 +0+0; DFP-0: 1280x800@60 +0+0; DFP-0: 1280x720@60 +0+0; DFP-0: 1280x768@60 +0+0; DFP-0: 800x600@60 +0+0"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Thanks in advance for any help.

---

### Post by fireandlight27 on 2008-03-05
Any luck with this?  I'm having the exact same problem.

---

### Post by Daelin on 2008-03-05
None, I ended up giving up as I got used to just flipping around the desktop cube on one screen.  I guess no one has any idea what it is.

---

