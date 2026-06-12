---
title: "netbios nating"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by mntgoat on 2009-08-26
I have a network 192.168.0.xxx. In there I have a linux box with an ip of lets say 192.168.0.10. That linux box is a NAT router for machines behind it on ips 10.0.0.xxx. The linux has a second NIC on 10.0.0.1. 

All traffic from 10.0.0.xxx to the 192.168.0.xxx network is working fine other than netbios. Basically none of the 10.0.0.xxx machines can query for a netbios name on the 192.168.0.xxx network. I realize the name query is a UDP broadcast, but I have no idea how to forward that broadcast to that network. 

Can anyone please give me some pointers as to how my iptables rules should look?

Thank you,

--Carlos

---

