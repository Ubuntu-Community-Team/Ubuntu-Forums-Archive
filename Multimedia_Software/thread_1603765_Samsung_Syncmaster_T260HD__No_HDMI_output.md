---
title: "Samsung Syncmaster T260HD | No HDMI output"
date: 2010-10-23
forum: Multimedia Software
---

### Post by dennisbinkhorst on 2010-10-23
Hi all,

I have recently purchased the Samsung Syncmaster T260HD 25,5" monitor in order to have a nice big screen to go with my Toshiba L550-13C notebook (17,3" screen). However, I have been unable to get the HDMI output to work. The D-sub connection on the other hand is fairly decent at 1920x1200 resolution.

The graphics card is the ATI Radeon Mobility HD4570.
I use the FGLRX non-free drivers that came -more or less- by default with 10.04.

The configuration below works with my notebook screen (0-LVDS), however not with the HDMI output (0-DFP2). The Samsung T260HD tells me "The source is not connected" on both HDMI channels.

*xrandr output*
```

$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 3520 x 3520
LVDS connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x900       60.1*+
   1440x900       60.1 +
   1280x800       60.1 +
   1152x864       60.1 +
   1280x768       60.1 +
   1280x720       60.1 +
   1024x768       60.1 +
   1024x600       60.1 +
   800x600        60.1 +
   800x480        60.1 +
   720x480        60.1 +
   640x480        60.1 +
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1200      60.0 +
   1776x1000      60.0 +   30.0     25.0  
   1680x1050      60.0 +
   1440x900       59.9 +
   1280x800       60.0 +   75.0  
   1920x1080      60.0     50.0     24.0  
   1600x1200      60.0  
   1400x1050      60.0  
   1600x900       60.0* 
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1280x720       60.0     50.0  
   1024x768       75.0     70.1     60.0  
   1152x648       60.0     50.0  
   1024x600       60.0  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   800x480        60.0  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)

```The fact that HDMI doesn't work, but the D-sub does, makes me think the problem lies in the current driver.

*xorg.conf*
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1600x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    DisplaySize  518        324
   HorizSync    30.0 - 81.0
   VertRefresh  56.0 - 75.0
    Option        "DPMS" "true"
    Modeline     "1920x1200@60hz" 154.000 1920 1968 2000 2080 1200 1203 1209 1235 +hsync +vsync
    Option       "IgnoreEDID" "true"
    Option        "PreferredMode" "1920x1200@60hz"
    Option        "TargetRefresh" "60"
    Option        "Position" "1600 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "IgnoreEDID" "true"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3520 3520
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
```Does anyone have this -or a similar- HW-configuration (The Samsung SyncMaster T260HD combined with the ATI Radeon Mobility HD4570) up and running on ubuntu 10.04?

Any help is appreciated!

---

### Post by dennisbinkhorst on 2010-10-23
Bump.

---

### Post by dennisbinkhorst on 2010-10-25
Bump? 
Anyone?

---

### Post by dennisbinkhorst on 2010-11-03
I replaced my EMINENT v1.3b cable with a 5 EURO HDMI v1.3c cable.
Output signal issue solved. 

Where did the days go where a cable was a cable?

---

