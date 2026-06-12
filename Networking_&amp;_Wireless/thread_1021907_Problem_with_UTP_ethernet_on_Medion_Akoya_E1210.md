---
title: "Problem with UTP ethernet on Medion Akoya E1210"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by aussiedaddy on 2008-12-26
I have installed Ubuntu on a Medion Akoya E1210 using wubi.  I had some issues trying to get the install to work - it seemed to be hanging when configuring apt.  I got over that by pulling the ethernet cable.

I then had trouble downloading the package information after adding the additional (universe and multiverse) software sources.  The network connection would work for a short burst and then slow down to almost nothing or stop altogether.  I managed to get around this (whilst getting somewhat frustrated) by stopping and restarting sudo apt-get update.

Now I need to install a number of packages (with quite a few dependancies) such as glade-2, libglade2-dev, libgtk2.0-dev etc.  The same thing is happening only worse.

Has anyone else struck this problem?  Any suggestions as to what I can do to fix it?  Or is there some workaround so I can install the required packages off a USB drive perhaps?

Thanks for reading my post

---

### Post by aussiedaddy on 2008-12-26
I can throw some light on this problem.  I am getting billions of dropped packets (as reported by ifconfig).  So I guess I have a driver or a hardware problem.  Driver is r8169.

---

### Post by aussiedaddy on 2008-12-26
Having done some more reading I gather I may need to switch to the r8101 driver, but I haven't been able to either download it or activate it.  Help please!

---

