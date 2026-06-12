---
title: "ATI multi screen big desktop impossible to setup on 11.04"
date: 2011-06-11
forum: Multimedia Software
---

### Post by djahma on 2011-06-11
Hi,

2nd day looking for a solution...I need some help to setup a simple 2 screens extended desktop. From my laptop with an nvidia card, it was very easy and done in seconds. But with my new desktop loaded with amd hardware, it's turning into a nightmare.

I've posted on details of my hardware and of [ this problem here]("http://ubuntuforums.org/showthread.php?t=1702573"), and I'm encountering new trouble. Since then, my xorg.conf has changed a little without success:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen      1  "amdcccle-Screen[2]-0" LeftOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
    Option        "DesktopSetup" "horizontal,reverse"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-0"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
    Option        "Monitor-CRT2" "1-CRT2"
    BusID       "PCI:2:0:0"
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
    Identifier "amdcccle-Screen[2]-0"
    Device     "amdcccle-Device[2]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

So I've ended up understanding the problem is that RandR12 is enabled so amdcccle cannot manage the monitors itself. I followed various guides to disable it, but it still tells me RandR is enabled (I amended the files xorg.conf and amdpcsdb in terminal mode when RandR was indeed not running, then rebooted):
> aticonfig --query-monitor
Error: option --query-monitor is not supported when RandR 1.2 is enabled!
> grep RandR /etc/X11/xorg.conf
    Option        "EnableRandR12" "false"
    Option        "EnableRandR12" "false"
> grep RandR /etc/ati/amdpcsdb 
EnableRandR12=Sfalse

So I'm still stuck in this bloody double X session setup: one per screen...
I'm desperate to get a mere extended desktop over 2 screens only.](*,) Please help.
thanks,
D.

---

### Post by djahma on 2011-06-12
I've found a solution...posted on [http://ubuntuforums.org/showthread.php?t=1702573](http://ubuntuforums.org/showthread.php?t=1702573) 
Sorry forum moderator, I know you hate duplicated entries, but it tortured my mind not to share my experience...

---

