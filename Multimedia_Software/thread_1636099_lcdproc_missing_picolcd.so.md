---
title: "lcdproc missing picolcd.so"
date: 2010-12-02
forum: Multimedia Software
---

### Post by AndrewWalker on 2010-12-02
Just in case anyone else has spent ages banging their head against the wall, the picolcd driver in the lcdproc package is missing!
The package in question is lcdproc-0.5.3-0ubuntu2 and the file picolcd.so should be in /usr/lib/lcdproc but is missing even though the picolcd is an option in the daemon. The bug is reported, Bug #483915 but not fixed. Can anyone tell me where I can get a binary of the file to drop in place to see if that is all the problem is?
If possible, can anyone fix and update the package? So far it's unassigned.

---

### Post by frank16 on 2011-01-17
x

---

### Post by frank16 on 2011-01-17
Same problem here.

I solved it by installing lcdproc from synaptic first then downloading the special Ubuntu package from the picolcd.com website:
[http://resources.mini-box.com/online/picolcd/4x20/lcdproc_0.5.3-1_i386.deb](http://resources.mini-box.com/online/picolcd/4x20/lcdproc_0.5.3-1_i386.deb)

Install with sudo dpkg -i package lcdproc_0.5.3-1_i386.deb
(Ofcourse the exact version might be different by now)
Allow the installer to overwrite the old lcdproc settings.

If you had already placed the picolcd in a USB port it wil be up and running immediately after the install. RC.d scripts seem to be in place too, so it should autorun on boot.

I´m using it with Mythtv, so I can select music without turning on the tv.

I don´t know why the ubuntu package doesn´t contain the driver, but it seems to need a special library (from the picolcd guys?).
Maybe there is a maintenance problem in incorporating that into Ubuntu?

Best of luck,
Frank

---

