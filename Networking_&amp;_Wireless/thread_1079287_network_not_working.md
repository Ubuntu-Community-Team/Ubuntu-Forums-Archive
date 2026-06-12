---
title: "network not working"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by morcar on 2009-02-24
I have tried other versions of Ubuntu in the past and they all work with my origo wired router but the newest version of Ubuntu refuses to connect to the net. Even when I install it onto the hard drive.

Does anyone know why this happens and how can i fix the problem ?

---

### Post by Iowan on 2009-02-24
I presume you're using DHCP - post results of **ifconfig**.  Might be helpful to see **lshw -C network**. What happens when you try **dhclient**? (All from a terminal)

---

