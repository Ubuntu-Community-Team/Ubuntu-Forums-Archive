---
title: "No screen? How do modify &quot;Screen&quot; to accept Geforce2 card?"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by sansrage on 2007-05-02
Hey guys, noob trying to figure this out.....

I've changed my device settings to 

Section "Device"
Identifier "6600"
Driver "nvidia"
BusId "PCI:0x0110

and Fiesty loaded up smaller fonts and a better resolution, but when it tried loading the desktop it failed out and said No screen loaded....I know the problem is it's going to a default onboard Intel chipset instead of my GeForce2 card, but I'm confused how it's to read 

(currently, it's)
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]
Moniter "HP w1907"
Default Depth 24
Subsection "Display"
(and then all the values)

What do I plug in for the GeForce2 MX/MX 400 card? I've read the readme.txt and I'm still confused....I'm sooo close!!!

---

### Post by sansrage on 2007-05-02
> **sansrage said:**
> Hey guys, noob trying to figure this out.....

I've changed my device settings to 

Section "Device"
Identifier "6600"
Driver "nvidia"
BusId "PCI:0x0110

and Fiesty loaded up smaller fonts and a better resolution, but when it tried loading the desktop it failed out and said No screen loaded....I know the problem is it's going to a default onboard Intel chipset instead of my GeForce2 card, but I'm confused how it's to read 

(currently, it's)
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]
Moniter "HP w1907"
Default Depth 24
Subsection "Display"
(and then all the values)

What do I plug in for the GeForce2 MX/MX 400 card? I've read the readme.txt and I'm still confused....I'm sooo close!!!

crap....forgot to mention I'm running Ubuntu Fiesty.

---

### Post by phidia on 2007-05-02
This happens with onboard video sometimes/all the time? Can you disable the onboard gpu in your bios?
Even if you can't do that you can run > sudo dpkg-reconfigure xserver-xorg Back up your current xorg 1st and the dpkg command could allow you to configure the Geforce.

---

### Post by sansrage on 2007-05-02
> **phidia said:**
> This happens with onboard video sometimes/all the time? Can you disable the onboard gpu in your bios?
Even if you can't do that you can run  Back up your current xorg 1st and the dpkg command could allow you to configure the Geforce.

It happens all the time with the onboard video. How do I disable the Bios?
OK...how do I backup the xorg in recovery mode? I haven't been able to load into my desktop with the nVidia card loaded.

---

### Post by phidia on 2007-05-02
When you get that no usable screen found message just open a shell i.e. press the alt+ctrl+F1 keys then cd to /etc/X11. You should see xorg.conf there (do ls <enter>) to view the contents of the X11 directory. type sudo mv xorg.conf /etc/X11/xorg.conf.bak
After that you can run the dpkg command I provided earlier.

---

