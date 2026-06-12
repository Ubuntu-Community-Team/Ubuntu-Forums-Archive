---
title: "New ethernet card Mac address cannot be recognized"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by samiux on 2009-07-29
I am using Ubuntu 9.04 Server edition.

Recently, my old ethernet card is out of order.  I then replaced it with a new one.  However, the Ubuntu box still keep the Mac address of the broken one.

How to make my box to recognize my new ethernet card with the new Mac address?

Thank you.

---

### Post by chili555 on 2009-07-29
Please open a terminal and let us see the result of:```
cat /etc/udev/rules.d/70-persistent-net.rules
```Please tell us the *wrong* MAC address, so we may advise you. Thanks.

---

