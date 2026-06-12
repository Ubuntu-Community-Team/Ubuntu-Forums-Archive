---
title: "Multiple DHCP servers on one network"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by adammw on 2010-01-26
Hi,

I wasn't quite sure how to do this so I thought I'd ask here.

I'd like to somehow set up a primary DHCP server (allocating only about 50% of address, leaving 50% reserved), and a secondary DHCP server (allocating the other 50%) on my network. However, I want the primary DHCP to give the addresses to everybody, and the secondary DHCP to only kick-in when the primary server is down.

I was wondering if there was a specific method to do this, and if it's actually possible?

Another hurdle is that the secondary DHCP server is on a Netcomm NB9W modem, which isn't that configurable.

Thanks for any help, ;)

---

### Post by inobe on 2010-01-26
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

i hope that offers anything.

---

### Post by Iowan on 2010-01-26
[Here]("http://www.randombugs.com/linux/linux-isc-dhcp-server-failover-debian-ubuntu.html") is an article on DHCP failover for a Debian server.

---

