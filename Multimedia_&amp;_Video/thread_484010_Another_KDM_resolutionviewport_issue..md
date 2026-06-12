---
title: "Another KDM resolution/viewport issue."
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by TheVrolok on 2007-06-25
I boot up, KDM is running at a low resolution (looks something like 640x480), but in a viewport that's more like 800x600 (as in, it's low res, but I'm able to scroll the screen edges and move the viewport).  Once I log in, all is well and I'm up at 1680x1050.  Just not sure why KDM is running oddly.

Here's my xorg.conf

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen"  
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
  # path to defoma fonts
    FontPath 	"/usr/share/fonts/X11/misc"
    FontPath 	"/usr/share/fonts/X11/100dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/75dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/Type1"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/usr/local/share/fonts"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "vbe"
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
    Option         "Buttons" "7"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
    Identifier     "VX2025wm"
    VendorName     "ViewSonic"
    ModelName      "VX2025wm"
    Gamma           1.11 1.03 1.04
    ModeLine       "1680x1050@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6800 (generic)"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800]"
    Monitor        "VX2025wm"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by TheVrolok on 2007-06-26
bump

---

### Post by dabl on 2007-06-26
Before you log in, you're looking at a 640x480 pixel splash screen image.  Once you log in, the xserver starts and runs the display as defined in your /etc/X11/xorg.conf file.

---

