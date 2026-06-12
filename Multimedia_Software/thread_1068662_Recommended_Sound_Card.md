---
title: "Recommended Sound Card"
date: 2009-02-13
forum: Multimedia Software
---

### Post by mawiles on 2009-02-13
After years of never getting on board sound to operate properly in any distro (this includes Mic), I switched to USB.  However, this is a soft solution, and I desire to use hardware when possible with this next build and install.  Please recommend an available sound card that has full support within latest Ubuntu and kernal.  It is a sad state of affairs that after this much time, support for audio is in such a disarray.

---

### Post by Mud.Knee.Havoc on 2009-02-13
> **mawiles said:**
> After years of never getting on board sound to operate properly in any distro (this includes Mic), 

Out of maybe 20 systems that I've used linux on, I've never had a problem with sound - with the exception of adding a line to a config file for a Dell Mini 9.  I always thought that sound and network interfaces was linux's strength.

The problem with the mic is usually that it's muted in alsamixer.  This is an easy fix if it ever does appear. 

That said, I seem to usually buy Asus motherboards, and any of their onboard audio chipsets have always been great with Linux.

EDIT: You aren't still running 6.06, are you?  A lot has changed in the nearly three years since it's been released.  Hardware compatibility increases with each release.  That could very well be part of your problem.

---

### Post by glotz on 2009-02-13
Do a
```
sudo lshw -class multimedia
```
Let's see if we can make it work for you.

I've never had any audio problems either. I once had to add a module for my old Sound Blaster card but that's it and it took me like 5 minutes to figure out.

---

