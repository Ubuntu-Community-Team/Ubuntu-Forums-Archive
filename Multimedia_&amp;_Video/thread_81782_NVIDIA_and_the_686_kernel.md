---
title: "NVIDIA and the 686 kernel"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by dhess31 on 2005-10-25
OK.  How EXACTLY do you get the binary NVIDIA driver to work with the 686 kernel?  I uninstalled all of the 386 kernel stuff, and put the 686 stuff on.  Worked fine.  But when I go to select the glx package, it has dependencies for the 386 kernel.  So when I reboot, ONLY the 386 kernel has the binary module.  Now, I've read the other threads about this, but couldn't seem to get it to work.   Any ideas here?

Don

---

### Post by mikeyman on 2005-10-26
You have to load the restricted modules for the kernel in question. Enabling Universe/Multiverse repositories in synaptic will display this option.

---

### Post by dhess31 on 2005-10-28
OK.  I did this, but now when I try to load X on the 686 kernel, I get an X error staing that the driver version and kernal module version are different.  It works fine under the 386 kernel.  Any ideas here?

Don

---

### Post by pokeroo on 2005-10-28
I have an NVIDIA GeForce FX 5600 (from MSI) and I installed the 2.6.12-9-686-smp kernel, the kernel headers and restricted modules.

I comipled the 7667 drivers from nVidia's website with gcc-3.4 (export CC=gcc-3.4) and changed xorg.conf (remove dri/GLcore and use nvidia instead of nv).

First it didn't work but then I removed the restricted modules (I'll have to double-check this once I get home) and recompiled the drivers. Also, I'm running Kubuntu 5.10 and I removed any nvidia related stuff from Adept that came with the distribution.

If you need more details I can post it when I get home tonight. Hope this helps.

---

### Post by dhess31 on 2005-10-28
I have actually done a compile from the Nvidia site, I was just hoping to get it working through synaptic.  It's no big deal, I can do it that way instead I guess.

Thanks,

Don

---

### Post by rjwood on 2005-10-28
[quote=dhess31]OK. I did this, but now when I try to load X on the 686 kernel, I get an X error staing that the driver version and kernal module version are different. It works fine under the 386 kernel. Any ideas here?

Don[/quote]

If you continue to have problems click on the link in my signature that ends in nvidia-look at that thread or ask tseliot he is very knowledgeable with this.

I hope this helps

---

### Post by dhess31 on 2005-10-29
OK.  Thanks for the link.

Don

---

### Post by dhess31 on 2005-10-29
Strangely enough, I got this to work through synaptic this time.
I un-installed all of the 686 kernel packages, then un-installed all of the nvidia stuff.  I then re-installed the 686 kernel packages, then re-installed the nvidia stuff.  This time, it worked like a champ.  Not too sure what was different, but I got it to work following the steps above.

Don

---

### Post by rjwood on 2005-10-29
[quote=dhess31]Strangely enough, I got this to work through synaptic this time.
I un-installed all of the 686 kernel packages, then un-installed all of the nvidia stuff. I then re-installed the 686 kernel packages, then re-installed the nvidia stuff. This time, it worked like a champ. Not too sure what was different, but I got it to work following the steps above.

Don[/quote]

Alright then! :KS:KS

---

