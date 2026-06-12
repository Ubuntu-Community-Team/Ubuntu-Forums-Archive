---
title: "Network Not COnnecting"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by metzy85 on 2010-03-29
Hello,

A friend called me today and he explained to me that after his ubuntu install he was unable to connect to a wired Ethernet network. He says it trys to connect using ETH0 and then seemingly fails and disconnects. I have him run a if config and send me a pic. The very odd thing about it is He had a lot 5-8 INET6 address??? ANY ideas??

The laptops is Acer extensa 4420

---

### Post by Iowan on 2010-03-30
A few more details might be useful. Share the pic, and/or have your firend run **sudo lshw -C network** and send you (us) the results - this should provide some details about the interfaces. **ifconfig -a** should show all interfaces and whether (or not) they have IP address.

---

