---
title: "Lost hi-resolution in Ubuntu 32-bit 9.10"
date: 2010-02-22
forum: Multimedia Software
---

### Post by BillDad on 2010-02-22
Hello. I installed Ubuntu 32-bit on my system and it correctly recognized the display size as 1680x1050. Unfortunately, during a later log-in (today), the resolution dropped back to 800x600 with no apparent way of changing it back. This happened for no apparent reason.

When this happened with fedora I gave the command

cvt -v 1680x1050 60

ands put the result in my xorg.conf file. 

By default, I noticed, Ubuntu doesn't have an xorg.conf file.

Is there a way to return to 1680x1050 resolution?

Thanks people.

Bill

---

### Post by ldso on 2010-02-22
By chance, do you know what X server you are running?  Do you have an nvidia or ati card?  It may be that a software update has you running a different X server than you used to run, and it doesn't offer as many settings.  I am old school, I usually futz around hand-editing xorg.conf.  Sometimes I use xorgconfig or X  -configure (or is it --configure)?

Hope that helps,
ldso

---

### Post by BillDad on 2010-03-01
Hello. 

My graphics card is an nVidia 6500 gForce 430. On Fedora it runs the nVidia "noveau" driver (but it worked just as well with the standard "nv" driver.

I had the resolution problem (not being able to get anything beyond 800x600) on Fedora, but I fixed by using the command:

# cvt -v 1680 1050 60

and put the resulting output in my xorg.conf file in the monitor section. After that, no problems. I tried the same thing with Ubuntu, but Xwindows choked on it (even though both use the Xorg server).

I am now using Ununtu/Gnome with 1680x1050. I erased my xorg.conf file, and the default seems to be spot on, 1680x1050, The reason that it is still an issue is that, with Fedora, I tried the same thing, but when I occassionally had to disconnect the monitor and reconnected it, it defaulted back to 800x600.

I am looking for a way to avoid this happening in Ubuntu, althouigvh hopefully it is moot point.

---

