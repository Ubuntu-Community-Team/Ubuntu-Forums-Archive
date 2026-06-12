---
title: "Resolution ok but full screen wrong size"
date: 2008-09-29
forum: Multimedia Software
---

### Post by TomiP on 2008-09-29
I am running a dual head setup with GeForce 6200 card, 1920x1200 LCD, 1600x1200 CRT and separate X servers. The system is Kubuntu Hardy, should that matter. The resolutions are correct and the whole screen estate is in use in both monitors.

But here is the problem: on the widescreen LCD something is confused about how wide the screen is. If I maximize a window it does not really maximize it but it leaves a bit of free space on the right side of the screen. This is not such a problem since I can manually "maximize" windows but full screen mode when playing movies for example shows the same behavior. The video does not really fill the whole screen and I have not figured how to fix it or go around it.

edit: after testing some more I noticed that this is purely a Kubuntu issue. Gnome works fine. KDE seems to think that the proper full screen width is 1594 and for example when resizing windows they 'snap' to that size. Still no luck fixing the problem though.

Would anybody have any ideas?

Here is my xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "Resolution" "800"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        VendorName      "Unknown"
        ModelName       "Samsung SyncMaster"
        HorizSync       30.0 - 121.0
        VertRefresh     50.0 - 160.0
        ModeLine        "1600x1200_95.00" 265.8 1600 1728 1904 2208 1200 1201 1204 1267 -hsync +vsync
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Monitor1"
        VendorName      "Unknown"
        HorizSync       30.0 - 83.0
        VertRefresh     55.0 - 75.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "nvidia"
        VendorName      "NVIDIA Corporation"
        BoardName       "GeForce 6200"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "True"
        Screen          0
EndSection

Section "Device"
        Identifier      "Videocard1"
        Driver          "nvidia"
        VendorName      "NVIDIA Corporation"
        BoardName       "GeForce 6200"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "True"
        Screen          1
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Videocard0"
        Monitor         "Monitor0"
        DefaultDepth    24
        Option          "metamodes" "CRT-0: 1600x1200_95.00 +0+0; CRT-0: 1600x1200 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 832x624 +0+0; CRT-0: 800x600 +0+0; CRT-0: 720x400 +0+0; CRT-0: 640x480 +0+0; CRT-0: 1600x1200_95 +0+0"
        SubSection      "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Videocard1"
        Monitor         "Monitor1"
        DefaultDepth    24
        Option          "metamodes" "CRT-1: 1920x1200_60 +0+0"
        SubSection      "Display"
                Depth           24
                Modes           "1920x1200"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Screen0" 1024 0
        Screen          1 "Screen1" LeftOf "Screen0"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
#       Inputdevice     "stylus"        "SendCoreEvents"
#       Inputdevice     "cursor"        "SendCoreEvents"
#       Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "ServerFlags"
        Option  "Xinerama" "0"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

---

