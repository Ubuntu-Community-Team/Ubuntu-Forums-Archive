---
title: "Please any body help me patch xorg"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by krajok on 2006-09-03
I can't use my Radeon Xpress 1150 VGA.
I did a research on google search all the day and found that my problem could be xorg bug #6377
 - [https://bugs.freedesktop.org/show_bug.cgi?id=6377](https://bugs.freedesktop.org/show_bug.cgi?id=6377)
There is a patch for this bug attached in above URL but the problem is I dont know how to use it.

Currently my xorg-server is 1.0.2-0ubuntu10.4

Can someone teach me how to apply this patch please.

---

### Post by krajok on 2006-09-03
I did it.

$ sudo apt-get build-dep xserver-xorg-core
$ sudo apt-get install fakeroot
$ apt-get source xserver-xorg-core
#### I don't know how to use patch, so I edit the file xorg-server-1.0.2/hw/xfree86/os-support/linux/lnx_pci.c manually, then continue with
$ cd xorg-server-1.0.2/
$ dpkg-buildpackage -rfakeroot
$ cd ..
$ sudo dpkg -i xserver-xorg-core_1.0.2-8_amd64.deb
$ sudo /etc/init.d/gdm restart

Then I work. :)

---

### Post by mpastell on 2006-10-17
I had similar problem with my X1300, but I just upgraded to Edgy beta and got the fgrlx drivers from the standard repository working :) My 2 d is working perfectly now, haven't tried the 3d yet.

Matti

---

