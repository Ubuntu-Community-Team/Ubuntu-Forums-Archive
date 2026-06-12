---
title: "Atom N2800 with GMA 3600 doesn't work"
date: 2012-06-13
forum: Multimedia Software
---

### Post by edmond2010 on 2012-06-13
I just tried ubuntu 12.04 32bit ( 3.2 kernel ) on a Intel DN2800MT board hoping that it would have framebuffer support for the GMA 3600, I have compiled some kernel versions 3.4.2 and activate gma3600 driver,but the attached monitor goes into standby (no signal) as soon as the frame buffer gets activated during boot.
 
Kindly post step-by-step solutions to the Intel GMA 3600 problem.
 
Thanks!

---

### Post by firekage on 2013-06-08
I have AOD 270 with GMA3600 - upgraded kernel to newer than 3.2 (i think that is 3.5.xx) and added acpi_backlight=vendor to grub and it works. Fn keys works, can set brightness, the only thing to do is now creating in rc.local one file because during the boot the screen is very black, not bright - i can set it when i logged in, but during the boot is pitch black because of driver. Even when i set brightness after when i'm logged, during reboot is being forgotten, that's why i have to create rc.local but don't have time to check it.

---

