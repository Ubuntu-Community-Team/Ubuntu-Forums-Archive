---
title: "changing MAC address"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by oren tal on 2010-11-09
In order to change the MAC address I do:
 ifconfig eth0 down hw ether ff:ff:ff:ff:ff:f0
When the ff:ff:ff:ff:ff:f0 is the new MAC address.

Now **how do I cancel that change and return it to the real MAC address of my NIC?**

---

### Post by uncaspi on 2010-11-09
reboot or pull out the card

---

