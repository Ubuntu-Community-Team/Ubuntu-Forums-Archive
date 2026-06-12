---
title: "Path of kernel source tree - noob needs help please"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by VincentCruise on 2009-09-12
I am installing a driver for a yagi wifi antenna. I need to know the path of "kernel source tree".

thank you.

---

### Post by kidders on 2009-09-13
Hi there,

The kernel source tree on any Linux box is traditionally located at /usr/src/[kernel_name_here]. There are often several installed at any given time, so a symbolic link (called /usr/src/linux) normally points to the one currently in use.

If your driver can't find it, it's probably because it's not there. Try apt-get install linux-source.

I hope that helps.

---

