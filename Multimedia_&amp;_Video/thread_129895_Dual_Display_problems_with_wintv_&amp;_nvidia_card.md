---
title: "Dual Display problems with wintv &amp; nvidia card"
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by Bretls on 2006-02-14
I just purchased a wintv go plus card, when x11 starts only one of my displays work. I currently have a pci nvidia 5200 running two monitors. I'm not too worried about having the tv card work as I am still dual booting with windows. I was hoping someone could help me get dual displays back. My video currenty only shows on the secondary monitor. I've tried using Xinerama but it didnt work, just made picture show up on primary monitor instead of secondary. I also tried uncommenting NoTwinViewXineramaInfo. Any help would be great.

My current xorg.conf file:

```
Section "ServerLayout"

Identifier "TwinView Configuration"

Screen 0 "Default Screen" 0 0

InputDevice "Configured Mouse"

InputDevice "Generic Keyboard"

Option "Xinerama" "Off"

EndSection



Section "Files"



        # paths to defoma fonts

    FontPath        "/usr/share/X11/fonts/misc"

    FontPath        "/usr/share/X11/fonts/cyrillic"

    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"

    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"

    FontPath        "/usr/share/X11/fonts/Type1"

    FontPath        "/usr/share/X11/fonts/CID"

    FontPath        "/usr/share/X11/fonts/100dpi"

    FontPath        "/usr/share/X11/fonts/75dpi"

    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

EndSection



Section "Module"

    Load	       "GLcore"

    Load           "i2c"

    Load           "bitmap"

    Load           "ddc"

    Load           "extmod"

    Load           "freetype"

    Load           "glx"

    Load           "int10"

    Load           "type1"

    Load           "vbe"

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

    Option         "Buttons"       "7"

    Option         "ZAxisMapping" "6 7"

EndSection



Section "Monitor"

    Identifier     "COMPAQ FS760"

    Option         "DPMS"

EndSection



Section "Device"

    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"

    Driver         "nvidia"

     Option "NoLogo" "1"

Option "RenderAccel" "0"

Option "CursorShadow" "1"

Option "Coolbits" "1"

Option "ConnectedMonitor" "crt, crt"

Option "NoPowerConnectorCheck"

Option "TwinView" "1"

Option "Metamodes" " 1024x768,1024x768; 1024x768,NULL"

Option "SecondMonitorHorizSync" "UseEdidFreqs"

Option "SecondMonitorVertRefresh" "UseEdidFreqs"

 #Option "NoTwinViewXineramaInfo"

EndSection



Section "Screen"

    Identifier     "Default Screen"

    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"

    Monitor        "COMPAQ FS760"

        DefaultDepth    24

    SubSection     "Display"

        Depth       1

        Modes      "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       4

        Modes      "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       8

        Modes      "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       15

        Modes      "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       16

        Modes      "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       24

        Modes      "1024x768" "800x600" "640x480"

    EndSubSection

EndSection




```

---

