---
title: "Ubuntu 10.04 Setting NIC Priority"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by rplankenhorn on 2010-11-04
I have a machine running Ubuntu Server 10.04 with two NICs: one LAN (eth0) and one WLAN (wlan0).  The eth0 interface is connected to a router and the router is connected to a cellular modem card to access the internet.  The wlan0 interface is used for maintenance and connects to my wireless network.

What I want to do is reorder the priority of the NICs.  I am thinking that when Ubuntu chooses an interface to access the internet, it chooses the local LAN or eth0 for me over the wireless network.  Since cellular data is slow and I don't have an unlimited plan, when Ubuntu can access the internet over the wlan0 interface, I would like it to use that connection and not the eth0 interface.

I have looked into some other threads and they all seem to suggest something along the lines of adjusting the routing table.  These solutions seem to force the eth0 interface to only do local traffic.  This wouldn't work me because I still need it to be able to connect over the cell connection when the wireless network is not available.

Any help would be much appreciated.

---

