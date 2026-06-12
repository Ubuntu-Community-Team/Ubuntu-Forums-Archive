---
title: "XGL/Compiz doesn't work after new kernel installation"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by playalistic on 2006-08-23
Hi.
I had previously installed XGL/Compiz on Ubuntu 6.06 with the 386 kernel. I've just upgraded to the 686 kernel and upon rebooting XGL/Compiz isn't working anymore. Does anyone have any idea what I need to do? Is it a complete reinstallation or simple change? Thanks!!!

---

### Post by reacocard on 2006-08-23
it's probably just your graphics drivers. reinstall your ati or nvidia drivers, and the problem should be fixed.

---

### Post by playalistic on 2006-08-29
I've tried reinstalling the ATI drivers but it seems as though i've totally hosed everything now. Should I expect to have these problems everytime I do a kernel upgrade?
I'm going to do a clean install and kernel upgrade before installing XGL/Compiz again but if this is going to happen everytime a new kernel is released I probably won't bother for now :)

---

### Post by reacocard on 2006-08-29
It shouldn't happen unless something dependent on the kernel version is not updated with the kernel, which is usually drivers. I'm afraid idk much about using ATI with compiz, since I have an Intel card. But I do have to update DRI everytime I update the kernel, so if you use DRI you could try updating it.

---

