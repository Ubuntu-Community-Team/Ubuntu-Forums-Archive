---
title: "Set IP address of DHCP client failure"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by slick666 on 2009-11-05
Dear forum

Like the title says I'm trying to set the dhcp failure ip address. What I want to do is set up a box that normally uses DHCP to get it's ip address. but every once and a while I would like to connect it via crossover cable to another machine. In that case I would like to have the box default over to a know address (i.e. 192.168.1.123). My thought is to have the system run DHCP but when it times out set the ip address to something static.

This is on an ubuntu server so I think it is just a matter of configuring the /etc/network/interfaces file. I can't seem to find what I'm looking for because there is so much content that comes back. If someone could give me a boost or post a link it would be most appreciated.

---

### Post by Iowan on 2009-11-05
No positive answer, but check options in */etc/dhclient.conf*. Perhaps there's a failover option in there.

---

