---
title: "nautilus and desktop icons"
date: 2010-12-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bladerunner6 on 2010-12-19
i can only get natty to load up in classic desktop, but then i am missing my desktop icons, the panels load up.

if i do sudo killall -1 nautilus, then the desktop icons load up.
how do i make this permanent

---

### Post by MacUntu on 2010-12-19
> **bladerunner6 said:**
> how do i make this permanent

By waiting for developers to fix the problem. ;)

---

### Post by garvinrick4 on 2010-12-19
In unity interface do you have:
```
ccsm
```
and check the unity plugins

---

### Post by bladerunner6 on 2010-12-19
i think the nvidia-173 drivers dont work too well with unity,
even in classic it had issues, back to nouveau and 2d decorator

---

### Post by cariboo on 2010-12-19
What model nvidia graphics card are you using, as you may be using the wrong driver.

---

### Post by bladerunner6 on 2010-12-20
FX5200

128mb gfx mem,

---

### Post by ronacc on 2010-12-20
I have the same card in one box , 173 is the correct driver for it .

---

### Post by efflandt on 2010-12-21
Even with nvidia-current (260.19.21) I often end up with some sort of default gray upper right panel applet/indicator icons, plain Unity icons, and default Nautilus icons.  Only rarely do I end up with fancy icons.  But applets and icons rarely work initially, so I usually have to do either "unity --reset" or "compiz --replace" to get those working (or sometimes "sudo restart gdm" from console), and then fancy icons/applets revert to simple ones.

Or in Classic or Failsafe I end up with dirty gray panels and simple icons instead of dark Maverick like panels and applets/indicators.  So it is not just older nvidia drivers that have issues with natty at this point of development.

**garvinrick4** what do you specifically mean by "and check the unity plugins" (which would you check or uncheck to help)?

---

### Post by Harry33 on 2010-12-21
According to Nvidia Corporation, FX 5200 series should use 173.14.28 (stable) driver, not the later ones.

---

### Post by bladerunner6 on 2010-12-28
anyone had any success with unity and nvidia-173 gpus

---

### Post by cariboo on 2010-12-28
Have you tried the nouveau drivers with libgl1-mesa-dri-experimental. I have it running on a system with an AGP 6600GT, with zero problems.

---

