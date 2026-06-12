---
title: "eth0 reassigned"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by marpha on 2009-05-23
I am putting together a small cluster and am using a diskless setup.  I'm using Intrepid Ibex for both server and clients.

I successfully obtain the initramfs via PXE boot via the one of two network cards specified by DHCP. Then, somewhere in the boot process before mounting the NFS file system the interface "eth0" is reassigned to my second NIC upon loading its module.  The OS loads fine, but the second card, which is supposed to have its own static IP and name eth1, has been assigned to eth0 and the associated IP (so that the first card can't get its proper address).

What configuration file(s) control assigning of names (e.g. eth0) to specific modules as they load?

---

