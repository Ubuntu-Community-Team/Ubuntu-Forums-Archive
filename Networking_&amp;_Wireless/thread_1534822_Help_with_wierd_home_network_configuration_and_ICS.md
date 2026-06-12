---
title: "Help with wierd home network configuration and ICS"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by fdm on 2010-07-20
With my home network, I am using wireless router that is connected to the internet, my headless server, and three other computers wirelessly. My goal is to add a second source of internet to the network by adding a wireless adapter to the server. In this network, the regular computers can not be used since they can't always be on/stable/in range.

The problem is that I want the server to get internet from my router's connection - but at the same time, I want to disable dhcp in the router, set dhcp up in the server, and have it use ICS to share wlan0 with the three other computers. I can make the server use wlan0 easily, but my friend won't let me use it for heavy traffic because it will slow down his connection and hinder things like streaming.

If anyone knows whether or not this is possible without adding another server or expensive hardware, your help would be much appreciated.

---

### Post by fdm on 2010-07-20
Been reading up on my networking options. Looks like I want to use a network bridge to mesh the two private networks, then I should be able to access both gateways on either network. Hope it works.

---

