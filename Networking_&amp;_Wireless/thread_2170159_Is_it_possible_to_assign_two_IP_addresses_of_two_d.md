---
title: "Is it possible to assign two IP addresses of two different subnets for eth0 on ubuntu"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by Beth_Tran on 2013-08-25
Hi all,
   I've read so many posts regarding this subject, and have tried many variations without success.
   Can any guru let me know if it's possible to do this, and if yes, how?
   I'm trying to set up openstack/grizzly on VM ubuntu 12.04, and this requires two NICs, 
   which my host does not have.  It has only one NIC.
   Appreciate your expert comments.
Cheers,
Beth

---

### Post by Cheesemill on 2013-08-25
If you are looking to test OpenStack on a single machine then don't bother manually installing everything and setting up multiple IP's, just use DevStack instead....

[http://devstack.org/](http://devstack.org/)

---

### Post by TheFu on 2013-08-25
Possible, probably. I'd think it would only work with managed layer-3 switches. You probably want multiple switches to segment each network.
It would be cheaper to buy another NIC and another cheap switch than to do it with 1 NIC and a layer-3 switch. Those are expensive for a home user who isn't "into networking."

---

