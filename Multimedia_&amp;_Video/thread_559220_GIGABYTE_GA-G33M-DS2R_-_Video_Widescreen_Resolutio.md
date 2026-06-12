---
title: "GIGABYTE GA-G33M-DS2R - Video Widescreen Resolution"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by curramberon on 2007-09-24
Just got a  GIGABYTE GA-G33M-DS2R with Q6600 processor. :guitar:
I installed Ubuntu 7.04, Feisty Fawn (32 bit).

Everything works except that I can't figure out what video driver to use to enable 1680x1050 60 Hz resolution and 3D.

At the moment the display is setup at 1280@1024 60 Hz, with the VESA driver.

My LCD is a Gateway FPD2275W with 1680x1050 native resolution (60 Hz).

The intel driver installed in the system is xserver-xorg-video-intel 2:1.9.94, but when I try to use it, the xserver fails, and I have to go back to the VESA driver.

This is how I've been trying to reconfigure the xserver :

sudo dpkg-reconfigure xserver-xorg

I have tried the i810, the Intel, and VESA drivers, but so far I have not been able to get native resolution working.

BTW I had previously installed the 64 bit version of Ubuntu 7.04, but I had the same problem.

This motherboard has integrated video: Intel GMA 3100.

Help!

:confused:

---

### Post by mhoev on 2007-09-26
curramberon,

Sorry, I can not help you with your issue :-(

But I hope you don't mind to answer a short question on the mainboard support in Gutsy Gibbon Tribe 5: Does the build in ethernet adapter work with the standard kernel? I am still on 7.04, and here the ethernet adapter is not supported (the switch shows 10M instead of 1000M, and eth0 does not send any packages to the net). I saw a patch for this based on 2.6.23rc2, but Gutsy Gibbon is based on 2.6.22.

Regards,
Markus

---

### Post by curramberon on 2007-09-26
mhoev,

In 7.04:
Enable "boot from Ethernet (not sure this is correct terminology)" from the BIOS.
This will fix your problem; no additional drivers will be required.

My original video resolution problem was fixed by following the instructions in this post:

[http://ubuntuforums.org/showthread.php?t=506744&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=506744&highlight=gma+3100)

To my surprise, I ended up with Gutsy, but it worked.
I now have 1680x1050, desktop effects, and I can play video files.

---

### Post by liuxin on 2007-09-30
i am suffering from the same problem with the G33 chipset and GMA 3100 graphics.
my ubuntu is 7.0.4.

but now i solved the problem of ethernet adapter not finding.
in G33 chipset, the integraded ethernet adapter is 82562v, you can download the ethernet module -- e1000 from here:
[http://downloadmirror.intel.com/11960/ENG/e1000.htm](http://downloadmirror.intel.com/11960/ENG/e1000.htm)

my lcd monitor is width-screen support 1440x900, but now i can only set up the resolution 
1280x1024.

finding  driver to GMA 3100
who can help me? thank you.

> **mhoev said:**
> curramberon,

Sorry, I can not help you with your issue :-(

But I hope you don't mind to answer a short question on the mainboard support in Gutsy Gibbon Tribe 5: Does the build in ethernet adapter work with the standard kernel? I am still on 7.04, and here the ethernet adapter is not supported (the switch shows 10M instead of 1000M, and eth0 does not send any packages to the net). I saw a patch for this based on 2.6.23rc2, but Gutsy Gibbon is based on 2.6.22.

Regards,
Markus

---

