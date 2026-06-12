---
title: "ethX device changes with mac address... annoying"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by i.r.id10t on 2009-05-21
Got an issue (has been one for a while now... several ubuntu releases in fact) that isn't really a bug but is a major annoyance.

I teach a Linux class in a lab.  Students have USB drives that they install Ubuntu to (we're on 9.04 this summer).

However, when they change seats to a different computer, their network device changes from eth0 to eth1.  Change seats again, again its a new MAC address, so eth2 now.  And so on.

This also happens with VMWare "machines" when they are run in a different install of VMWare.

Very annoying.

How can we change this?  I'd like it to work "the old way" where the first identified NIC (by built in kernel support, loading a module, and then position on PCI bus) is always eth0, the second is eth1, and so on.

Thanks

---

### Post by Iowan on 2009-05-21
It's not necessarily a fix, but check /etc/udev/rules.d/70-persistent-net.rules ... might be able to "clean up" the extras there.

---

