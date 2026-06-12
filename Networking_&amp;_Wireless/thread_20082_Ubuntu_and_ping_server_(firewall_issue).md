---
title: "Ubuntu and ping server (firewall issue?)"
date: 2005-03-15
forum: Networking &amp; Wireless
---

### Post by TedLinxs on 2005-03-15
Hi,

Without any problems I could install hoary-preview-live-i386.iso, that wasn't possible in the older versions (so good job guys )
After running the live iso, I tried to use the internetconnection of my server (Fedora core 3)
First setting up eth0 with adress 192.168.1.2, checked this with ifconfig. I can ping this adress but I can't ping the adress of my server (192.168.1.1)
When I use Fedora it's no problem to ping the server.

Did I overlook something, maybe a firewall issue?

Ted

---

### Post by alastair on 2005-03-15
ifconfig -a
route -n

Check /var/log/syslog as well - I assume you would see if packets were being dropped via a firewall.

---

