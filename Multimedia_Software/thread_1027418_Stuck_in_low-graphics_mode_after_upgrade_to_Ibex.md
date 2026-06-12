---
title: "Stuck in low-graphics mode after upgrade to Ibex"
date: 2009-01-01
forum: Multimedia Software
---

### Post by Harksaw on 2009-01-01
After upgrading to Ibex, when I start up I get the following message:

> Ubuntu is running in low-graphics mode.
The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Screen 0 deleted because of no matching config section
(EE) Device(s) detected, but none match those in the config file.

I've got a nvidia Geforce 7600GT, and two monitors, one is a LCD TV attached through HDMI. I'm running x64.

Under "Hardware Drivers" it says I'm running "Nvidia accelerated graphics driver (version 177) [Recommended]" I've tried uninstalling that and going back to version 173 without success.

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Philips FTV"
    HorizSync       15.0 - 70.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP-1: 1920x1080 +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP-0: 1600x1200 +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Any ideas?

---

### Post by 67GTA on 2009-01-01
Do you have a TV tuner card? Open a terminal and see if ```
lsmod | grep cx18
``` returns anything.

---

### Post by Harksaw on 2009-01-01
> **67GTA said:**
> Do you have a TV tuner card? Open a terminal and see if ```
lsmod | grep cx18
``` returns anything.

No, nothing returns. My TV is hooked up by an HDMI cable coming from the back of my video card. (via a DVI - HDMI converter)

---

### Post by zipher on 2009-01-02
Try this link:

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

Good luck!

---

### Post by eric321 on 2009-01-03
I had the exact same problem. I solved it by going back to the Hardy xserver-xorg packages.

[LIST]
[*]make backup of sources.list
[*]change sources.list back to the hardy URLs
[*]apt-get update
[*]apt-get remove xserver-common
[*]dpkg --force-depends -r x11-common
[*]apt-get -f install
[*]apt-get install xserver-xorg-core
[*]restore backup of sources.list (back to intrepid)
[/LIST]

After that my dual screen config worked again (with the latest 177 nvidia packages).

I did have a keyboard problem after this: up arrow worked as printscreen. I solved that by removing the xserver-xorg-input-evdev package.

---

### Post by james_steward on 2010-01-19
Going back to the Hardy xserver-xorg packages was the answer for me.
Thanks heaps.  Really irritating when an upgrade downgrades your system ;-)

---

