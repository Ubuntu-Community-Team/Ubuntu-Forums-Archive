---
title: "VPNC disallows lookups on local network"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by wgandhi on 2010-07-05
In my current network setup, there is a dhcp server running on 192.168.0.15. There is a personal domain called mypersonal.com with a DNS server on the same machine. Without any VPN, the resolv.conf looks like this :
nameserver 192.168.0.15
search mypersonal.com

Once I connect to my company VPN, resolv.conf is updated with the nameserver for my company domain. It still has my local nameserver information :

nameserver <company DNS primary>
nameserver <company DNS secondary>
nameserver 192.168.0.15
search company.com mypersonal.com

I read the help stating that top 3 nameservers from resolv.conf are used for the lookup. However, ubuntu fails to resolve any access to <website>.mypersonal.com. To make matters worse, if I use my XP machine to logon to work, it is still able to resolve my local network.
Is resolv.conf used in ubuntu at all? 
It feels like there is a simple setting I am missing. On XP, I had to re-prioritize the network adapters to make it work correctly. Is there a similar thing on ubuntu?

---

### Post by purecharger on 2010-08-16
I have the exact same problem! It seems that the secondary/tertiary nameservers are not queried at all. But, as soon as I manually switch the order, the previously unresolvable names are resolved, and the ones that resolved fine no longer resolve!

---

