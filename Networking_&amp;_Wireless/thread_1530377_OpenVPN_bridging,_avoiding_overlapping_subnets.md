---
title: "OpenVPN bridging, avoiding overlapping subnets"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by YesWeCan on 2010-07-13
I have created a "road warrior" setup so that a roaming Windows laptop can connect to a Windows home network via a Ubuntu server. The laptop runs OpenVPN client with tap tunnel to the Ubuntu server that bridges the tap to the local Windows network. It all works in general.

A problem arises when the LAN subnet where the laptop is occassionally located happens to be the same as the home LAN subnet. In this case, the "redirect-gateway def1" fails to redirect and the client reports errors during connection. Presumably this is because the router local to the laptop has the same IP address as the home router and this causes some sort of routing confusion. As far as I can tell from the OpenVPN docs, having overlapping subnets is a big no-no.

I have two questions:
1) I can change the home LAN subnet to something else. But to what? How do I decide what a suitably uncommon subnet is? How do I predict what Starbucks or Borders use for subnets, for example, or other wireless locations?

2) I read that I can avoid changing the home subnet by having the Ubuntu server remap the local LAN addresses in its IP tables. Does this actually work with Windows networking? I don't know but I am concerned that netbios or something will send IP details within a packet and therefore will not be NAT'ed. Has anyone successfully used NAT/NETMAP with Windows networking?

Many thanks,
Brian

---

