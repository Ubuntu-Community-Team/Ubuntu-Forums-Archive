---
title: "ATI Radeon Overheating problem can be solved!!??"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by Dropknee on 2006-09-05
I found this in a release note from drivers 8.26.18, check [this]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html"). This is called Thermal Event Power Management and need to be activated in order to work.

Thermal Event Power Management

This release of the ATI Proprietary Linux driver now enables Thermal Event Power Management. The ATI Proprietary Linux driver now reacts to Thermal Events by throttling down the GPU to prevent overheating. For this feature to work please ensure that the daemon /sbin/atieventsd is started. Further details can be found in topic number 737-22637 

Maybe ppl like me with X800 card, have the solution to the overheating problem, but I really dont know how to activate this feature.

Any help from a guru out there??? I want to go back to my Ubuntu box, Im in Windows because my card overheating in Ubuntu with ATI propietary drivers, and I know a lot of ppl have this problem too. 

Thx for any help

---

### Post by Dropknee on 2006-09-05
I boot up Ubuntu to check this and  use BUM (Boot up Manager) to check this service and this service appear, but with a interrogacion (?) mark, so I dont know is the service start or not.

---

### Post by blastermaster on 2006-09-06
Maniatico LOL, just a joke, I hope you get this working, I cant help since I use nvidia :D

---

### Post by zak- on 2006-09-07
I see I have this service running just fine, but it's not doing any good. And I don't see how this would solve the x800/x850 overheating issue anyway.

As the description says, this feature will down-clock the GPU when the temperature exceeds safe levels. If this threshold temperature were the same as the one used for accelerating the fan speed, then this would mean us constantly having underclocked GPUs even without any 3D applications. This is not necessary in windows where I have my GPU at the default 500 MHz and the temperature stays in check, just as it should.

---

### Post by bropers on 2007-08-29
I have been fighting this problem as well, on an IBM / Lenovo ThinkPad Z61p. Very shortly after starting X with almost any version of the fglrx driver (Ubuntu provided or built from source), my system will shutdown. It took me a while to discover it was due to a critical thermal event, reporting a temperature of 128C! I then started watching temperatures via ACPI, but was only looking at CPU temperatures. With the thinkpad_acpi module loaded, I have access to the /proc/acpi/ibm/thermal file which includes the GPU temperature. With the vesa X module, I hover around 115C and 120C, which is awful hot to start with. I can "stress" the GPU just by grabbing a window and "wiggling" it around, causing the temperature to rise a couple degrees C.

Does anybody have any ideas on why the GPU runs so hot or on how to mitigate this problem? I would love to run fglrx (allowing me to finally run this machine in it's native wide-screen mode and to do some beryl eye-candy goodness).

TIA.

---

