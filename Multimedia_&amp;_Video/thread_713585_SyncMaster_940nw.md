---
title: "SyncMaster 940nw"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by repos on 2008-03-02
Hello everybody!!

I have been trying to get two monitors working together, but I don't get it :mad:

Details:
Monitor 1: from Compaq Presario C700
Monitor 2: SyncMaster 940nw
OS: Ubuntu 7.10
Video:  Intel (Mobile GM965/GL960 Integrated Graphics Controller).

This is the very last xorg.conf I tried (don't know what I'm doing wrong):
With this I got two clone monitors with a very low resolution.

```
---
[...]
Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller0"
Driver "intel"
BusID "PCI:0:2:0"
Screen 0
EndSection

Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller1"
Driver "intel"
BusID "PCI:0:2:0"
Screen 1
EndSection

Section "Monitor"
Identifier "Generic Monitor0"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Generic Monitor1"
Option "DPMS"
HorizSync 30-81
VertRefresh 56-75
EndSection

Section "Screen"
Identifier "Default Screen0"
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller0"
Monitor "Generic Monitor0"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

Section "Screen"
Identifier "Default Screen1"
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller1"
Monitor "Generic Monitor1"
DefaultDepth 24
SubSection "Display"
Modes "1440×900" "1024×768" "800×600" "720×400" "640×480" "1×1"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen0"
Screen "Default Screen1" RightOf "Default Screen0"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Don't forget xinerama!!!111oneoneone11!eleven!!11
Option "xinerama" "on"
Option "clone" "off"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

```

Thanks for the help!

---

### Post by petzworld999 on 2008-03-02
I see some errors near the end. Try doing this:
sudo gedit /etc/X11/xorg.conf
[/code]

and changing it to this:


```

---
[...]
Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller0"
Driver "intel"
BusID "PCI:0:2:0"
Screen 0
EndSection

Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller1"
Driver "intel"
BusID "PCI:0:2:0"
Screen 1
EndSection

Section "Monitor"
Identifier "Generic Monitor0"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Generic Monitor1"
Option "DPMS"
HorizSync 30-81
VertRefresh 56-75
EndSection

Section "Screen"
Identifier "Default Screen0"
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller0"
Monitor "Generic Monitor0"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

Section "Screen"
Identifier "Default Screen1"
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller1"
Monitor "Generic Monitor1"
DefaultDepth 24
SubSection "Display"
Modes "1440×900" "1024×768" "800×600" "720×400" "640×480" 
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen0"
Screen "Default Screen1" RightOf "Default Screen0"
# Don't forget xinerama!!!111oneoneone11!eleven!!11
Option "xinerama" "1"
Option "clone" "0"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
#InputDevice "Synaptics Touchpad"
EndSection


```

if that doesn't work, try starting from scratch:

```

sudo dpkg-reconfigure xserver-xorg

```

---

