---
title: "Low graphics mode error but graphics works fine?"
date: 2009-12-06
forum: Multimedia Software
---

### Post by Entropy512 on 2009-12-06
I'm running Kubuntu 9.10 with the 190.42 Nvidia drivers from the repository at [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

Things have been working well for a while, but after applying some updates two days ago (I don't remember which, although a new kernel was added), I get a "low graphics mode" error on startup.  This occurs even if I boot a kernel that was working fine before.

However, if I choose the option in the error dialog to go to a console login, I don't get dropped to the console.  KDM comes up instead, and Xorg/KDM/KDE is 100% functional, including VDPAU hardware acceleration!

So why am I getting a "low graphics mode" error when it seems like my graphics configuration is fine?  I'm not sure where to even start trying to debug this.

---

### Post by cnja on 2009-12-07
I've got the same issues,

Dell Laptop CPX-j with ATI Mobility video.

sending a bug report to the guru's, hopefully they can figure out what happened.

---

### Post by fxo on 2009-12-07
Same behaviour in my laptop with a Mobility Radeon HD 3400 card. It seem to be a problem with kdm, I have try to install gdm and run kdm destok session and all seem to work fine.
Fxo

---

### Post by Entropy512 on 2009-12-09
Well, at least that means my use of the Avenard repo is not the cause, since that's only for NVidia + MythTV users.

---

### Post by cnja on 2009-12-10
after some head scratching, and much reading... I decided to just reinstall all the video drivers and software for my laptop, ATI and MACH64.  did a reboot, and all is good.

---

