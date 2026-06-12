---
title: "Compaq Presario F755US default resolution problem"
date: 2009-09-27
forum: Multimedia Software
---

### Post by Goshe on 2009-09-27
I've installed Ubuntu 9.04 on compaq presario f755us notebook with geforce 7000m/nforce610m and after installing the proper Nvidia graphic driver I can't set default resolution for the screen.When the configuration is saved in xorg.conf on the next restart the Xserver is corrupted and I have to change to default(low-level) graphic and start nvidia-xconfig,restart the X server and for every starting on the nootebook I must change the resolution manually.

Anyone can help?

---

### Post by alpha4189 on 2009-09-27
I had the same problem (same notebook), but I'm using the "kubuntu" distro. I'm new to this, but in case that doesn't make much of a difference, what I did was alt f2, type in hardware drivers, and use that utility, which automatically detected my proprietary driver, and I activated it. After a restart, problem solved.


Hope this helps.

---

### Post by Goshe on 2009-09-28
Do you mean "hardware drivers" as string or the name of the driver's package

---

