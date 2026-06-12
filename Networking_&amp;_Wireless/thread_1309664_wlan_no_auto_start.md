---
title: "wlan no auto start"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by emuman on 2009-11-01
System: karmic 9.10
The wlan connection doesn't autostart after upgrade from 9.04. 
Workaround: sudo /etc/init.d/networking restart

What's the solution?

---

### Post by emuman on 2009-11-07
Solution was: I comment the wlan0 interface out in network/interfaces and let network-manager manage the connection.

---

