---
title: "[SOLVED] Mythbuntu blank screen and 100% CPU"
date: 2007-12-12
forum: Mythbuntu
---

### Post by LeastCriminal on 2007-12-12
Hi,

I am having problems installing Mythbuntu on a frontend machine.  The machine has an NVidia GeForce4 MX 4000 video card with TV-out.  I am using the nvidia-glx "nvidia" driver, as suggested by the restricted driver manager.  The installation went ok, and the graphics output looks right on both the TV and VGA output through the "Mythbuntu" screen with the blue progress bar.  Once the bar is filled and it starts X, the VGA monitor goes black and the TV shows streaks of garbage.  I can ssh into the machine, and it shows Xorg is consuming close to 100% of CPU.

This machine used to be an Ubuntu 7.04 machine and worked perfectly, so I know the hardware is fine.  I tried the nvidia-glx-new and  nvidia-glx-legacy, and neither worked any better.  The open source "nv" driver works perfectly for the VGA monitor, but has no TV-out, which is a deal breaker.

Any suggestions?  This looks to me like a driver problem; probably one that someone else has had.

Thanks!

---

### Post by mongrol on 2008-02-05
I'm having the exact same problem after a fresh myth build with mythbuntu (previously fiesty). Has anyone seen this and know a fix?

---

### Post by superm1 on 2008-02-05
Start out in the log /var/log/Xorg.0.log

Post it here if nothing it standing out to you.

---

### Post by mongrol on 2008-02-06
I've changed the nvidia drive from nvidia-glx-new to the older nvidia-glx (I have a Gefore 6800GT). The hanging has now stopped.

---

