---
title: "Bonding (or bridging?) network interfaces"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by akudewan on 2009-05-16
Hi,

I have two ethernet cards on my computer. Both of them are connected to two different ISPs. At present, I can choose either eth0 or eth1 (but not both).

Both the connections use DHCP.

**Is there any way to combine the two so that I can use the bandwidth provided by both?**

I followed [this article]("http://www.linux.com/archive/feature/133849") and tried bonding the connections, but it didn't work. The connection would simply time out while looking up the hostname.

**Could I try bridging? Or is bonding the only way to go?**

---

### Post by netztier on 2009-05-16
> **akudewan said:**
> 
**Could I try bridging? Or is bonding the only way to go?**

Neither bonding nor bridging will help if you want to connect to multiple ISPs simultaneously, they're made for other things.

What you want to to requires some advanced routing and NAT configuration, and it's not going to be trivial!

[http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html)

best regards

Marc

---

### Post by akudewan on 2009-05-16
Thanks! I'll go though that tomorrow. Should be fun

Its 3:17am over here. Must sleep :)

---

