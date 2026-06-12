---
title: "Changed motherboard - network not working"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by 1915 on 2006-07-05
So my old Asus K8S-MX mobo burned, I installed the new Asus K8V-X today and ubuntu boots up as expected, but network wont load.

dmesg | grep "eth0" says:

> eth0: VIA Rhine II at 0x1a000, 00:15:f2:43:73:0b, IRQ 195
eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.


The drivers on the mobo-cd is sk98lin. I've tried both:

modprobe sk98lin
and
modprobe via-rhine

but I still get the same message when doing /etc/init.d/networking restart:

> SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.


And that marks the end of my linux-skills.. help?

uname -a
> 
Linux xxxx 2.6.15.-23-386 #1 PREEMPT <date and so on> UT 2006 i686 GNU/Linux"

---

### Post by 1915 on 2006-07-05
After some searching and tweaking I finally found out that my mobo network is linked to eth1. So "ifup eth1" worked with no problems.

How do I set this up so eth1 will be eth0 instead?

---

