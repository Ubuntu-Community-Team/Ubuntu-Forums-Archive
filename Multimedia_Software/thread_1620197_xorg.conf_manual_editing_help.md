---
title: "xorg.conf manual editing help"
date: 2010-11-12
forum: Multimedia Software
---

### Post by dazman19 on 2010-11-12
Hi,

I had a post yesterday (that I will close)

Ever since I got an ati card it has been a nightmare trying to set up dual monitors. When i had Nvidia i used Twinview it was quite simple.

I have tried big desktop, xinemara or whatever and that is all rubbish. I get errors every time i type anything that starts with aticonfig. So I have resorted to editing the xorg.conf file manually and so far I have been relatively successful.

I have got 2 screens. I believe they are identified by: 
aticonfig-Screen[0]-0 # i think this is my 27" 1920x1080 screen
and
aticonfig-Screen[0]-1 # which I think is my 22" 1680x1050 screen

My xorg.conf file is below. I am trying to extend the display... But I dont know how to do it, I have tried to use this line below: 
Screen     0 "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"

it still loads, but it doesn't actually work. This set up does display the 1920x1080 res on the 27" and 1680x1050 on the 22" which is great, except its mirroring the displays and i got a gap on the 27" where the extra pixels are.... 

Can anyone help me get this file. I have made about a million backups so far... So I am not worried if it bombs out, I can always get it back.

Oh, this machine is running Maverick, my notebook runs Jaunty J.

Thanks
Daz

FYI fglrx is installed:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series  
OpenGL version string: 4.0.10237 Compatibility Profile Context




[PHP]Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen      1  "aticonfig-Screen[0]-1" 0 0
    Screen     0 "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    #Option        "Xinerama" "on"
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
    BusID       "PCI:7:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0" #samsung27
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Modes      "1920x1080" "1680x1050" "1280x1024" "1024x768"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1" #samsung22
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Modes      "1680x1050" "1280x1024" "1024x768"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
[/PHP]

---

