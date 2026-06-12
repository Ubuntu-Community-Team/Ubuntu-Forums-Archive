---
title: "Not able to browse other sites when connecting to VPN"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by arindom on 2011-04-30
The problem that I have been struggling with is while connecting to VPN server, I can't connect to other sites. 

I am on 11.04, but this have been happening on 10.10 as well. 

On Win7, I was able to browse the VPN and the other sites at the same time without any issue. 

I have read and tried some of the solutions posted in this forum and others. For example : Tried by checking ON the "Use this connection only for resources on its network" option (under IPv4 settings tab) but doing that is allowing me to browse all sites except the VPN site. 

Also tried : sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE (I am using a Wireless connection).

The method that I am using is "Automatic (VPN)".

---

