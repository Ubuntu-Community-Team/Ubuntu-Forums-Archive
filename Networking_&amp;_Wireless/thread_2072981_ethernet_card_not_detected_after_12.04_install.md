---
title: "ethernet card not detected after 12.04 install"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by Nuitblanche on 2012-10-18
Hi, 

hope someone can help. I had a Windows XP Profession desktop, slowed down by clutter and junk. I reformatted the hard drive, wiping out windows and installed Ubuntu 12.04. Everything seems to be working fine except I can't get wired connection. It is not detecting the ethernet card.

ifconfig -a

only shows

lo        Link encap:Local loop 
          Inet address:127.0.0.1  Mask:255.0.0.0
          Inet6 address: ::1/128 Scope:Guest
          ACTIVE LOOP WORKING  MTU:16436  Metric:1
          Packages RX:988 errors:0 lost:0 overruns:0 frame:0
          Packages TX:988 errors:0 lost:0 overruns:0 carrier:0
          collissions:0 length.tailTX:0 
          Bytes RX:80864 (80.8 KB)  TX bytes:80864 (80.8 KB)

and

sudo lshw -C network

only shows

PCI (sysfs)

What happened to my ethernet card when I installed Ubuntu 12.04?
How can I fix it?

Thanks much anyone for your help!

---

### Post by chili555 on 2012-10-18
> sudo lshw -C network

only shows

PCI (sysfs)
It takes a few moments, please wait. Actually, we'd rather see:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

