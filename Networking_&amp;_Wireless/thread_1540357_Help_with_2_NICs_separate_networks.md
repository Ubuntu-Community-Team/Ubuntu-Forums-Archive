---
title: "Help with 2 NICs separate networks"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by swilson8224 on 2010-07-27
Guys and Dolls,

Thank you for the help and for reading my posts.

I am developing a disaster recovery (DR).  I have an Acer G710 running SCO 5.0.7 as production and a machine and in the event I loose her I want a fairly hot backup.  I can't find exact hardware as production so having a real hot spare is not an option at this time.  And we are too cheap to purchase separate licenses of SCO.

So, I bought a LeftHand Networks NSM200 for 300.00 and I got Ubuntu 8.04 loaded via a PXE server.  I configured this NAS as a NFS server and I have a neat script for getting my files from the SCO box to the Ubuntu box without a problem..(that is not true but another subject) and here is my problem.  

The production SCO box and the DR SCO box both have the same license and so they CANNOT be on the same network.

I thought I could use the eth1 on the Ubuntu to talk to the disaster recovery box but I have hit one brick wall.

I am thinking I just set up a static ip network distinct from production with everybody sharing broadcast and gw addresses that I could see the DR box from NAS and production from NAS but I cannot see DR.

Will I have to get into iptables and do some footwork there?

Seriously, thanks for the help.

---

