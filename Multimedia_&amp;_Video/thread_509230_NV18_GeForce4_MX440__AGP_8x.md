---
title: "NV18 GeForce4 MX440  AGP 8x"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by mrga on 2007-07-25
Ok i installed everything, nvidia-glx, nvidia-glx-dev, nvidia-kernel-source, new kernel
modinfo: could not open /lib/modules/2.6.20-16-generic/volatile/nvidia.ko: No such file or directory
 

I change "nv" to "nvidia" but stiil after i reboot i get error that X can't start, so i need to change xconf and "nvidia"
back to "nv".

I searched and see that i need to ad more lines ,but i don't know what in xconf.

Thank you!

P.S Ubuntu Feisty Fawn 7.04

---

### Post by madmetal on 2007-07-26
i think for this card you should install nvidia-legacy driver since it old..
how did you install nvidia-glx?

---

### Post by serfcx on 2007-07-27
I have the same card under Feisty and used envy to install the nvidia driver which has installed NV17

Try out envy ?

---

### Post by mrga on 2007-08-14
OK, i have reinstalled computer, and now i want to make all right.
So bery wiki is defaced, any good link what to do.

---

### Post by playing_with_matches on 2007-09-09
> i think for this card you should install nvidia-legacy driver since it old..
how did you install nvidia-glx? 

I actually have the same card, and I did not use the legacy drivers...  I installed glx via the wiki, and didn't really have a problem, except I can't get TV-OUT to work on it, but legacy is not needed.  Although one time when I downloaded the auto-update on the drivers, it kinda killed my system...

---

