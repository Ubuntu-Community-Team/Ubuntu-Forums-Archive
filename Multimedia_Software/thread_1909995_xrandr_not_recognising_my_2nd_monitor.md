---
title: "xrandr not recognising my 2nd monitor"
date: 2012-01-16
forum: Multimedia Software
---

### Post by ahydra on 2012-01-16
Would be grateful for any help I can get with my dual-monitor setup, having tried all sorts of things for the last hour and a half.

I'm running ubuntu 11.10. My setup is an ATI 5450, monitors connected to the DVI and VGA ports. The DVI monitor should be 1680x1050 (primary, on the left) and the VGA one 1280x1024 (on the right). I installed the fglrx drivers and tried to use amdcccle to set up the dual-monitor system. However this resulted in a black screen on reboot, so I reinitialised xorg.conf with aticonfig -initial=dual-head -f, which at least brought one monitor back.

Tracking down the problem a bit further, it seems xrandr (v1.3) doesn't recognise the VGA monitor at all:

```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1600x1200      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0     75.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       60.0     75.0  
   1280x768       59.8  
   1280x720       59.8  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)

```This is weird because the VGA screen does show up in amdcccle (normally as the primary, even though nothing ever displays on it). xrandr doesn't recognise the VGA monitor if it's plugged into the on-board video either.

Enabling Xinerama in amdcccle didn't help at all.

My xorg.conf is currently a bit of a mess:
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[0]-1" 1680 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
#    Option        "Xinerama" "on"
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

Section "Monitor"
    Identifier   "0-DFP2"
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
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "DesktopSetup" "horizontal"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "0-CRT2"
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
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```My graphics card does appear in lspci as 

```

01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]

```As stated, I'd be grateful for any advice on how to be able to use both monitors (as a combined desktop, i.e. windows can be dragged between them)  - thanks :)

ahydra

---

### Post by wolfen69 on 2012-01-16
I noticed that in the section 
```
Section "ServerFlags"
#    Option        "Xinerama" "on"
EndSection
```
there is a "#" in front of option. # must be removed, otherwise xinerama will not be used.
```
gksudo gedit /etc/X11/xorg.conf
```
remove the # and save. Reboot.

---

### Post by ahydra on 2012-01-16
> **wolfen69 said:**
> I noticed that in the section 
```
Section "ServerFlags"
#    Option        "Xinerama" "on"
EndSection
```there is a "#" in front of option. # must be removed, otherwise xinerama will not be used.
```
gksudo gedit /etc/X11/xorg.conf
```remove the # and save. Reboot.

Tried this - no luck I'm afraid :(. I did mention in the OP that enabling Xinerama didn't help - the problem seems to be deeper than that, in that xrandr doesn't even think the 2nd monitor is connected.

I'll keep Xinerama turned off for now so that I can use xrandr.

ahydra

---

