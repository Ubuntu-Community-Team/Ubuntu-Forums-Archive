---
title: "Problem running cisco vpn"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by chinna saaeb on 2009-08-27
I am using Cisco VPN client on Ubuntu 8.04 LTS (64 bit version). No firestarter installed with automatic DHCp selected in network connections.

Using cisco vpn I could auhtenticate into my server.
There after I am neither able to browse any site nor connect using ftp to my server.
can anybody advise.

---

### Post by cabez0n on 2009-08-31
Perhaps it is a routing problem and when you try to connect to the ftp the traffic goes out to another interface, and not the vpn. Just a thought

Check out the route command

---

