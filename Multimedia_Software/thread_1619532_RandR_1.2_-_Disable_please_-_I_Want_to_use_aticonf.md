---
title: "RandR 1.2 - Disable please - I Want to use aticonfig"
date: 2010-11-11
forum: Multimedia Software
---

### Post by dazman19 on 2010-11-11
I read a thread on how to disable this, and I don't think it has worked. I am pulling my hair out trying to get my dual monitors to work. 

So far I have managed to get my 27" displaying 1920x1080 and my 22" displaying its native 1680x1050. Which is progress... But The problem I have is I cant run any aticonfig commands now.

Currently the two screens are sitting on top of one another. 
I want to run this command but keep getting this error: 

[PHP]
$ sudo aticonfig --desktop-setup=horizontal
Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-6
[/PHP]

I want to be using fglrx driver so I can use 3d stuff later, (a few games and things).

My xorg.conf is now a mess(see below), I dont really know what to do. Can someone please help.

[PHP]
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[0]-1" Above "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
    Option        "MergedFB" "true" #Enable MergedFB function
    Option        "MonitorLayout" "TMDS, TMDS" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
    Option        "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
    Option        "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
    Option        "OverlayOnCRTC2" "1"
    Option        "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
    Option        "MetaModes" "1620x1080-1920x1080" #Monitor Resolutions for Primary-Secondary monitors 
    Option        "Capabilities" "0x00000800"
    BusID       "PCI:7:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
    BusID       "PCI:7:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3600 1080
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
[/PHP]

---

### Post by dazman19 on 2010-11-11
Ok so I have figured out that xrandr operates on the ports. I just need some way of turning it off. I cant do any of the bigscreen setup guides until i stop getting the error. Does anyone know how I can get this error to go away!

---

