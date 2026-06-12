---
title: "Display Dimmed After Suspend/Hibernation"
date: 2010-05-10
forum: Multimedia Software
---

### Post by neu5eeCh on 2010-05-10
Using 64Bit Ubuntu 10.04 on a VAIO VGN-FW373J. ATI Mobility Radeon HD  3650.

This relates to [Bug 451282]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/451282").

If I install the ATI 3D Drivers, the dimming problem goes away, but a host of other bugs crop up. After a resume from screen lock, suspend, or hibernation, the screen is reduced to graphical chaos. There are also hibernation errors. This bug is worse than the dimming bug, so I've uninstalled the 3d ATI drivers.

Question: Does anyone know a workaround?

If I can't find a workaround, I may have to look for a different Linux Distro or be content with Windows 7 on this particular laptop. :(

---

### Post by utnubuuser on 2010-05-10
Hardy Heron is good for a year yet...

---

### Post by neu5eeCh on 2010-05-10
> **utnubuuser said:**
> Hardy Heron is good for a year yet...

Probably so, but as much as I like Ubuntu, I'm thinking PCLINUXOS Gnome or KDE might be a good workaround. I haven't tried the latest PCLOS on this laptop, but I'll post the results of this distro is better (in this regard).

---

### Post by neu5eeCh on 2010-05-11
The solution shown at the Bug listing worked on my system (after a minor tweak that I missed the first time). I added the following to /etc/rc.local

> 
brt=`cat /sys/devices/virtual/backlight/acpi_video0/brightness`
abrt=`cat /sys/devices/virtual/backlight/acpi_video0/actual_brightness`
if [ "$brt" != "$abrt" ]; then
echo $abrt > /sys/devices/virtual/backlight/acpi_video0/brightness
fi


---

### Post by 5oak on 2010-09-13
> **VTPoet said:**
> The solution shown at the Bug listing worked on my system (after a minor tweak that I missed the first time). I added the following to /etc/rc.local

Yes, this worked for me too. However, the screen brightness isn't restored to the value that I entered in gconf-editor 
(98%),. but much less (I'm guessing 70-80%). Is it supposed to 'regain' the original brightness setting?

I'm curious... What minor tweak are you talking about?

---

### Post by Bucky Ball on 2011-07-11
Ever get this fixed? Having the same issue with 10.04 LTS ... 10.10 and 11.04 are fine.

The fix suggested here did nothing. ;(

---

