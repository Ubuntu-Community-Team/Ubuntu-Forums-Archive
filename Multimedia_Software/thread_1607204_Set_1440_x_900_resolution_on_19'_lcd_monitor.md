---
title: "Set 1440 x 900 resolution on 19' lcd monitor"
date: 2010-10-27
forum: Multimedia Software
---

### Post by lrbottini on 2010-10-27
Hi everyone, need some help here, i'm trying to set the resolution to 1440 x 900 on ubuntu manually since it's not being showed under the options. I've followed this tutorial [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) 
The problem is that i don't have the output name to add on this command (as you can see below under the xrandr command.:

xrandr --addmode XXXXX 1440x900
[B]xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  

BTW i'm using one of the proprietary nvidia drivers.

Any help would be highly appreciated. 

Thanks. 
[/B]

---

### Post by lrbottini on 2010-10-27
Solved, edited xorg.conf file like this:


[LIST=1]
[*]Section "ServerLayout"
[*]    Identifier     "Layout0"
[*]    Screen      0  "Screen0" 0 0
[*]    InputDevice    "Keyboard0" "CoreKeyboard"
[*]    InputDevice    "Mouse0" "CorePointer"
[*]    Option         "Xinerama" "0"
[*]EndSection
[*] 
[*]Section "Files"
[*]EndSection
[*] 
[*]Section "InputDevice"
[*] 
[*]    # generated from default
[*]    Identifier     "Mouse0"
[*]    Driver         "mouse"
[*]    Option         "Protocol" "auto"
[*]    Option         "Device" "/dev/psaux"
[*]    Option         "Emulate3Buttons" "no"
[*]    Option         "ZAxisMapping" "4 5"
[*]EndSection
[*] 
[*]Section "InputDevice"
[*] 
[*]    # generated from default
[*]    Identifier     "Keyboard0"
[*]    Driver         "kbd"
[*]EndSection
[*] 
[*]Section "Monitor"
[*]    Identifier     "Monitor0"
[*]    VendorName     "Unknown"
[*]    ModelName      "CRT-0"
[*]    HorizSync       30.0 - 81.0
[*]    VertRefresh     56.0 - 75.0
[*]    Option         "DPMS"
[*]EndSection
[*] 
[*]Section "Device"
[*]    Identifier     "Device0"
[*]    Driver         "nvidia"
[*]    VendorName     "NVIDIA Corporation"
[*]    BoardName      "GeForce 7600 GT"
[*]EndSection
[*] 
[*]Section "Screen"
[*] 
[*]# Removed Option "metamodes" "1440x900 +0+0; 1024x768 +0+0"
[*]# Removed Option "metamodes" "1440x900_60 +0+0; 1024x768 +0+0"
[*]    Identifier     "Screen0"
[*]    Device         "Device0"
[*]    Monitor        "Monitor0"
[*]    DefaultDepth    24
[*]    Option         "TwinView" "0"
[*]    Option         "TwinViewXineramaInfoOrder" "CRT-0"
[*]    Option         "metamodes" "1440x900 +0+0"
[*]    SubSection     "Display"
[*]        Depth       24
[*]        Modes   "1440x900"
[*]    EndSubSection
[*]EndSection
[/LIST]
and the file ~/.config/monitors.xml with the desired resolution

---

