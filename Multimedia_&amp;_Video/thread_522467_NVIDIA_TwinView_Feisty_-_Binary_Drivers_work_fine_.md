---
title: "NVIDIA TwinView Feisty - Binary Drivers work fine until computer is restarted"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by Fetch on 2007-08-10
hi
my nvidia binary drivers work great until I restart. After restarting X will not start, and I have to reinstall the nvidia binaries at the command line and restart gdm.

the xorg.conf file isn't changing at all, it is the same while the drivers are working, or when X fails to start and I'm in the console.


nvidia binary drivers work fine with one monitor, they stay put even thru restarts.

beryl, etc, work great over the two monitors, but if I restart, X won't even start/drivers need to be reinstalled.

Here is the 'working' xorg.conf file
You will see some commented out stuff I've played around with.

The two connected monitors are 19" LCDs, one LCD is on DVI, the other is Analog.

Please help me out guys, I've spent 7 hours on this!!


```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HIQ L90D+ D-SUB"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7100 GS"
EndSection

Section "Screen"

# Option "ConnectedMonitor" "DFP, CRT"
# Option "NoPowerConnectorCheck" "1"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 1024x768 +0+0, DFP: NULL; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection




```

---

### Post by tseliot on 2007-08-11
if you installed the driver from Nvidia's website, have a look at this page (where it says "Debian GNU/Linux or [K]Ubuntu with Xorg 7.x"):
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by Fetch on 2007-08-11
I used your envy script, worked perfectly! Thank you so much!

Obligatory rock on emoticon:
:guitar:

---

