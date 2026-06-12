---
title: "System running two nic with static public ip address. Unable to ping primary (eth0)"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by Robbinparrish on 2011-10-24
[SIZE=2]System running two nic with static public ip address. Unable to ping primary (eth0) ip address from outside the network.

Platform: Ubuntu 11.10 I386 Server
 HP Desktop
 Nic cards eth0 Intel Gigabit Network, eth1 D-Link Gigabit Network

I have configured two nic cards with the two different static public ip addresses. From this system i am able to ping the both networks (gateway and other live ips of these network) and also able to ping any sites or ip of outside the network. I have also checked the ping on both ip address from the outside the network then i found that i am only able to ping my secondary ip address. When i run 'route' command it shows me the default route is my secondary network gateway.

The resolv.conf file contents the following nameservers ...
nameserver 8.8.8.8
nameserver 4.2.2.1

Please help me out to work the both ip address.

Thanks & Regard's
Robbin
[/SIZE]

---

