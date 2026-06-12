---
title: "Lost ndiswrapper: can't modprobe it!"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by patrickfromspain on 2006-02-24
Hi there,

After compiling a custom kernel to make my battery monitor work, and I've lost ndiswrapper in my other kernels: 2.6.12-10-686 and -386. I've tried deleting the custom kernel but the problem is still there.

Also, I've removed the installed drivers, rebooted, and installed them again, and ndiswrapper -l says that driver installed, hardware present. But when doing sudo modprobe ndiswrapper it says operation not permited. Also, doing sudo ndiswrapper -m is ok, as it says it already contains an alias directive (or something similar)

Any ideas on how to solve this?

Thanx!

---

