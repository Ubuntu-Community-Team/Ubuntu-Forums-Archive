---
title: "Dual Nic configuration ?"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by dbrine on 2009-01-02
I just reinstalled Ubuntu (Desktop) and my MB has 2 NICS built it. When I view the interface file only lo and eth0 are there but when run ifconfig eth1 is pulling an ip as well?? eth0 is static. Why is eth1 pulling an ip? Shouldn't it be disable/ not configured?

---

### Post by arch0njw on 2009-08-10
> **dbrine said:**
> I just reinstalled Ubuntu (Desktop) and my MB has 2 NICS built it. When I view the interface file only lo and eth0 are there but when run ifconfig eth1 is pulling an ip as well?? eth0 is static. Why is eth1 pulling an ip? Shouldn't it be disable/ not configured?

Are you still having this problem?  Can you post your /etc/network/interfaces file?

If you have a line that looks like "auto lo eth0 eth1" you should be able to just remove the eth# controller you don't want to start.

---

