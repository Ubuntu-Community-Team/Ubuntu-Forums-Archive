---
title: "WSOD Triple Monitor Setup"
date: 2012-07-15
forum: Multimedia Software
---

### Post by lid6j86 on 2012-07-15
I'm running 2  AMD Radeon HD6900 cards.  The standard 'display'  (I believe its attached to xrandr?) did not detect all 3 monitors upon initial setup, so I downloaded the proprietary AMD drivers and installed them.

Although Catalyst originally stated my third monitor, I fixed Xorg.conf to finally at least recognize the third monitor and have the correct resolution when using Xinerama.  All three displays work fine and I can move freely back and forth

Here is my problem:  I would like to use Unity 3D which, as I understand, is not compatible with Xinerama currently.  When I turn off Xinerama to have run the three monitors independently, I get the White Screen of Death  (no display, x for cursor).  The display works temporarily when I first log in, but then goes white shortly after.

I've looked on the forums and have not seen much promise in fixes or workarounds yet.  I did see one where someone blamed it on nautilus.  I looked at nautilus, to see if I could just remove it but    a) it looks pretty important, and   b) I'm not fully sure of what it does or if there is a replacement for it, so I don't want to fiddle with it if I dont know what I'm doing.

has anyone figured out how to fix the WSOD on multiple displays yet?

I have 2 monitors attached via HDMI and 1 via DVI
I downloaded the latest Catalyst drivers (I believe it's 12.6) from the AMD website directly and installed manually.

here is my xorg.conf:

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[1]-1" 3360 0
    Screen         "aticonfig-Screen[1]-0" 1680 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP9"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP11"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP9"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP9" "0-DFP9"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP9" "1-DFP9"
    BusID       "PCI:9:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP11" "0-DFP11"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
This is from a xrandr query:

> xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 disconnected (normal left inverted right x axis y axis)
DFP7 disconnected (normal left inverted right x axis y axis)
DFP8 disconnected (normal left inverted right x axis y axis)
DFP9 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1680x1050      50.0 +   60.0* 
   1920x1080      60.0 +   50.0     59.9     30.0     25.0     30.0  
   1776x1000      50.0     59.9     25.0     30.0  
   1400x1050      50.0     60.0  
   1600x900       50.0     60.0  
   1280x1024      50.0     75.0     60.0  
   1440x900       50.0     59.9  
   1280x960       50.0     75.0     60.0  
   1152x864       50.0     59.9     75.0  
   1280x768       50.0     75.0     60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       50.0     75.0     70.1     60.0  
   1152x648       50.0     59.9  
   800x600        50.0     72.2     75.0     60.3     56.2  
   720x576        59.9     50.0  
   720x480        50.0     60.0     59.9  
   640x480        50.0     75.0     72.8     67.0     60.0     59.9  
DFP10 disconnected (normal left inverted right x axis y axis)
DFP11 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)

---

