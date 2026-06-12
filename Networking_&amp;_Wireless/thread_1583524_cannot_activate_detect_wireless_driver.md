---
title: "cannot activate detect wireless driver"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by abhiduke on 2010-09-28
I installed ubuntu 10.04 alternate version recently. I am able to install broadcom STA wireless driver for model 4321. Even if it is listed under System>Hardware Driver, it gives me an error when I try to activate it. It asks me to read the file var/log/jockey.log. 
 
I read the file and i found this:
 
/sys/module/wl/drivers does not exist, cannot rebind wl drivers.
 
BroadcomWLHandler Enabled(). knod disabled, bcm43xx: blacklisted, b43: blacklisted, b43: blacklisted.

---

### Post by bkratz on 2010-09-28
Sorry to ask the obvious question, but you did have it plugged into a wired internet connection when you attempted to activate the driver-right? It has to do some downloading.

---

### Post by abhiduke on 2010-09-29
Yes i tried that already, it is giving me the same error, here is what the jockey.log file reads:

2010-09-30 01:28:34,767 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-09-30 01:28:34,813 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-09-30 01:28:42,762 DEBUG: nvidia_173 is not the alternative in use
2010-09-30 01:28:42,905 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-09-30 01:28:43,238 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-09-30 01:28:43,445 DEBUG: nvidia_173 is not the alternative in use
2010-09-30 01:28:43,566 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by bkratz on 2010-09-29
Possible solutions exist in posts 2 and 3 of this thread

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)

---

### Post by abhiduke on 2010-09-30
Well i did something else which made my wifi work. i had installed kernel 2.6.32-25 (before that i had 2.6.32-24), i removed the kernel 2.6.32-25 and its headers, and restarted my system. then i installed modaliases for broadcom wireless, then i checked system>Administration>hardware drivers, and i activated the broadcom sta driver. 

It got activated i was able to connect to Internet.

and my graphics card started working too( i check this by opening the terminal, the terminal for ubuntu 10.04 is slightly transparent, and images behind the terminal can be seen vaguely if the graphics card is enabled).

However there is another problem, each time i restart my system, the wireless doesn't seem to work. so i checked it at system>Administration>hardware drivers, it says that 

broadcom sta wireless driver is activated, currently not in use, 

so each time i restart my system, i had to remove and activate this driver for using wireless.

is there a solution to this problem, can any one help me.

---

### Post by abhiduke on 2010-09-30
Well before i could wait for someone to reply, i searched and came across with this solution which is working perfectly even after i restart.

> **bkratz said:**
> you might want to look through this for information

[http://97.95.43.80:10080/580/](http://97.95.43.80:10080/580/)

---

