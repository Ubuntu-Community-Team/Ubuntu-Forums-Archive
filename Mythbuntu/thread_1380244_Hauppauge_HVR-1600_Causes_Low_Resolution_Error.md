---
title: "Hauppauge HVR-1600 Causes Low Resolution Error"
date: 2010-01-13
forum: Mythbuntu
---

### Post by jquintana on 2010-01-13
I bought an HVR-1600 yesterday and it has caused all kinds of problems. When I put the card in and boot the system I get an error saying something about Low Resolution Mode and am not able to boot into Mythbuntu.

I took the card out and everything works fine again.

Any suggestions are greatly appreciated!

---

### Post by klc5555 on 2010-01-13
> **jquintana said:**
> I bought an HVR-1600 yesterday and it has caused all kinds of problems. When I put the card in and boot the system I get an error saying something about Low Resolution Mode and am not able to boot into Mythbuntu.

I took the card out and everything works fine again.

Any suggestions are greatly appreciated!

Standard virtual memory allocation error when loading the cx18 module with the NVidia drivers. It's easily fixed by adding the vmalloc=256M parameter to grub. Discussed in numerous threads in this forum, and also on the wiki page here (updated for Grub2): 

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Workaround_for_NVIDIA_restricted_driver_users](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Workaround_for_NVIDIA_restricted_driver_users)

---

### Post by jquintana on 2010-01-13
Thanks -- that did the trick!

---

