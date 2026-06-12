---
title: "One NIC - WAN access to eth0:0"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by cje on 2009-03-15
I have one NIC

iface eth0 is .1.10
iface eth0:0 is .1.20

port 80 is routed to .1.10

I have two vhosts (in sites-enabled)
vhost1 /var/www/
vhost2 /var/www2/

Is is possible to access vhost2 from WAN?
If so, how?

---

