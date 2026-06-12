---
title: "Homeplug without router or switch?"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by bejolino on 2011-03-12
Problem:
Upstairs:
HP LaserJet 2600n printer
connected via a standard Ethernet cable to the Homeplug device

downstairs:
Notebook with Ubuntu 10.10 Maverick installed
connected via a standard Ethernet cable to the Homeplug device

Is it possible to print directly?
Or will I need a cross cable?
How will I configre the printer? (When I do manual setup it gives me  IP 169.254.241.52, but then it asks for subnet and gateway data)

How will I configure the printer in my computer?

Any suggestion or useful link?
Is it possible or I will have to use a switch/router?

Can I maybe use 2 cross cables, setting on the printer the IP of the computer and viceversa?

---

### Post by Scunizi on 2011-03-12
Do you have internet connectivity at all?  It doesn't sound like it.  Still it would be much easier with a router.. that aside you might get by with setting static IP addresses on both the printer and computer.. one at 192.168.0.2 and the other at 192.168.0.3 with a subnet of 255.255.255.0 .. this might work as long as the Home Plug system acts like a hub or switch of some sort... otherwise you're back to getting a router .

---

