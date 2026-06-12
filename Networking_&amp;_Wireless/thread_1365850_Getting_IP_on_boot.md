---
title: "Getting IP on boot"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by PaulStat on 2009-12-27
I'm sure this must be frequently asked, but I'm not sure what to search for?

Anyway I've configured my wireless USB dongle to have a static IP address, but I've noticed it only 'gets' it after I've logged in. So if I want to connect to my linux box from my Vista laptop using NX, I have to login on the linux machine first.

How do I get it so that it resolves the IP and connects to the network during boot?

---

### Post by Iowan on 2009-12-27
Unless things have changed lately (my batting average isn't too good today), Network Manager configures interfaces on user login. The older */etc/network/interfaces* method seems to configure devices on boot.

---

