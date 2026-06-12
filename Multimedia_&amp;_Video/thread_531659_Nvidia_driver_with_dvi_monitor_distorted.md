---
title: "Nvidia driver with dvi monitor distorted"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by antaeus on 2007-08-21
I just installed Ubuntu Feisty fawn.  Default VESA nv driver worked fine at installation.  I've done apt-get update and apt-get upgrade.  I installed my nVidia driver using envy 0.9.7-0ubuntu8.  It appears that the nVidia driver is running now, but looks like there is a communication error with the DVI monitor.  The monitor displays a double image of the desktop with some lines on the right side, see attached picture.  When I run nvidia-settings it shows the resolution as 800x600, but from xorg.conf I would expect it to be 1024x768.  nvidia-settings will not let me select a different resolution.  I tried running 'dpkg-reconfigure xserver-xorg' to set the possible resolutions, but no change.

System:
Pentium 4
nVidia GeForce4 Ti 4200
DVI monitor (IBM T85D)

gorg.conf:
Section "Monitor"
    Identifier     "IBM T85D"
    HorizSync       28.0 - 49.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce4 Ti 4200"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce4 Ti 4200"
    Monitor        "IBM T85D"
    DefaultDepth    16

    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by tseliot on 2007-08-22
weird problem...

try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by antaeus on 2007-08-27
Problem solved, miscommunication with the monitor's EDID somehow.

See [http://www.nvnews.net/vbulletin/showthread.php?t=97075](http://www.nvnews.net/vbulletin/showthread.php?t=97075)

Basically, adding the following options in the device section of xorg.conf fixed the problem.  You must make sure that the HorizSync and VertRefresh are correct for your monitor before enabling these options.

Section "Device"
Identifier "nVidia Corporation NV25 [GeForce4 Ti 4200]"
Driver "nvidia"
[B]Option "UseEDID" "False"
Option "ExactModeTimingsDVI" "true"
Option "ModeValidation" "NoDFPNativeResolutionCheck"[/B]
EndSection

---

