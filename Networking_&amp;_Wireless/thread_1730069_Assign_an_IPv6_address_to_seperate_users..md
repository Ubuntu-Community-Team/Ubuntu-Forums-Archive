---
title: "Assign an IPv6 address to seperate users."
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by Fludizz on 2011-04-15
I have an Ubuntu 10.04 server/router with IPv6 internet connectivity (I have an internet routable /64 subnet). Since I have this abundance of IPv6 addresses I wanted to try and assign v6 addresses to specific users on the local system. I've been looking at ip6tables with packet mangling but I don't seem to be able to find out how to do this or if this is even possible.

Current configuration:
eth0: Local network, has the /64 IPv6 public range active and the IPv4 LAN range.
tun0: 6in4 tunnel with a ISP assigned public v6 address.
eth1: Standard IPv4 internet connection.

All users on my system use the v6 address configured on tun0. I want to force them to use the /64 range which is configured on eth0. If I can force users to use a specific v6 address, I'll configure more then one v6 address on this interface based on the users userID on the system.

Can anyone give me some pointers in which direction I should search?

---

### Post by lemming465 on 2011-04-18
Unfortunately, IP addresses and routes are generally shared by all users.  Short of putting them each into separate virtual machine guests, it's going to be very hard to configure or enforce per-user IP addresses.  This is equally true for IPv4 and IPv6.

---

### Post by Fludizz on 2011-04-19
Because all are shared I was thinking something in the direction of "marking" each packet with it's local userID as a mark. Then use the packet mangling options to force a different source address based on the mark the packets have.

Would that be possible? I haven't been able to get that to work...

---

