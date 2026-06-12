---
title: "Cdc acm"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by catinhat on 2009-12-28
I'm trying to install us robotics usb modem for my Ubuntu9.10 computer and the instructions say it needs CDC ACM where would I find this.

---

### Post by chili555 on 2009-12-28
It's probably already there:```
/lib/modules/2.6.31-16-generic/kernel/drivers/usb/class/cdc-acm.ko
```Verify, on your system with:```
sudo updatedb
locate cdc-acm
```Updatedb will take a few moments; please be patient. If you find *cdc-acm.ko*, I think you can proceed.

---

