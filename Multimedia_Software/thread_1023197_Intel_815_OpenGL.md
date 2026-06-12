---
title: "Intel 815 OpenGL"
date: 2008-12-27
forum: Multimedia Software
---

### Post by raptorpenguin on 2008-12-27
Hello all,

I have an old Compaq running Breezy Badger (the only version that runs fast enough on a computer as old as mine.), with an Intel 815 series graphics card.

I was trying to install Frets On Fire (a Guitar Hero like game) on my computer, and when I run it from the command line, it gives me a bunch of random looking output ended by:

"Import Error: No module named OpenGL.GL"

Then, I tried running glxinfo, and it said "Direct rendering: No". After that, I tried Google searching "Intel 815 opengl", and I clicked on the Intel website:

[http://support.intel.com/support/graphics/intel815/sb/CS-004083.htm](http://support.intel.com/support/graphics/intel815/sb/CS-004083.htm)

, which says that my card supports OpenGL.
Also, I can run 3D graphics when booted under Windows.

I am clueless here, any ideas?

---

### Post by itix on 2008-12-28
For some reason, FoF (Frets on Fire) can't find the OpenGL kernel module. Have you tried to upgrade OpenGL manually (since I suppose that the repositories are not open for you with breezy badger)?

---

### Post by raptorpenguin on 2008-12-31
No, I have not tried updating OpenGL. Do you know where I would find the package to update it?

---

### Post by nicefinger on 2008-12-31
Could it be as with i810, that 3D is only supported if You use 16-bit colour?

---

### Post by itix on 2008-12-31
Hmmm... I have recently learnt that Open GL can't be updated so I'm afraid that won't be the solution to this problem. Some graphics cards like ATI radeon has really old versions of Open GL.

Yours however is an intel-card so that shouldn't be a problem.

Have you tried nicefingers suggestion?

---

### Post by raptorpenguin on 2008-12-31
> **nicefinger said:**
> Could it be as with i810, that 3D is only supported if You use 16-bit colour?

This very well could be it. I'll give it a try.

---

### Post by raptorpenguin on 2008-12-31
Hmm. Changing color depth didn't seem to do the trick. However, while I was configuring my xorg.conf file to change default color depth, I noticed an option for loading other graphics modules. Does the "dbe" module have to do anything with this?

---

