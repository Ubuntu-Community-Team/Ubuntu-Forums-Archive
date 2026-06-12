---
title: "Change broadband mobile MTU"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by brunolabs on 2010-07-21
> **SecretCode said:**
> Hm. Try
```
sudo ifconfig eth0 mtu 1492
ifconfig | grep MTU
```

And then try surfing...


Hi all!
I also have this problem but my internet connection is Mobile Broadband (through a wireless modem HSDPA), not eth0.
In this case how can I change the MTU value?


Thanks.

---

### Post by mikewhatever on 2010-07-22
Substitute your interface name to eth0. To find out what you interface name is, run 'ifconfig'.

---

