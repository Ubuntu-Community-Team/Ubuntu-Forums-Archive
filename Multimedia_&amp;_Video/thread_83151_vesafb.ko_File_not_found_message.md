---
title: "vesafb.ko File not found message"
date: 2005-10-28
forum: Multimedia &amp; Video
---

### Post by lorenco on 2005-10-28
I am running Kubuntu Breezy and ever since my first reboot after the install I get a message right upfront:
can not insmod: lib/mod/vesafb.ko no such file... or something.:confused: 

It is not really causing any problems as far as I can see?

vga=0x342 still works..

---

### Post by Abel Hernandez Zanatta on 2005-11-08
Well I had the same problem about the vesafb.ko not found but I solved the problem taking a look at bugzilla.

You can take a look at bug 17331:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17331](http://bugzilla.ubuntu.com/show_bug.cgi?id=17331)

Basically you need to add a line to the usplash script and run
dpkg-reconconfigure linux-image...............

---

