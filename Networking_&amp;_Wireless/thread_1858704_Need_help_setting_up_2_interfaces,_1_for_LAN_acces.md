---
title: "Need help setting up 2 interfaces, 1 for LAN access only, 1 for WAN"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by ziggo0 on 2011-10-12
I'm running Ubuntu Server 10.04 x64 with 2 network cards. They are both hooked directly to a switch, then the switch to the router (10.0.0.1). I'm using one card for all LAN activities, such as Samba, and the other for various internet services (http, ftp, game servers, etc). My reason for this is because on eth1 (lan only) is set for 9k Jumbo Frames, where as eth0 (the one I want to use for all other activity) is set at default MTU (1500). Some servers are not compatible with jumbo frames and refuse to work - so I decided to separate these.

Gateway: 10.0.0.1
eth0: 10.0.0.101 (internet services)
eth1: 10.0.0.102 (samba)

Through my research I'm pretty sure this can be accomplished via route, but I've ran into a problem. I set samba to listen on eth1, which works great - I can connect to shares no problem, except when I request a file it sends it out on eth0 - which is slower because it does not have jumbo frames set. How can I accomplish what I'm trying to do? All I want is samba to exclusively use eth1 for uploads/downloads and everything else can use eth0.

---

### Post by Sergius14 on 2011-10-12
You are mixing the very basic concept of LAN.

Both interfaces are connected directly to the same Network. That's bad.


You have to have different networks, so then even you don't have use routes at all.

Network for LAN-9K Jumbo,  eth1:

10.0.0.102 /24 or 255.255.255.0

Network for Inet,  eth0:

10.0.1.101 /24 or 255.255.255.0

Gateway / Default Gateway

10.0.1.1


Of course, that you have to change the IP address of the router and it is going to be at a different network. Any other device at the LAN that wants to access Internet, has to be at 10.0.1.0/24 network too.


I hope that you could understand what is happening.


Regards,

---

