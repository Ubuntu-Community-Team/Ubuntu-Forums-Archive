---
title: "Dual Monitors - Different Resolutions"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by anton_pm on 2007-06-20
Hi,

I've just moved over to Ubuntu from Fedora and have made much more progress on this. I have a 17" LCD and a 32" Widescreen LCD connected to the same card. I use the 32" to watch movies/TV etc, but can't get it to display in anything that doesn't start with 1280 - makes widescreen stuff look pretty bad.  I have set them up without Xinerama or Twinview, as I'm not too fussed about being able to drag windows over. I've set the WS LCD to 1360x768, but it still shows as 1280x1024 (same as the 17"). Not really too sure how to get around this one. Here's my xorg.conf:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen" 0 0
    Screen         "Screen1" RightOf "Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    Option "xinerama" "true"
#    Option "Clone"    "true"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
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
    Identifier     "LCD1770NX"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Q321"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen         0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen         1
EndSection

Section "Screen"
    Identifier     "Screen"
    Device         "Device0"
    Monitor        "LCD1770NX"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Q321"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1360x768"
    EndSubSection
EndSection


Any suggestions would be great

---

### Post by NT4usB on 2007-06-20
server is defining screen and screen (no distinction) and device is using screen 0 and screen 1

on second thought... maybe I don't know what I'm talking about.
here's mine if you want to compare:
[http://home.pacbell.net/clayt/xorg.conf.dapper.txt](http://home.pacbell.net/clayt/xorg.conf.dapper.txt)

---

### Post by anton_pm on 2007-06-21
Cheers mate,

There's some stuff on yours i'll be interested to try.

---

### Post by anton_pm on 2007-06-21
For anyone who's interested:

    Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
    Option "ModeValidation" "NoMaxPClkCheck"
    Option "ModeValidation" "NoDFPNativeResolutionCheck"

In the Screen Section for the 32" widescreen

And

    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0

In the Monitor section for 32" WS got this working and it look fantastic. I have now officially left windows behind!!

---

