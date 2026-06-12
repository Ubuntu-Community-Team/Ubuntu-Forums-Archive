---
title: "How do I enable my HDTV as a separate xscreen?"
date: 2008-05-29
forum: Multimedia Software
---

### Post by MdaG on 2008-05-29
As the title says. I just made a clean install of Kubuntu 8.04 and this worked in Ubuntu 7.10, but not any longer (I basically copy pasted my *xorg.conf* from my previous install). What differs between Ubuntu 7.10 and Kubuntu 8.04 ?

I get a picture on both my TV and monitor during startup, but as soon as KDM kicks in it's just a blank screen on the TV.

This is my *xorg.conf*:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
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
    Option         "XkbLayout" "se"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L204WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
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
    ModeLine       "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "OEM 37'' TFT-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
    DisplaySize     819.6 461
    Gamma           1
    #Option          "NoEdidMaxPClkCheck"
    #Option	    "NoMaxPClkCheck"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    BusID          "PCI:0:5:0"
    Screen          0

EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    Option         "ConnectedMonitor" "DFP"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "nvidia-auto-select +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
    Virtual     1920 1080
    Depth       24
    Modes	   "1920x1080_60" "1280x720_60" "720x480_60"
    EndSubSection
EndSection

```

---

### Post by MdaG on 2008-05-31
Finally made some progress by simply using the default xorg.conf and adding the screen via nvidia-settings. It's not satisfactory yet as the image is only partly visible on my screen. Most of it is there but I can move the pointer slightly outside of view.

Is there any way to force the TV to draw the image "in view"?

My new xorg.conf looks like this:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L204WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "OEM 37'' TFT-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1920x1080 +0+0"
EndSection
```

---

### Post by buntu_hugenewbie11 on 2009-01-24
I am trying to set up a separate xscreen to just a connected monitor.
Using nvidia settings it seems that the best I can do is twin view.
If I understand the function of separate xscreen I should be able to have a separate working desktop on one monitor.
I seem to not be able to set this up with nvidia settings.
What should I copy from the above xorg file to get it working?
Any direction with this would be helpful.

---

### Post by buntu_hugenewbie11 on 2009-01-24
Ok I seem to have gotten a separate xscreen working.
This is what I did:
- logged in as root and copied xorg.conf file to home directory or somewhere safe. (just in case stuff goes wrong.)
-logged out as root
-ran sudo nvidia-settings
-change your nvidia settings as you feel (see this for help: ([http://weblogs.java.net/blog/bleonard/archive/2008/05/opensolaris_200.html](http://weblogs.java.net/blog/bleonard/archive/2008/05/opensolaris_200.html))
-then apply what you can
-save changes to xorg
then hit crtl-alt-backspace to restart Xserver
(I am using kde 3.5 and kubuntu Hardy)
Hope this helps.
Now if only I can get full screen working with flash on one display and be able to keep working on the other monitor then my weekend at work will be substantially improved.

---

