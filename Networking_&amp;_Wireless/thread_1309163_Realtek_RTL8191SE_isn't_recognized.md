---
title: "Realtek RTL8191SE isn't recognized"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by framefly on 2009-11-01
Hi all,

my NIC (**Realtek RTL8191SE  Wireless LAN 802.11N PCI-E NIC) **isn't recognized by 9.10. Using ndiswrapper failed also. Is there any solution for this prob?

Thx

---

### Post by filipejps on 2010-02-28
same problem here

---

### Post by pmeves on 2010-03-20
same problem here

---

### Post by chili555 on 2010-03-20
> **pmeves said:**
> same problem herePlease open Applications > Accessoties > Terminal and post:```
lspci -nn
iwconfig
```You can omit all the entries that are obviously not your Realtek. Thanks.

---

