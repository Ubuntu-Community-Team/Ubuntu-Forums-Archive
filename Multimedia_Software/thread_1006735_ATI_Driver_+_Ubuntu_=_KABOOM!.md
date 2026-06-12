---
title: "ATI Driver + Ubuntu = KABOOM!"
date: 2008-12-09
forum: Multimedia Software
---

### Post by Tr!p on 2008-12-09
As the title says, I tried installing the restricted driver for my ATI 9800 pro. After I re-started my machine to take affect, the screen is unreadable so much so, that I can't navigate around to re-install the old default driver. I'm currently using Ubuntu 8.04 What should I do? :cry:

---

### Post by NT4usB on 2008-12-09
Ctrl+Alt+F1 to get to a tty. Log in and try a couple things. 
Personally, I'd skip straight to Envy. It's always worked well for me (big thank you to tseliot for creating it!) 
If you're handy with vi, you can cd to .../X11 edit xorg.conf, and change the driver to vesa. Otherwise...```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```Nothing?```
sudo dpkg-reconfigure xserver-xorg
```step through and choose vesa for a driver. Restart gdm.
Still nothing?
```
sudo apt-get install envy
sudo envy -t
```
First choose the option to uninstall, cleans out all the video stuff first.
Then chose install.

---

### Post by Tr!p on 2008-12-10
Yesterday, in a period of frustration, I opened a terminal window and purged that driver.
```
sudo apt-get remove --purge xorg-driver-fglrx
```
After rebooting I was in a low graphic mode and after many unsuccessful attempts, was not able to recover on my own.
This morning, I did a fresh install and scratched one in for "lessons learned" (turn off eye candy before fooling with vid drivers)

---

### Post by SamTzu on 2008-12-10
Always the same old song and dance.
I'm at the point of moving back to M$ products and/or bying Nvidia card.

Here is my xorg.conf for those who have been fighting a losing battle with ATI X1?00 and dual display / multi display / Big Desktop / xinerama problems.
No wonder we are so lost when we can't even talk about it using same terminology.

Don't ask me why the X wants 3 Monitors when all I have is 2.

Sam

xorg.conf
-----------------------------------------------------------------------------------------------
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor 0"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor 1"
    Option        "RightOf" "Configured Monitor 0"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor 0"
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

### Post by CHaoSlayeR on 2008-12-10
Well with your Radeon 9800 you are better off with the current open source radeonhd driver which should deliver full hardware acceleration with your card. The fglrx driver is only required for the Xxxxx or HDxxxx product line.

So I would try that one.

Regards,

C]-[aoZ

---

