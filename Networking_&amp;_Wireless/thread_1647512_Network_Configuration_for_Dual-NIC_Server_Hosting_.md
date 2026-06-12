---
title: "Network Configuration for Dual-NIC Server Hosting KVMs"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by dcaunt on 2010-12-17
Hi all,

I'm trying to design a network configuration that will give fault tolerance to my virtual servers.  The setup I'm trying to achieve is two virtual servers (both Ubuntu Server 10.10) running via KVM on a physical Ubuntu 10.10 Server with two network cards.  Both network cards are on the same subnet, so I had to follow the instructions here to avoid ARP problems:

[http://ubuntuforums.org/showthread.php?t=1065664](http://ubuntuforums.org/showthread.php?t=1065664)

Since they're on the same subnet, I figure that the best way to utilize both NICs is to have the traffic from the virtual machines go over both NICs unless one fails (and then all traffic will go over the one remaining good NIC).  To do this, will I need to create a bond between the two NICs?  Will bonding work given the work-around I needed to implement from the thread above?  Does this sound like the best configuration for two NICs (on the same subnet) and two virtual servers?  Can anyone suggest a better setup?

Thanks.

Dan

---

