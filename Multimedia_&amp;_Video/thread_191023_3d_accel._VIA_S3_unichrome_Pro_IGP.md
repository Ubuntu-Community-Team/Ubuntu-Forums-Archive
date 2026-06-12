---
title: "3d accel. VIA S3 unichrome Pro IGP"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by manish_m on 2006-06-07
I have AMD64 pc with VIA S3 unichrome Pro onboard. Dapper correctly configured xorg. My problem is that i m getting very low fps with glxgears
Here is the output:
__driCreateNewScreen_20050727 - succeeded
2189 frames in 5.0 seconds = 437.716 FPS
2390 frames in 5.0 seconds = 477.914 FPS
2374 frames in 5.0 seconds = 474.695 FPS
I m attaching Xorg.0.log, excerpt from dmesg & glxinfo output.
i m uising "686" version of kernel.

---

### Post by Tomy on 2006-06-08
I have the unichrome Pro IGP on an MSI K8MM-V motherboard with a Sempron 2800 CPU.

My etc/X11/xorg.conf file has this section:

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

glxgears -printfps gives me 535 FPS with the "via" driver. 
If I use the "openchrome" driver I borrowed from Linspire I get 605 FPS.

Several of the Ubuntu screensavers freeze my system solid because of bugs in the "via" driver that were reported in November 2005. Hopefully, someone over at [www.x.org](www.x.org) will find the time to fix these  problems.  At least the "via" driver and accelerated 3d somewhat work in Dapper -  this is a big improvement.

Tomy

---

