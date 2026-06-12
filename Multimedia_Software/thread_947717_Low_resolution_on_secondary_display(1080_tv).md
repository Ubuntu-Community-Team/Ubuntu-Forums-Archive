---
title: "Low resolution on secondary display(1080 tv)"
date: 2008-10-14
forum: Multimedia Software
---

### Post by Aiurm on 2008-10-14
Hi

I have been using linux for a while now, but only on servers. So the display parts i am really uncertain about. 
I have a Samsung LE40M86BD that should be capable of running this according to specs.

Resolution: 1920x1080
Horizontal Frequency: 66.587 kHz
Vertical Frequency: 59.934 Hz
Pixel Clock: 138.500 MHz
Sync Polarity: +/-

I use Nvidia x server config and there the highest resolution i can choose is 640x480. I had the screen connected by vga when i first tried and assumed this was the reason. I bought a hdmi cable and connected this. But there was no change. I tried changing xorg.conf manually, but there seemed to be no changes no matter how i changed it. This is my file. I hope someone could help me solve this problem, i dont want to boot windows every time i want to see a movie on the tv :(.


```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Samsung"
    ModelName      "LE40M86BD"
    Option         "DPMS"
    HorizSync       15.0 - 68.0
    VertRefresh     49.0 - 61.0
    Modeline "1920x1080" 176.92  1920 2008 2224 2632  1080 1080 1083 1120
    Modeline "1080" 182.01 1920 1952 2640 2672 1080 1102 1113 1135
    Modeline "1080i" 148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync -vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection	   "Display"
         Depth	   24
	 Modes	   "1080i"
    EndSubSection
EndSection


```

---

### Post by Aiurm on 2008-10-19
I just tought i would write a bit of an update. I have tired connecting another screen as secondary, and its the same deal. Seems to me that there should be some way to have nvidia show me the "unsafe" modes for my screen. But alas there doesnt seem to be such an option.

I have searched the forum to find solutions and [http://ubuntuforums.org/showthread.php?t=831920&highlight=640x480](http://ubuntuforums.org/showthread.php?t=831920&highlight=640x480) this one seems to fit the bill. Having followed it I still dont get to choose any higher resolutions even with the "seperate X screen" option set. I have changed xorg.conf back and forth, but it doesnt display any new options.

---

### Post by aeiah on 2008-10-19
are those your modelines you have in xorg or ones you got from somewhere else? if they're from somewhere else, the app pstrip.exe for windows can generate linux modelines, perhaps that'll help.

my xorg for a 720p tv using an nvidia 7800gt has these bits in:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC L32W451"
    DisplaySize     1600    900
    HorizSync       31.0 - 50.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1240x692" 69.2 1240 1296 1424 1608 692 693 696 717 +hsync +vsync
    Option         "IgnoreEDID"
EndSection

```
note how i use 'IgnoreEDID'. perhaps its worth trying.

and..

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "FlatPanelProperties" "Scaling = Centered"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: NULL, DFP: 1240x692 +0+0"
EndSection

```

my screen section looks weird because i had to use 1240x692 to stop overscanning of the image.

in your screen section you set the mode to '1080i', have you tried setting it to the other two modes you specify in your modeline section? (1080 and 1920x1080)

---

### Post by Aiurm on 2008-10-19
I got the modelines from another user with the same tv as me who claims to have gotten things working.

[http://ubuntuforums.org/showthread.php?t=653081](http://ubuntuforums.org/showthread.php?t=653081)

I have tried contacting this user, but have had no luck.


I have tried different modelines and they all seem to be ignored... I always get 640x480 no matter what i write in xorg.conf, it seems i am getting overridden somehow.

---

### Post by Aiurm on 2008-10-22
Still looking for help on this, is there a way to force the screen to use my modelines?

If my modelines were wrong i would get a "out of sync" or something on my screen, but what i am getting is just some standard resolution.

---

### Post by Aiurm on 2008-10-30
Well i had to buy a second computer with vista on it to get my tv working in 1920x1080. But any input on getting it to work with ubuntu would be welcome.

---

### Post by Aiurm on 2008-11-01
If someone could help me i would be very greatfull. I dont understand whats happening. Whatever i write in xorg.conf seems to be ignored on the secondary monitor is something done wrong?

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier	   "Monitor1"
    VendorName     "Samsung"
    ModelName      "SAMSUNG LE40M87 1080p"
    HorizSync      30.0 - 80.0
    VertRefresh    56.0 - 75.0
   Modeline       "1080i" 138.5 1920 1952 1968 2080 1080 1083 1085 1111 +HSync +VSync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1920x1200 +0+0; DFP-1: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1080i"
    SubSection     "Display"
        Depth       24
        Modes      "1080i"
    EndSubSection
EndSection

---

