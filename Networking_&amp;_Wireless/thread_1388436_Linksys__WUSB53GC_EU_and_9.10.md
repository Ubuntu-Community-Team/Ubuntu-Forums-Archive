---
title: "Linksys  WUSB53GC EU and 9.10"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by wschulte on 2010-01-23
Had some troubles getting this wirelss USB device to work on a fresh installled 9.10. The device was seen and a wlan0 interface was setup but no way to get it to work


After looking around a bit I found this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889) and installed the patched kernel (linux-image-2.6.31-16-generic_2.6.31-16.50lp446889lexical1_i386.deb). Worked flawless :D
So assuming this patch was incorporated in newer kernels I went on to the 2.6.31-17 .. and nope .. again only a wlan0 device seen as before the 16 kernel. No network :(

So I stick to the 2.6.31-16 kernel fornow .. any chance the solution of this kernel willbe build in to later kernels ?

---

