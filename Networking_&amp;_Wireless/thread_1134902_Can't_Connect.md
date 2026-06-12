---
title: "Can't Connect"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by drewv on 2009-04-24
I'm setting up a new Ubuntu 8.10 desktop that I'm trying to use to connect to my Windows XP laptop directly with a crossover cable so that I can pull some files I need off of my laptop.  When I connect the cable both machines start trying to establish a connection, but neither one succeeds.  I have all of the firewalls turned off in Windows, so that's not the problem.  What am I missing?

Thanks!

---

### Post by Iowan on 2009-04-24
How are machines set up? (IP addresses, netmask, gateways, etc.) I presume they can't ping each other.

---

### Post by drewv on 2009-05-07
I did have both machines set up to automatically configure DHCP.  I ended up manually setting up the IP addresses as 192.168.1.4 and 192.168.1.5 and a subnet of 255.255.255.0.  Once I did this they were able to connect.  

Thanks for getting my brain going in the right direction!

---

