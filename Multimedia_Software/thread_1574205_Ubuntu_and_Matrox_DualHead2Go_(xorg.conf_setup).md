---
title: "Ubuntu and Matrox DualHead2Go (xorg.conf setup)"
date: 2010-09-13
forum: Multimedia Software
---

### Post by Cyclops_ on 2010-09-13
Hi all!

I just purchased a Matrox DualHead2Go.  This is a box that creates a dual output from a single output on your video card.

I just plugged it in, and away it goes (working well).

The only thing I would like to figure out is the "Xinerama" effect that it presents.  Since I am splitting a single output from the video card to a dual monitor setup, is there a way to set up two "virtual monitors/screens/whatever on would call them" in the xorg.conf?

I'm using the latest nVidia.

Many thanks for any help!

---

### Post by marfal on 2010-09-24
I'm also using a Matrox Dualhead2go from an older machine and nvidia card (using nvidia driver ver.96). Works out the box, however when displayed across the two screens (2560x1024)the display appears slightly out of focus. If I drop the display resolution down to 1280x1024 (to a single screen)using the "NVIDIA X Server Settings utility" the focus looks fine.
I notice the nvidia utility lists "Matrox (CRT-0 on GPU-0)" not sure why as I have two 20" flat panel monitors.
(ubuntu 10.04)

---

### Post by Cyclops_ on 2010-10-01
Hm...  I'll have to try the lowered resolution.  That will probably help the out-of-focus...
 
Is there anything I can do to be able to use Twinview or Xinerama, but in such a way that I can drag windows across?
 
(Thanks for the reply)

---

