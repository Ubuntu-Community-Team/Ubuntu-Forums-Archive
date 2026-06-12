---
title: "Problem with Nforce 3 and ati 9600"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by ahil4o on 2006-02-25
Hi guys. I'm new to Ubuntu and I really like it. Today I tried to isntall Ubuntu to a friend of mine his system specs are:
Athlon 64 2800+
Gigabyte Nforce 3 motherboard
Ati Radeon 9600
1 gb ram
I installed it and everything went ok but when the x server starts the computer freezes. I went into recovery mode and tried all kinds of drivers and x server configurations but nothing worked can you help me please?

---

### Post by procras on 2006-02-25
Check to see which driver X is trying to use.
The simplest is vesa and will work with most hardware.

Try to boot into a console instead of X and look at the xserver settings in 
/etc/X11/Xorg.conf

The installer asks you which Xserver to use and you can select ati radeon or vesa and any of them should work.

When you are more familiar you may want to try the ati propriety driver fglrx

---

