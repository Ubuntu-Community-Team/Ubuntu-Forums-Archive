---
title: "wireless connection with linksys WUSB100"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by Al P on 2011-07-16
I am new to ubuntu I am trying to find a driver for my wireless adaptor WUSB100 before I install ubuntu again. any ideas?

---

### Post by chili555 on 2011-07-16
There are evidently a couple of different versions of this device. At least one of them is driven by rt2870sta that's already in place but is also claimed by rt2800usb that needs to be blacklisted. In order to find out for sure, we need to see, from a terminal:```
lsusb
```Thanks.

---

