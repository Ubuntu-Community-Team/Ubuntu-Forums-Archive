---
title: "How can I access my computer behind a router from outside of my home network?"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by clay7 on 2013-07-08
If I have a PC running Xubuntu 12.04.2 behind a router in my home, is there a way to access this computer WITHOUT having to do port-forwarding on the router or reconfiguring the router in any way? 

I have SSH and X11VNC installed on this PC.

---

### Post by 1clue on 2013-07-08
Looking at the PC you want to connect, if your IP address is one of the following then you need reconfiguration:
192.168.x.y
172.16.x.y
10.x.y.z

Those are private IP addresses, you need something that does NOT fit one of those patterns in order to reach it over the net without router or firewall modification.

If your ISP gave you public addresses (not one of the above) then you could change the computer in question so it uses one of those addresses and then maybe get to it.

If your router is already set up with a VPN you could use that to get full access to the network.

---

### Post by clay7 on 2013-07-08
Yes, my home IP is 192.168.x.y, but I heard somewhere that I could connect to my home computer without having to adjust port forwarding on the router by using one of two methods:

1. ssh remote port forwarding.

2. OpenVPN.

I searched around but could not figure out how to do either one.

I'm not sure if this matters, but I do have access to a VPS (not at home - it's rented) which has Ubuntu 12.04 server on it.

---

### Post by 1clue on 2013-07-08
One of the main points of having a private network is that a remote person can't get to your computers directly.  A whole lot of people consider that to be a benefit.

If you can set up an ssh vpn on one end you might be able to connect to it from your private host and then send data both ways, but whatever the end point is needs to support that.  If the endpoint is your firewall then for sure you will need to set that up, which means you modify the device configuration.

---

