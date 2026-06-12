---
title: "3 Nics...but auto numbering skipped eth1 - why?"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by mrchip on 2011-01-17
New to Ubuntu and running desktop version. I have 3 Nic's (one o/b 2-pci). When I ifconfig I get info on eth0, eth2, eth3 and lo. What happened to eth1 and how do I configure eth2 to be eth1.
 
BTW if I ifconfig eth1 I get "error fetching interface information: Device not found"
 
Thanks

---

### Post by Iowan on 2011-01-17
Does **sudo lshw -C network** show anything for eth1?
Another place to look is */etc/udev/rules.d/70-persistent-net.rules*

---

