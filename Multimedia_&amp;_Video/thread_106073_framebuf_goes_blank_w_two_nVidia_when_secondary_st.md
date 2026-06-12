---
title: "framebuf goes blank w/ two nVidia when secondary starts X11"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by blazko on 2005-12-19
Hello all,

I am going nuts right now: I have a system with two nVidia Geforce PCIe 6x cards (6200 and 6600). The primary card is connected via VGA and is configured to use frambuffer at 0x314 (800x600) with vesafb.
The second card is connected via DVI and is used for X11 - in the xorg.conf I specify this card using BusID.

As soon as the second card shows up X11, the framebuffer just stops working. Is there any option to disable this behaviour? I am using the "nvidia" X driver, not "nv" (last does not know about BusID?!?).

Thanks for any hints!
Regards, Timo

---

