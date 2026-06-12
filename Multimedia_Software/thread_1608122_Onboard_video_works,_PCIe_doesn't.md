---
title: "Onboard video works, PCIe doesn't"
date: 2010-10-28
forum: Multimedia Software
---

### Post by zanus on 2010-10-28
I have been trying at this for a week now.  I got this dual monitor setup working at one point in time using the dual head attribute for aticonfig, but when I turned on Xinerama in Catalyst Control Center, I had a plethora of problems.. I figured my best bet would be to reinstall ubuntu and try it from scratch.

So as of right now, I am at a clean install of Meerkat x64.  At the end of the installation, my second monitor turned on! It was a miracle!... The one I wanted to work (the PCIe card) showed the Press ENTER to reboot screen, while the onboard card displayed a terminal type screen... showing various procedures ending.  Regardless, my monitor turned on, so I know it is possible that it is being recognized.

But now, when I login it doesn't turn on again.. never again.  Even when I go to gnome-display-properties, only one monitor appears.  Detect Displays does nothing.

Here's some info, just for ... clarification.
**lspci | grep VGA**
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```**xrandr**
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0 +   60.0* 
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
```**aticonfig --lsa**
```
* 0. 01:05.0 ATI Radeon HD 4200
  1. 02:00.0 ATI Radeon HD 4300/4500 Series

* - Default adapter
```**cat /etc/X11/xorg.conf**
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection
```Actually, that's the first time that xorg.conf has ever appeared for the first time in my many re-installations... I'm really surprised.  Every other time when I ran sudo Xorg -configure .. X would quit, go to console... show some lines and reboot the computer before I could read any of it.

What must I do to get my other monitor to show up in gnome-display-properties, preferably without Catalyst Control Center.  Although, I know I'll probably end up needing it just for the Xinerama feature.  Either way, can any body help me... I think my hair is turning gray now because of this and I'm only 24, this isn't good. :mad:

Thank you

---

### Post by zanus on 2010-10-28
Well I thought maybe adding the device to my xorg.conf file would make a difference, but I guess not... that or I have no clue what I'm doing.

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection
Section "Device"
    Identifier    "Secondary Device"
    Driver    "fglrx"
    BusID    "PCI:2:0:0"
EndSection
```

---

### Post by zanus on 2010-10-28
Ok, so going by this tutorial
[http://hamzakc.wordpress.com/2006/10/16/dual-monitor-setup-ubuntu-ati/](http://hamzakc.wordpress.com/2006/10/16/dual-monitor-setup-ubuntu-ati/)

I tried once again to replicate what I did the first time, getting my second monitor to work, but now I can't get it
When I run it, it creates an xorg.conf file like this
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-1" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "Secondary Device"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```
It boots up, and doesn't even make it to the GUI.. I'm at a terminal login screen, where I have to navigate to /etc/X11 and replace the current xorg.conf file with the backup that was created..

This is getting really frustrating.  I could install Catalyst Control Center at this point, but everytime I have installed it, it too only shows one display, BUT it also shows another "Unknown Display" with an unknown adapter.  So it's obviously being recognized....somewhat.

Nevertheless, I know it is possible because I ran the --initial=dual command at one time, turned on Xinerama and was successfully able to drag and drop from one screen to another.  I'm missing something, I'm just not savvy enough to figure it out.  Any help is greatly appreciated.

---

### Post by zanus on 2010-10-28
Ok, so I guess I'm giving up on this one.  I've came to the conclusion that my Radeon HD 4350 is just messed or corrupted somehow.

I decided to go a different route in trying to figure this out to come to this conclusion.  I turned my machine off and plugged my main monitor into the offending card... and the secondary one into the working card.  I proceeded to reinstall Ubuntu yet again with that configuration.  The GUI loaded up just fine... the Live CD I mean.  The pre-installation process seemed to work just fine, I was able to use gParted like normal and all that, but when it came time to go forward.. I constantly got bombarbed with "I/O errors".

I have no clue why a video card would have to do with the CD-ROM or HDD not being able to transfer/receive data, but I tried the installation again with an old 10.10 beta CD I had and I got the exact same result.  I even used a different CD-ROM drive.

In the end, I unlpugged my card.. plugged my main monitor back into my onboard card and installed with the stable CD and here I am with a complete and successful installation... but without my desired dual-monitor setup.

---

