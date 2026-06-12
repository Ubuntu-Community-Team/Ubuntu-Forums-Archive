---
title: "DHCP server and BOOTP server"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by snarf77 on 2011-08-25
Hi all,

I need to set an IP address for a Device I bought from my computer.  My computer is part of a network where a server (DHCP) distributes leases for IP address.

I consequently need to install on MY computer (running Ubuntu 10.10) a Bootp server to configure my device.

I gave a try to Bootpd and xinetd as I didnt want to interfere with the main office server (runnign dhcp3-server) but I never succeed to make this work and I found a lot of post telling it is now (above ubuntu 10.04 or so) totally deprecated and not usable.

I then instlled dhcp3-server on my computer hoping I can configure only host base on hardware address (MAC) but the dhcp3 server refuses to start if one subnet is not configured and if I must use the one my eth port is part of. Doing this I am configuring the same subnet as the main server which I really don't like. Unfortunately the dchp3 server refuses to start tellign me that:

Aug 25 17:21:23 myhostname dhcpd: Can't bind to dhcp address: Address already in use
Aug 25 17:21:23 myhostname dhcpd: Please make sure there is no other dhcp server

Of course there is one !!

My wish is simply to have a standalone Bootp server on my computer (I used a lot of those on windows) but I can't succeed in making one work in ubuntu and I don't know how to configure dhcp3-server to coexist with another one ??

Any help or workaroud appreciated

Snarf

---

