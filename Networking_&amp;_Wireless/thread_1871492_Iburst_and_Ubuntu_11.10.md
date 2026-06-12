---
title: "Iburst and Ubuntu 11.10"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by DocMSK on 2011-10-29
Hello,

I am using Ubuntu 11.10.

I also have an [iBurst]("http://goo.gl/PnvVS") account that I access with an [iBurst USB modem]("http://goo.gl/X70M8"). Simply iBurst is a wireless internet service in a number of countries.

I used to use the Iburst USB modem to access the internet on older releases of Ubuntu.

[Sourceforge]("http://goo.gl/SZqFG") has the Ubuntu iBurst drivers but they are for an older version of the kernel (36).

I am relatively inexperienced with Linux/Ubuntu.

1. Has anyone been able to use iBurst via the USB modem in Ubuntu 11.10?

2. Is it possible to compile the drivers which are for an older kernel version to work with Ubuntu 11.10?

Any help greatly appreciated.

Thank you.

---

### Post by lost.soul on 2011-11-20
Hey, 

I have the exact same problem, the drivers were not compiled for the new kernel =( 

However, it seems that they are working on it (Only very slowly) based on the link below:

[http://sourceforge.net/tracker/index.php?func=detail&aid=3409443&group_id=138984&atid=742189](http://sourceforge.net/tracker/index.php?func=detail&aid=3409443&group_id=138984&atid=742189) 

however it has been a month since the last update :/

---

### Post by Deep Overload on 2011-12-08
Hi, 

To allow the drivers to compile for the usb modem:

Comment out "obj-m += ib-pcmcia.o" in the Makefile on line 13 - we dont want to compile for that interface.

then change line 60 in ib-net.c to:

spinlock_t ib_lock = __SPIN_LOCK_UNLOCKED(old_style_spin_init);


Then in the terminal do: sudo make
There you go, the driver is now compiling.

Then install iburst with: sudo make install

Cheers
Deep Overload

---

