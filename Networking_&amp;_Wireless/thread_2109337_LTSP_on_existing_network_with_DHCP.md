---
title: "LTSP on existing network with DHCP"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by rvdb on 2013-01-27
Dear all,

i want an old pc to function as 'terminal' for my Ubuntu workstation.

The network at home has a dhcp server running on the router provided by the internet provider (KPN) and i cannot switch that off.

So i want to install LTSP WITHOUT the dhcp/dns part. The official docs all assume the clients are on a network of their own.

I found a few pointers on the web but i can't get it to work. 

Any help please???

Rein van den Boomgaard

---

### Post by Meliorit on 2013-02-19
I've been working on something similar.  In my experience, you will need to be able to set some pretty advanced settings to get LTSP to work this way.  
1. give LTSP server a static address (vi /etc/network/interfaces)
2. reserve above IP in DHCP server
3. reserve an IP for your LTSP client on your DHCP server.  You'll need an IP to reserve, the mac of the client, and to set Option 017: /opt/ltsp/i386, Option 066: ip of ltsp server, Option 067: ltsp/i386/pxelinux.0

Those settings point the pxe-booting client in the correct direction.  Also make sure you don't install ltsp-server-standalone, the dhcp server on it will conflict with your router's dhcp.

---

