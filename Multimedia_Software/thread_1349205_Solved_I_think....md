---
title: "Solved I think..."
date: 2009-12-08
forum: Multimedia Software
---

### Post by Isaacgallegos on 2009-12-08
> Linux support for the WinTV-HVR-1250 and WinTV-HVR-1800 is in the current kernel 2.6.25 release.
ubuntu 9.10 has 2.6.31-16-generic. Do I downgrade to an older version of ubuntu? Or can I **$ sudo apt-get install linux-image-2.6.xx-yy-generic** to get the correct one? 
I'm trying this out tomorrow. So let me know your thoughts or any advice that might help this issue finally be solved! Thanks!

---

### Post by LuisGMarine on 2009-12-09
No you don't need to downgrade to have that option.  From now on every kernel since 2.6.25 is going to have support for WinTV.  So any version after 2.6.25 is going to support it, unless they specificity state that they are removing support from the kernel.

---

### Post by Teamgeist on 2009-12-14
To get the card running in Ubuntu you might have to install the package **linux-firmware-nonfree**.

You can do this in Synaptic or via **sudo aptitude install linux-firmware-nonfree**.

Reboot your computer afterwards.

---

