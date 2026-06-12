---
title: "Automatic Log off on a dual screen mode"
date: 2012-03-03
forum: Multimedia Software
---

### Post by adonp on 2012-03-03
Hi,

I have a laptop (SiS Mirage 3 graphics) with max support resolution of LCD screen 1280x800 @75Hz, and an external TFT with max support resolution at 1280x1024 @75Hz.

I have modified xorg.conf so that I  can share any window by laptop screen and an external screen. For example, half of a window of an aplication could be on TFT screen  and other half on the other (laptop scrren). The position of screen is shown below (Left the TFT right the laptop):

TFT screen: ............     laptop screen: 
 __________ . . . . .        __________ 
|... 1280x....          |     . . . . . | 1280x         ........|        
|... 1024......            | . . . . .     | 800............             |      
|..................                     | . . . . . |__________|      
|_________ |                          

so far everything is ok, the problem that I have is the following,
whenever I move the mouse pointer below the lowest bound of laptop screen or move the mouse pointer from the lowest bound of TFT to the right till reaches TFT-laptop screen border, the system automatically logs me off.

My OS is debian

My xorg.conf is the following:

```


# xorg.conf BEGIN
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen          0 "Screen0"
    Screen          1 "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "extmod"
    Load  "dbe"
    Load  "record"
    Load  "dri"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "TURBO-X"
    ModelName    "TURBO-X model"
    HorizSync    31.0 - 83.0
    VertRefresh  56.0 - 76.0
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "DEL"
    ModelName    "DELL 1908FP"
    HorizSync    31.0 - 83.0
    VertRefresh  56.0 - 76.0
    Option        "DPMS"
EndSection


Section "Device"
    Identifier  "Card0"
    Driver      "sis671"
    VendorName  "Silicon Integrated Systems [SiS]"
    BoardName   "771/671 PCIE VGA Display Adapter"
    BusID       "PCI:1:0:0"
    Option      "MergedFB" "true"
    Option      "MetaModes" "1280x1024-1280x800 1280x1024-1280x800"
    Option     "MergedDPI" "100 100"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "sis671"
    VendorName  "Silicon Integrated Systems [SiS]"
    BoardName   "771/671 PCIE VGA Display Adapter"
    BusID       "PCI:1:0:0"
    Screen        1
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth     24
        Modes   "1280x1024"  "1280x800"    "1024x768"    "800x600"    "680x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card0"
    Monitor    "Monitor1"
    SubSection "Display"
        Depth     24
        Modes  "1280x800"    "1024x768"    "800x600"    "680x480"
    EndSubSection
EndSection

#----END


```I would appreciate any help,
Thank you

---

