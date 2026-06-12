---
title: "Display details fixing the small problems ATI dual setup"
date: 2010-05-31
forum: Multimedia Software
---

### Post by marcoftheknight on 2010-05-31
_**PLEASE READ BEFORE : Well There might not be a solution to this problem other then buying a better LCD because my TV LCD might just not be good enough and if anyone knows how I could tell this please let me know and what I should look for when buy a larger lets say 23-32 inch screen ( might get 23 inch)**_

Ohh and what does Spilled the Beans means and where are is the information on this? lol :) im a newbie sometimes but its all good. 

I have vertical lines that  slowly go up they aren't super easy to see but after about 1min you notice it and I have no Idea why I have this problem secondly yon my other monitor the 32inch 1920 by 1080 has small jaged (saw tooth lines) how do I go about fixing these problems? My Dvds have horizontal lines every once in a while that are annoying when alot is going on on the screen. The last small detail is contrast when running blender the 3d objects dont show good shading contrast. how do I fix these minor but very important details or even knowing whats causing the problem. graphics gurus welcome. 

I have the lastest catalys setup 10.05 installed  

xrandr -q
Screen 1: minimum 320 x 200, current 1366 x 768, maximum 1366 x 1366
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       59.8*+
   1280x1024      75.0  
   1280x960       75.0  
   1360x768       59.8  
   1152x864       75.0  
   1280x768       75.0  
   1280x720       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     67.0     59.9  
CRT2 disconnected (normal left inverted right x axis y axis)

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[1]-1" 1920 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    HorizSync    50.0 - 65.5
    VertRefresh  56.0 - 75.0
    Gamma        1
    ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine     "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine     "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine     "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine     "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine     "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine     "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine     "1920x1080@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "30"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
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
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

