---
title: "Resolution issue - Jaunty/NVidia 6800 in SLI"
date: 2009-06-12
forum: Multimedia Software
---

### Post by ProggyBS on 2009-06-12
Hello,

I'm fairly new with Linux but I'm experiencing some issues with my video cards in Jaunty.

I have 2 NVidia Geforce 6800s running in SLI and I'm currently using the 180 NVidia driver.

My first problem was after upgrading Ubuntu to Jaunty, XServer was unable to start because it didn't register my SLI properly so after a manual edit of xorg.conf to read the BusID, I am able to run GDM.

My problem now is my lack of resolution choices. I am currently limited to a max resolution of 640x480 with a 60hz refresh rate. I've played around with some changes to xorg.conf to try to force other resolutions but I am unable to reach my desired resolution of 1280x1024 with a 75hz refresh rate (Windows Capable).

I'm sure it is just a configuration issue and any help would be appreciated. I have added a copy of my current xorg.conf below. Also, I'm not sure of my monitor's capable Horizontal and Vertical rates. I am unable to find the information online but my monitor is a 19' HP 9500.

Here is xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    ModeLine       "1280x1024_75.00" 138.54 1280 1368 1504 1728 1024 1025 1028 1069
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "SLI"
    BusId       "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection


```

---

### Post by benagro on 2009-06-13
I have just the same problem with a NVidia 6600. 
I have a Acer P191w monitor that works perfectly in win with a 1440x900 resolution, but the best I can have in Ubuntu, either with KDE or Gnome, is a 1360x768 res, that gives a distorted image.
Any help please?

---

### Post by ProggyBS on 2009-06-13
I ran xfix from recovery mode and readded the BusID to my xorg.conf. I was then able to get a better resolution (1024x768). It was using the VESA driver at the time which was not sufficient so I used EnvyNG to load the 180 Nvidia driver again.

After restarting Xserver, I am able to go up to a max resolution of 1360x768, but I am still not able to go up to my desired 1280x1024 with a 75hz refresh rate. Also, I am not able to enable visual effects now.

Here is an updated xorg.conf:

```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    BusId        "PCI:5:0:0"
    Option        "SLI"
    Driver    "nvidia"
EndSection

```

---

