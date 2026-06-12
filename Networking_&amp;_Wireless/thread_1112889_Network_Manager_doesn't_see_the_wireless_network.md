---
title: "Network Manager doesn't see the wireless network"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by ricky22 on 2009-04-01
Hi,

I changed the WPA2 password in my wireless router yesterday (the connection had been very slow recently and I was worried it had been broken). I was able to connect yesterday, but today the GNOME Network Manager doesn't even see the network. I can connect to it from my mobile, from a Mac, and from PC under Windows. I can connect to other networks in Ubuntu, but it doesn't see my own network at all. The router is next to my PC. It worked fine with the old password. When I create the network manually, the bar shows no signal, and it prompts me for the password over and over again. I installed the wifi-radar, it finds all the networks in the area except for my own, same as the GNOME Network Manager. The wireless device in my PC is Broadcom, with proprietary driver that came with Ubuntu 8.10. It's worked fine so far. Any help on that would be really appreciated. Thanks!

Patrick

---

### Post by ricky22 on 2009-04-01
SOLVED!

I checked the system log, saw the error: 

Apr  1 11:07:54 P NetworkManager: <WARN>  start_sharing(): (eth1): failed to start dnsmasq: Could not find dnsmasq binary. 

Installed the dnsmasq package through Synaptic and it works! *^_^*

Patrick

---

### Post by rasmus91 on 2009-04-01
super :D

---

