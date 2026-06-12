---
title: "Screen resolution changes during boot/load"
date: 2009-12-05
forum: Multimedia Software
---

### Post by airborne180 on 2009-12-05
Goal is Mythtv, but just getting system loaded to proper resolution.  Hardware is as follows:

Hardware
Memory: 1002.5 MiB
Processor: AMD Athlon(tm) XP 2200+

System Status
Available disk space: 229.0 GiB

Video Card
 BoardName:     "GeForce4 Ti 4200 with AGP8X
 Drivers: Nvidia accelerated graphics driver (version 96)Ubuntu

Sustem:
Release 9.10 (Karmic)
Kernel Linux 2.6.31-15-generic
GNOME 2.28.1
System:

Monitor: Philips 37PFL5322D/37, 37 inch LCD TV.
    This TV does not seem to transact EDID, so I created an xorg.conf as follows to support stated 1360x768 resolution:

Code:
Section "Monitor"
        Identifier      "LCD TV"
        HorizSync 30.0 - 75
        VertRefresh 60.0
        Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
        DisplaySize     818     462     # 1360x768 42.2dpi
        Option "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "LCD TV"
        Device          "Configured Video Device"
        DefaultDepth    24
        Option  "AddARGBGLXVisuals"     "True"
        Option "MetaModes" "1360x768_60.00"
EndSection

Section "Module"
        Load    "glx"
EndSection
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce4 Ti 4200 with AGP8X
        Option "NoBandWidthTest" "1"
        Option  "NoLogo"        "True"
        Option  "UseEDID"       "False"
EndSection

This seems to work mostly okay, system boots about half way, showing the "UBUNTU" screen, with the little line underneath, with the highlight segment moving back and forth.  A look at /var/log/Xorg.0.log shows no errors setting resolution.  Shortly before the Gnome desktop appears, something calls the nVidia proprietary driver to set the resolution back to 800x600, as shown on the last line of Xorg.0.log.  I can reset it using the | System | Preferences | Display |, and all works reasonably well.

I have grep'd through where I thought the startup sequences were, trying to find something in the bootup that might be setting the resolution back to 800x600, but didn't find anything.

I really need this thing to boot and remain in 1360x768.  Any ideas where to look for something resetting the resolution?  Perhaps something is expecting EDID, and resets to a default when it doesn't find it??

I'd be grateful for any ideas.

Thanks!

---

### Post by airborne180 on 2009-12-26
I had been using the nVidia tool to change resolution in | System | Preference | Display |, and I saw on another post that it was better to answer "No" to the question: "Do you want to use your graphic driver vendor's tool instead?"  The resolution has stopped changing after boot once I tried this path.

It might be nice to know what file is being modified by the other path, does anyone have an idea where this change is being written?  It's not in xorg.conf.

Thanks!

---

### Post by HappyFeet on 2009-12-26
You will need to do:
```
gksudo nvidia-settings
```
Then make the necessary adjustments. Apply and Save the settings. It will probably tell you "failed to parse....."

You will have to do the following after that.

Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by crank48 on 2009-12-29
> **airborne180 said:**
> I had been using the nVidia tool to change resolution in | System | Preference | Display |, and I saw on another post that it was better to answer "No" to the question: "Do you want to use your graphic driver vendor's tool instead?"  The resolution has stopped changing after boot once I tried this path.

It might be nice to know what file is being modified by the other path, does anyone have an idea where this change is being written?  It's not in xorg.conf.

Thanks!
Thanks Airborne180!!!!!

After 3 days of futzing with my nVIDIA 6100 saving-of-settings upon reboot and having them stick and typing in countless lines of code from all these wonderful Unix experts, you're ultra-simple solution solved all my problems!!!  I guess I had wrongly put all my eggs in the nVIDIA basket.  Airborne180, you made my day, no er, month!  Crank48

---

