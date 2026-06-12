---
title: "i915 chipset, stuck in vesa mode"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by Jonne on 2005-10-19
Well, I'm new to Linux, and installing drivers seems to be one of the tasks that aren't very easy to do.

I have this package installed: xserver-xorg-driver-i810, which, according to the description, should contain the drivers for i915.

Now, the problems I'm having:
-DVI doesn't work, my LCD screen is connected to VGA (not a big problem, I can live with that ;) )
-no hardware acceleration (I'd like stuff to be a little snappier, and I'd like some more eyecandy on my desktop, like real transparency. I'd like to try some 3D games too on Linux, which seems impossible with the VESA driver.)

If I edit xorg.conf to change "vesa" to "i810" or "i915", it won't start X. Only vesa seems to work.

If you need more info, I can provide that for you.

edit: I guess I typed "i815" or something. It worked this time, now that I've tried again.

---

### Post by shof2k on 2005-11-17
Try installing the i180, i915, and common modules from freedesktop.org.  These are more recent than the ubuntu versions.  You may need to install them in single user mode to fully work.

Good luck

---

