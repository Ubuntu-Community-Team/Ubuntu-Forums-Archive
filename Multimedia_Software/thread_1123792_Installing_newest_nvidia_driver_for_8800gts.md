---
title: "Installing newest nvidia driver for 8800gts"
date: 2009-04-12
forum: Multimedia Software
---

### Post by burntresistor on 2009-04-12
I downloaded the pkg for the 8 series 64 bit 8.10 started installing and its telling me to turn off the xserver in the error message.  Do I follow directions on the nvidia site or since they dont be made specifically for unbuntu. what is the best way to install it ?

---

### Post by vancedus on 2009-04-12
Have you tried using Envy to get your drivers?  It is in the repositories.  Easy, works well.

---

### Post by overdrank on 2009-04-12
> **burntresistor said:**
> I downloaded the pkg for the 8 series 64 bit 8.10 started installing and its telling me to turn off the xserver in the error message.  Do I follow directions on the nvidia site or since they dont be made specifically for unbuntu. what is the best way to install it ?

When in the command line you can use this command to stop x ```
sudo /etc/init.d/gdm stop

``` If you are using gnome, as vancedus stated envy may make things easier for you.
Moved to Multimedia & Video

---

### Post by RedSingularity on 2009-04-12
Why not get it through the Package manager?  Its much easier.

---

### Post by burntresistor on 2009-04-13
i dont believe the one in packet manager is the most current  release

---

### Post by RedSingularity on 2009-04-13
It has the nvidia-glx-180

Is that the one your looking for?

---

