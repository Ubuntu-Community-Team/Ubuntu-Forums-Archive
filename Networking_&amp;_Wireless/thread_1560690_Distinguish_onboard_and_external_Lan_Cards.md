---
title: "Distinguish onboard and external Lan Cards"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by satish_j on 2010-08-25
eth0 and eth1 are the 2 Lan cards detected on my system.one is on-board and the other is external.
How to distinguish these two cards??i.e whether eth0 is On-board or eth1??

---

### Post by Iowan on 2010-08-25
Pretty low-tech, but check the external to see if it has a MAC address printed on it. Then compare against results of **ifconfig -a** or **sudo lshw -C network**

---

### Post by endotherm on 2010-08-25
if you know the manufacturer of either one of them, just check teh mac prefix with arin, and that should tell you which maniufacturer made which card.

or even simpler, just plug one into a dhcp router, and reboot. then run ifconfig, and see which interface pulled an address.

---

