---
title: "Nvidia Drivers not loading"
date: 2011-03-28
forum: Multimedia Software
---

### Post by hdrip on 2011-03-28
Ok so I've been a long time Windows user and I finally decided to make the switch to Ubuntu.  I first installed it on my laptop and only had a few minor issues which were solved with the power of Google.  I then decided I would install it on my main PC.  Everything worked great until I tried to install the NVidia drivers....

I've tried the restricted drivers, the repository method and manually installing the drivers downloaded right from NVidia.  All end with the same problem.  After the GRUB menu it boots right into TTY1.  If I edit the xorg.conf file and change the driver name from nvidia to nv, I get the GUI back.  I suspect because it's defaulting to the standard video controller.

When I try to access the NVidia settings it tells me that the driver is not loaded and to run sudo nivdia-xconfig.  Which again puts me back to TTY1.  A vicious cycle right?

I've even tried bypassing the splash screen to no avail.

Any ideas would be greatly appreciated.  Please don't make me go back to Windows!

Thanks

---

### Post by cbowman57 on 2011-03-28
What version of Ubuntu are you running?

---

### Post by hdrip on 2011-03-28
Turns out my video capture card was wreaking all the havoc.  Removed the card and Ubuntu booted into GUI no problem.

It's Ubuntu 10.10 btw.

---

### Post by cbowman57 on 2011-03-28
Good news.  I was just curious because some of the early Nvidia drivers on 11.04 were having similar problems.

---

