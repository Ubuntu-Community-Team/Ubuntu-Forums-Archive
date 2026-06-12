---
title: "assigning the same ip address to multiple eth interfaces?"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by tr333 on 2009-01-11
Is it possible/safe to assign the same static ip address to both eth0 and eth1 on a machine?

---

### Post by Nostalos on 2009-01-11
You have to use Network Bonding.   [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

---

### Post by dmizer on 2009-01-11
> **Nostalos said:**
> You have to use Network Bonding.   [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

Note:
This does not necessarily give you a faster access speed. It's primary purpose is for load distribution and failover. So, if you have high incoming traffic volume you may see increased performance. Performance will be limited by your LAN speed, and by your connection equipment (router).

If you need a high availability trunk on your network, bonding is a good way to go about it. If you're simply looking for better internet speeds, this probably isn't the answer.

---

### Post by tr333 on 2009-01-12
I didn't really need to do anything complex with this.  I only wanted to setup the networking so that it wouldn't matter which ethernet port the LAN cable was plugged in to (this machine has two network ports on the motherboard).  I would normally have used DHCP, but this situation requires a static IP address.

EDIT:  After reading the link, it looks like network bonding might achieve the same result.

---

