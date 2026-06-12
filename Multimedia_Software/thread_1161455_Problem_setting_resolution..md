---
title: "Problem setting resolution."
date: 2009-05-16
forum: Multimedia Software
---

### Post by Ennorath on 2009-05-16
I recently installed Ubuntu 9.04 on my DELL laptop, the problem is I'm trying to plug an external monitor but I can't get it to work with 1600x1050 resolution(I have no problem on windows vista though).

Info: 
Ubuntu Jaunty (using Gnome as GUI)
Video Card: ATI RADEON 3500 with fglrx driver installed
Monitor: Samsung 2232BW Plus 22"

Here's a copy of my xorg.conf, I'm fairly new to linux but from what I got on google it looks pretty weird. The only modification on it was this:
   
 DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1600x1050"
        Virtual    1600 1050
    EndSubSection

The xorg.conf:
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1600x1050"
        Virtual    1600 1050
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

Any ideias on how to solve this is welcome and if you need any extra info just let me know.

Thanks in advance.

---

### Post by Ennorath on 2009-05-17
Update, my xorg.conf file looks like this after a few tries at modifying it, none of which worked. aticonfig added some lines and I added a line generated using gtf and one manually. Still looking for new ideias.

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Modeline "1600x1050_75.00"  178.87  1600 1712 1888 2176  1050 1051 1054 1096  -HSync +Vsync
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option      "PreferredMode"      "1600x1050_75.00"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1600x1050_75.00"
    EndSubSection
EndSection

---

