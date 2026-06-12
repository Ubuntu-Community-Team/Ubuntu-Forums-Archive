---
title: "nvidia drivers"
date: 2005-12-13
forum: Multimedia &amp; Video
---

### Post by kg4gyt on 2005-12-13
I installed the NVIDIA drivers on my box, and now when I try to switch to another terminal (Ctrl-Alt-F?) I get a screen of random pixels when I'm on an analog cable (Digital just gives a monitor no signal error) and the system can't recover from it when switching back. I'm using the 7667 drivers from nvidia. Any thoughts?

---

### Post by 23meg on 2005-12-13
I get a blank screen on my laptop with Nvidia drivers, and I've found out that when I temporarily disable usplash, the problem is gone. See if the same is true for you. I'm looking for a permanent solution to this as well.

---

### Post by kg4gyt on 2005-12-14
Disabling usplash from /boot/grub/menu.lst seemed to fix everything.

Thanks

---

