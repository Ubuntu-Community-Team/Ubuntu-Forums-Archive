---
title: "Netbook Mousepad Issue... No Movement!"
date: 2010-08-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by KdotJ on 2010-08-10
Hey everyone, hope someone can help me out.

I recently upgraded my netbook to Maverick A3 (as an upgrade, not a clean install). My netbook is an HP Mini 210 and has worked great with ubuntu. However, since I installed Maverick, the track pad has had an issue, it will not allow me to right-click. Normal left-click (and tap) work fine, along with movement.

As some background information, I had this issue under Lucid Beta 1 & 2 but by the time of RC1 it was fixed by a simple system update. However, during my use of Lucid Beat 1 & 2, I could remedy the no right-click issue by typing this into the terminal with sudo:

```
echo options psmouse proto=exps => /etc/modprobe.d/psmouse.modprobe
```

After doing so, right-click was possible.

So, I tried to do this is in Maverick A3 to fix the right-click issue (or at least temporarily). However, after doing so and a reboot, now the track pad does not work at all! The mouse pointer appears centre screen as normal when it boots in the GDM, but I cannot move the pointer, nor click anything.

Is there anything I can do? Either to get the mouse working again, or even better, to fix the no right-click issue?


Many thanks

---

### Post by KristinaK on 2010-09-23
is it fixed now?

---

