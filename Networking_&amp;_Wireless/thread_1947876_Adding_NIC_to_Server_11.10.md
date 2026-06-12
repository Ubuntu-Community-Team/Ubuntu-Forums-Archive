---
title: "Adding NIC to Server 11.10"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by Sandcastle on 2012-03-27
Hi all,

I have a server box that I'm adding another network card to, but am having problems in configuration. 

The card is recognized, and listed through lspci and in /etc/udev/rules.d/70-persistant-net.rules. I edited /etc/network/interfaces to assign it a static IP.

However, the machine hangs at boot on network configuration, and returns an error when restarting the network service.

```
# /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                        
ssh stop/waiting
ssh start/running, process 7837
RTNETLINK answers: File exists
Failed to bring up eth1.
```The system boots, complaining of not being able to fully configure the network. However, the card works. I can ping both of its addresses during configuration. The error does not come up when the new card is set to acquire a DHCP address, so I'm tempted to just add a fixed lease for this address.

I suppose I shouldn't complain, but I am still a bit vexed by the issue and hang-on-boot. Is there another file that needs to be edited to properly install the NIC?

---

### Post by Sandcastle on 2012-04-26
I think I found the solution to my problem. I don't have access to the server referenced in my original post, as it was a school loaner, but came across the same situation trying to set an alias.

In /etc/network/interfaces, not defining a gateway for the second interface solved my issue. I'd imagine the problem with the two NICs was also gateway-related.

---

