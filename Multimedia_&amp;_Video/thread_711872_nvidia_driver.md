---
title: "nvidia driver?"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by hsnz on 2008-03-01
My graphic is NVIDIA GeForce FX 5200
My monitor is LG FLATRON 775FT

I have installed nvidia driver:

```

logout
ctl-alt-f1
login
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg2.run
sudo /etc/init.d/gdm start

```

afer install my xorg.config file was this:

```

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
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
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce FX (generic)"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce FX (generic)"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1400 1050
        Depth       24
        Modes      "800x600@85" "800x600@60" "800x600@75" "832x624@75" "800x600@72" "1024x768@85" "800x600@56" "1024x768@75" "640x480@85" "1024x768@70" "640x480@75" "1024x768@60" "640x480@72" "1024x768@43" "640x480@60" "1152x864@75" "1280x960@60" "1280x1024@60" "1400x1050@60"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

```

after restarting X a message box said "Lo graphics Mode - Your graphics adapter not recognized".
What was wrong and what must I do?

---

### Post by sanddgroper on 2008-03-01
Hi
The driver you loaded looks a bit old.
I to have the FX5200 card and for every version of Ubuntu from 6.06lts to now
I use the nvidia glx driver from the miscellaneous -graphical(restricted) package
in synaptic and have had no problem with it .

Cheers
Sandy

---

