---
title: "Problem setting up my HDTV as a second monitor."
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by MdaG on 2008-02-11
Hi!

I'm trying to use my HDTV as my second monitor and it's working fairly well with a couple of annoying exceptions.

1. The (complete) screen doesn't seem to be within the viewing area. 
See the image below and you'll know what I mean.
[IMG]http://img156.imageshack.us/img156/2338/pict0923xf4.th.jpg[/IMG]
[Enlarge](http://img156.imageshack.us/my.php?image=pict0923xf4.jpg) (<--- Click)

2. The resolution is too low.
It's currently set at 1280x720, but since it's a full HDTV I'd rather see it being around 1920x1080. My friend has the same model as me and has it working fine in Windows XP so I know it's doable.

See my **xorg.conf** below. I generated the two highest mode lines (for the HDTV) using gtf and without really knowing if it's nescessary...
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
    Option         "XkbOptions" "lv3:ralt_switch"
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

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L204WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "OEM 37'' TFT-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
    DisplaySize     819.6 461
    Gamma           1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    Option         "ConnectedMonitor" "DFP"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "nvidia-auto-select +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
	Virtual     1920 1080
        Depth       24
	Modes	   "1920x1080_60" "1280x720_60" "720x480_60"
    EndSubSection
EndSection

```

Any ideas anyone?

---

### Post by falstaff on 2008-02-12
Hello,

Try to use different Modelines, I had such problems few days ago... You can find my Modelines under Sharp LC-46X20E[http://www.mythtv.org/wiki/index.php/Modeline_Database]("http://www.mythtv.org/wiki/index.php/Modeline_Database").

I used xrandr to change/test the modelines, but i dont know if this is working with nvidia drivers too...

bye
falstaff

---

### Post by MdaG on 2008-02-27
> **falstaff said:**
> Hello,

Try to use different Modelines, I had such problems few days ago... You can find my Modelines under Sharp LC-46X20E[http://www.mythtv.org/wiki/index.php/Modeline_Database]("http://www.mythtv.org/wiki/index.php/Modeline_Database").

I used xrandr to change/test the modelines, but i dont know if this is working with nvidia drivers too...

bye
falstaff

Thanks for your reply. I've tried playing around with mode lines, but to no avail. According to [<link>this page</link>]("http://www.mythtv.org/wiki/index.php/Modeline_Database#Standard_Modelines") newer versions of the nvidia drivers mode lines are ignored. According to nvidia-settings I have version 100.14.19.

> Versions of the Nvidia driver from the 8xxx series upwards use a built in list of modelines. You just have to set the correct modes for your display in the Screen subsection.

The format is simple, HorizontalResolutionxVerticalResolution_frequency 

I'm not sure if my drivers are "new". They should be considering they came with this iteration of Ubuntu...

---

### Post by 01000111 on 2008-02-27
I had the same problem with my 61" Samsung but now it works perfectly at 1920x1080...  here's the secret...

My TV is plugged in to my PC via a VGA cable, not HDMI.  Boot into Recovery mode and issue the commands:

Xorg -configure
cp /root/xorg.conf.new /etc/X11/xorg.conf
reboot

I found that the above must be done while the TV is on and displaying the PC source, otherwise it don't work good!

Also, On several occasions, I had to issue the above 3 commands, logon, then reboot to Recovery mode and do the 3 commands again, then presto!

Good luck.

01000111

---

### Post by MdaG on 2008-02-28
> **01000111 said:**
> I had the same problem with my 61" Samsung but now it works perfectly at 1920x1080...  here's the secret...

My TV is plugged in to my PC via a VGA cable, not HDMI.  Boot into Recovery mode and issue the commands:

Xorg -configure
cp /root/xorg.conf.new /etc/X11/xorg.conf
reboot

I found that the above must be done while the TV is on and displaying the PC source, otherwise it don't work good!

Also, On several occasions, I had to issue the above 3 commands, logon, then reboot to Recovery mode and do the 3 commands again, then presto!

Good luck.

01000111

I don't understand. Are you saying that I have to auto configure each time I want that resolution? Also is it necessary to use the VGA-input (My TV only supports 1080p through HDMI and only 720p through VGA)?

---

### Post by morticul on 2008-03-04
Hi. Have you been trying twinview instead of xinerama. It works fine for me. I have an 1920x1200 screen external to my latpop. You can configure part of it using the nvidia-settings tool. Or directly in the xorg.conf.

Here is the part of my xorg.conf that does the trick:
```


Section "Device"
        ....
        # some other stuff here
        ....

	Option          "TwinView" "True" # this enable twinview
	Option          "TwinViewOrientation" "RightOf" # set the relative positoin of screens
	Option          "UseEdidFreqs" "True" # this asks automatically for frequencies
	Option          "MetaModes" "1440x900,1920x1200; 1440x900,NULL" # put possible resolution in the  order specified by useDisplayDevice
	Option          "UseDisplayDevice" "DFP-0,DFP-1" # determine the order of the screens.
	Option		"DynamicTwinView" "True"
EndSection

```

also, ```
grep 'NVIDIA' /var/log/Xorg.0.log
``` is useful to understand what's happening when things doesn't work.

---

