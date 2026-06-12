---
title: "Xinerama Settings problem dual-screen nvidia"
date: 2008-07-21
forum: Multimedia Software
---

### Post by skatedawe on 2008-07-21
Hi.

I got this new 19" LCD, Samsung 19" SyncMaster 913v (Left, the one with the config problem) with BENQ FP937s.
Im doing the dual screen in Xinerama mode.
The two screens are working on 1280x1024.
Geforce FX 5200 PCI 128mb Ram.

**From from nvidia-settings:**
Dimension: 2560x1024 pixels (764x302 millimeters)
Resolution: 85x86 dots per inch
Nvidia Driver Version: 169.12

And i straight to the problem:

The left screen are ~20-25pixels leftout (the "screen image" starts after 20pixels) in horizon from left to right, so the image on the mouseover-screen-dragging is the leftout problem, there is a piece missing  on the left screen thats not displaying ok, because the screen starting a little to the right (from left).


This has to be edited manually i think, i've been having most luck with that.
I shouldn't be that hard to figure out the problem.

Here is the xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    Screen      1  "screen1" RightOf "Default Screen"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "true"
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
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
#   ModeLine       "1024x768"  65.0   1024 1048 1184 1344  768  771  777  806 -hsync -vsync
    Modeline       "1280x1024" 65.0   1280 1328 1512 1712 1024 1025 1028 1054 -hsync -vsync
EndSection

Section "Monitor"
 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:5:6:0"
    Screen          0
EndSection

Section "Device"
 # 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:5:6:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
#1       Virtual     1024 768
        Virtual     1280 1024
        Depth       24
#1	Modes      "1024x768@60"
	Modes      "1280x1024@65"
    EndSubSection
EndSection

Section "Screen"
 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

Thanks for all help.

---

### Post by skatedawe on 2008-07-22
The display layout could be set by manually clicking with the sreens hardware 
buttons. From right to more left, as i wanted... 

Problem solved.

---

