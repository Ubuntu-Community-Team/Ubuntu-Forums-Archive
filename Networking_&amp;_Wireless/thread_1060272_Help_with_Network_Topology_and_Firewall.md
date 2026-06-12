---
title: "Help with Network Topology and Firewall"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by LRT on 2009-02-04
I would like to install an Ubuntu firewall on our network but I'm confused about some things because I'm not very familiar with how networks function. Please see the diagram I attached.

I would like the printers, servers, and workstations (desktops and laptops) to be placed on 3 different subnets. 

Should I allow the firewall to also act as the DHCP server and serve the 3 different subnets???

Will it be possible with the proper iptables configuration to allow Desktop 3, for example, to communicate with Server 3 (the file server) or with one of the printers??

---

### Post by cariboo on 2009-02-04
I would suggest you start [here]("http:///tldp.org/HOWTO/NET3-4-HOWTO.html"), then have a look at this [iptables howto]("http://help.ubuntu.com/community/IptablesHowTo").

Jim

---

