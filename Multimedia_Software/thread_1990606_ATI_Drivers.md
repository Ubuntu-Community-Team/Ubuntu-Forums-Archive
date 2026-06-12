---
title: "ATI Drivers"
date: 2012-05-29
forum: Multimedia Software
---

### Post by chome4 on 2012-05-29
Installed a new video card and lspci | grep VGA gives:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5430 Series]

When I go to 'Additional Drivers',  and activate 'ATI/AMD proprietary FGLRX graphics driver' and restart, the screen goes black and tells me the resolution is out of range.

The only way to get the display to show again was to do a fresh install.

Where can I find the drivers for this video card?

---

### Post by gnusci on 2012-05-29
Check this thread:

[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

---

### Post by chome4 on 2012-05-30
> **gnusci said:**
> Check this thread:

[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

Followed everything up to reboot. Then I got:

Signal out of range

H: 74.9KHz   V:59.9Hz

Mode should be below...

1280 x 1024 75Hz

Same problem, basically!

---

### Post by gnusci on 2012-05-30
post the output of:

$ cat /etc/X11/xorg.conf

---

### Post by chome4 on 2012-05-30
> **gnusci said:**
> post the output of:

$ cat /etc/X11/xorg.conf

 Booted with my Linux Knoppix DVD and found xorg.conf: 

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver       "fglrx"
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
    EndSubSection
EndSection

---

### Post by chome4 on 2012-05-30
These instructions give a way of showing a fuller list of resolutions...

[http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation/comment-page-1/#comment-10233](http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation/comment-page-1/#comment-10233)

But I still can't see this list when I use the regular 'Displays' facility.

There's no xorg.conf present, by the way. I did a fresh install of 12.04

---

