---
title: "No S-Video on Radeon 9100 IGP"
date: 2013-10-18
forum: Multimedia Software
---

### Post by tom_hurst on 2013-10-18
OK, this is seriously starting to drive me crazy...

I've been trying to activate the S-Video output on my laptop, with barely any success.
I'm using a Radeon Mobility 9100 IGP on Ubuntu 10.04.3 with kernel 2.6.32-22 (also tried 3.0.0-32).

I can add a new mode using xrandr, but when I try *xrandr --output S-video --mode 800x600* it still says "disconnected".
changing *load_detection* doesn't do anything, either.

When I boot it up using the vesa driver, xrandr won't even list the S-Video output.
*lspci -v* says it's using kernel modules radeon and radeonfb.

The weird thing, though: if I choose kernel 2.6.31.20 from grub, I can activate the S-Video out. Only in black & white, though, PAL/NTSC change doesn't affect that. *lspci -v* still says it's using modules radeon and radeonfb.

 Is there any hope for solving my problem with this setup, i.e. without having to upgrade everything?
Do you need more info?

Thanks in advance!

---

### Post by theiron on 2013-10-18
I suggest that you upgrade to at least Ubuntu 12.04 in order to take advantage of the LTS.

---

