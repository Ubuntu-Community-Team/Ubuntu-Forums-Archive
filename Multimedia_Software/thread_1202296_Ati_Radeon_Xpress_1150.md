---
title: "Ati Radeon Xpress 1150"
date: 2009-07-02
forum: Multimedia Software
---

### Post by Sankou on 2009-07-02
I need ATI Radeon Xpress 1150 drivers. I've checked everywhere, nothing seems to be working.

---

### Post by tuku on 2009-07-23
I have exactly the same problem. There are no drivers on the AMD/ATI site. Please post any solutions.

---

### Post by steefjeqv on 2009-07-24
Hi,

You shouldn't need these official ATI drivers, also called fglrx.

Ubuntu Jaunty uses the open-source xorg-xserver-video-ati driver by default. This should work.

If you experience any troubles you can update these drivers using Tormod Volden's ppa :

[https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/~tormodvolden/+archive/ppa") 

Greetings,
Steven

---

### Post by steefjeqv on 2009-07-25
Hi,

Took a look at this thread. You don't have to read everything, just post nr. 32. This is a small how to which upgrades your X (graphic environment).
Caution : if you've recently tried installing fglrx (ati closed source driver), be sure it's completely removed from your system.

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx 

[http://ubuntuforums.org/showthread.php?p=7674928#post7674928]("http://ubuntuforums.org/showthread.php?p=7674928#post7674928")

Greetings,
Steven

---

