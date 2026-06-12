---
title: "lower glxgears score than in Gentoo, drivers?"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by gnychis on 2007-06-13
Hey all,

I'm not trying to argue performance between Gentoo and Ubuntu and the whole compile from source approach.  I used Gentoo for 3 years and just tossed it out the window for Ubuntu because I could no longer stand building from source.

However I have a Thinkpad x60s laptop which has Intel Graphics Media Accelerator 950.  I believe the proper thing to do is to use the i810 driver, so I "sudo dpkg-reconfigure xserver-xorg" and went through the options... and selected i810.

I'm getting around half of the glxgears score I used to get with xorg and this laptop.  I used to get a score around 1100, now I'm getting around 650.

I was just wondering if there is anything else I should do that might help.

Thanks!
George

---

### Post by Syke on 2007-06-14
I don't know if it will affect your performance, but you probably should be using the "-intel" driver, not the "i810" driver. It's the newer driver.

---

### Post by gnychis on 2007-06-14
oh really?  thanks :)

whats the ubuntu way of doing this?  the same method i did previously to switch to i810?

---

