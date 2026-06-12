---
title: "help me please"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by paleo on 2009-02-05
Ok, thank you for the help with setting up another nic card. This is what I am trying to do. I have two computers both on a wireless lan. one is a vista box the other is ubuntu 8.10 I have a crossover cable and each box has another nic with an ip of 10.0.0.x the wireless is on 192.168.1.x I want to transfer files using my wired 10.0.0.x network please help I can ping my vista and my ubuntu using the 10.0.0.x so I know I have the cards set up but I can't see the vista box from ubuntu or the other way either. I have samba set up on my wireless but the transfer speeds are slow I would like to use samba on the 10.0.0.x network. Please help/

---

### Post by Iowan on 2009-02-05
Are you using the smb.conf "interfaces" option?> # The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


---

