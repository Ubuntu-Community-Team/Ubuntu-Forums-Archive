---
title: "Dual nics, connecting both causes one connection to drop..."
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by cmed67 on 2013-03-28
Hi all,

   Ubuntu server box with two nics. One lan facing, the other internet facing through a separate router. Both connections work individually, but when both are connected at the same time, the internal nic connection stops allowing connectivity to the server from the lan. I've disabled UFW in lieu of using Shorewall to control "zone" access, but even that fails. I do notice a default route gets set on reboot, but even removing that default route doesn't help. 

   I did just add the following lines to the Sysctl.conf file to see if it helps any:
net.ipv4.conf.all.arp_ignore=1
net.ipv4.conf.all.arp_announce=2
But this did not make any difference. Connectivity to the server from the internal nic is cut off whenever the external nic is connected. 

   I absolutely can not have either network talking to each other, but do want the server to be able to access both in a secure manner <keeping traffic separate>.

Any help would be appreciated!

Carl

---

### Post by cmed67 on 2013-04-02
Is there someplace else I need to post this question to hopefully get a response? I'm sure for someone this is a fairly simple issue and I could really use some help. :-/

---

### Post by Iowan on 2013-04-02
> **cmed67 said:**
> Is there someplace else I need to post this question to hopefully get a response? I'm sure for someone this is a fairly simple issue and I could really use some help. :-/
Nope! This *should* do.
Do both interfaces get IP addresses? Are they in different subnets?
Perhaps post results of:
 ```
ifconfig -a
route -n
```

---

