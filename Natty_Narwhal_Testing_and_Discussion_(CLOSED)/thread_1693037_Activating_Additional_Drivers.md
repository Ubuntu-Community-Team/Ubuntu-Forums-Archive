---
title: "Activating Additional Drivers"
date: 2011-02-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by evworld on 2011-02-22
I running Natty from a usb drive.  When I try to activate Video driver fro the ATI graphics accelerators  I receive a systems error.

System Error: E:Unable to correct problems, you have held broken packages

Any Ideas.

---

### Post by Harry33 on 2011-02-22
> **evworld said:**
> I running Natty from a usb drive.  When I try to activate Video driver fro the ATI graphics accelerators  I receive a systems error.
System Error: E:Unable to correct problems, you have held broken packages
Any Ideas.

Well in this dev forum this issue is dealed in a number of threads.
ATM proprietary drivers (both AMD and NVidia) do not support the new xserver 1.10 rc series. Installing these will break your system.
So ATM you can only use xserver-xorg-video-ati, the open source driver.
Infact they that works quite well, except with the high end Radeon HD6**** series cards.

---

