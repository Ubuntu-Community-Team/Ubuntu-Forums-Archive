---
title: "Re: No internet Access on Ubuntu 12.04"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by eyeneedhelp on 2013-03-16
i am curious about this since i have an usb device i want to give to a friend. how do i see what drivers are embedded in ubuntu. pls keep it simple since i am a rank beginner!. the device is asus by the way but im curious how to see the info .

---

### Post by wildmanne39 on 2013-03-16
*Thread moved to **Networking & Wireless**.*

Please do not hijack someone else's thread.

Please post the output of:
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```
Thanks

---

