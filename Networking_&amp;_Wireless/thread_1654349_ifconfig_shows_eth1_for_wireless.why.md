---
title: "ifconfig shows eth1 for wireless.why?"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by HMD69 on 2010-12-28
Hi all,
when I type ifconfig it shows 3 devices:eth0 (for ethernet), eth1( for wireless) and lo
Why it shows eth1 for wireless?is it correct?

---

### Post by chili555 on 2010-12-28
It probably is correct. I have a laptop that uses the driver ipw2200; the interface that is created is eth1. There are plenty of threads here on this forum referencing an interface ra0; there are also threads (albeit old) where the interface is called ath0.

It is perfectly normal. I suggest that you and the searchers that will find this thread, not be convinced that there is but one correct way of doing things. There are many.

---

### Post by HMD69 on 2010-12-28
> **chili555 said:**
> It probably is correct. I have a laptop that uses the driver ipw2200; the interface that is created is eth1. There are plenty of threads here on this forum referencing an interface ra0; there are also threads (albeit old) where the interface is called ath0.

It is perfectly normal. I suggest that you and the searchers that will find this thread, not be convinced that there is but one correct way of doing things. There are many.

Thanks

---

### Post by Iowan on 2010-12-29
Both of my laptops (an HP running Jaunty, and a Toshiba running Maverick) also reference the wireless card as eth1. I considered editing */etc/udev/rules.d/70-persistent-net.rules*, but they work fine as is.

---

