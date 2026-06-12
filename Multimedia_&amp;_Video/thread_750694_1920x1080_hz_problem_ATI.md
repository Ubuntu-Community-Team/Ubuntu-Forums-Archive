---
title: "1920x1080 hz problem ATI"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by oyvinvo on 2008-04-09
I've just switched my graphics card from a nvidia chipset to a ATI Radeon HD 2600, and got some problems with underscanning. First of all, the TV is a Toshiba 42" 42Z3030D, and should work best with 100 hz. The highest I can get is 60hz, but I have to decrease it to 50 hz to get the exact 1:1. It seems when I change it to 50 hz, it doesn't change it globally. There's still the underscan problem in the login/splash screen. Which is not really a problem, but the annoying thing is the same underscan problem in mythtv. I've changed the settings in mythtv to 50hz aswell. When I quit mythtv the hz is also set to 50 in gnome, so I have to change it back to 60.

So my question, is actually two questions. How can I get it to use 100hz? And why does it keep changing when I start mythtv? Since this is my first experience with ATI cards, I guess the problem lays in my xorg.conf file, so I'm therefor pasting it here. Hope someone can help me out, or atleast point me in the right direction. Would be much appreciated:)

```

# xorg.conf (xorg X Window System server configuration file)

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
        Load  "GLcore"
        Load  "v4l"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "no"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I'm used to setting the video modes in the xorg.conf file from previous experience with nvidia, but it looks like ATI has another way around this. 

Another thing is that lspci doesn't seem to find the card;
> 01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9588
but I actually got catalyst up running after downloading the drivers from ati.amd.com. Before that, it complained about that the card wasn't detected, when I used other drivers.

---

### Post by Yellow Pasque on 2008-04-09
Try playing with cvt and pasting the modelines into the monitor section (chage the underscore to a '@')
```
cvt -v 1920 1080 100.0Hz
```

For 'Unknown device', try updating the database. I don't think this affects the operation of the card/driver anyway.
```
sudo update-pciids
```

---

### Post by oyvinvo on 2008-04-09
Cheers.

> 01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT]

I'm going to bed now, but I'll try adding the modelines in the monitor section tomorrow:) I'll let you know how it goes. I got a warning from CVT tho, but guess it's not that important.

```

b52@b52-media:/etc/modprobe.d$ cvt -v 1920 1080 100.0Hz
Warning: Refresh Rate is not CVT standard (50, 60, 75 or 85Hz).
# 1920x1080 99.90 Hz (CVT) hsync: 114.58 kHz; pclk: 302.50 MHz
Modeline "1920x1080@100.00"  302.50  1920 2072 2280 2640  1080 1083 1088 1147 -hsync +vsync

```

---

### Post by warp99 on 2008-04-09
Since their are no resolution modes with that refresh rate for your particular monitor your can setup a "Generic Monitor" or "Display" and set them yourself from the monitor dialog GUI, then entries similar to these would show up in your xorg.conf.

```
Section "monitor" #
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       31.5-65.5
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

```
and here:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6200]"
        Monitor         "monitor1"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1680x1050@60"  "1600x1024@60"  "1440x900@60"   "1280x800@60"  "1280x720@60"    "1280x768@60"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection

```

Of course your refresh rates will be higher, but that's how you would get the refresh rate and resolution you wanted.

---

