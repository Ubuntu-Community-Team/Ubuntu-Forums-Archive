---
title: "Network auto config with 2 NIC's, one static one dhcp"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by TwItChDW on 2009-03-07
I have 2 NIC's one this machine (ubuntu 8.10), one is a wireless usb card (the fake wg111v2 from netgear via ndiswrapper) and a standard Ethernet on-board card. Basically on this machine I want the wireless to connect to my wireless router via dhcp, and the wired connection to connect to another router with a static ip. The wireless is for internet access and the wired is for synergy/samba shares/etc. 

Right now bot are working but I have to manually start the wired connection with ifconfig after I use wicd to start the wireless connection.

I have tried to edit the /etc/network/interfaces file but that gives me an error saying it can't save once edited. I think a better way in this case might be to use a script to configure the eth0 interface after I connect with wicd but I have no clue how to write a script to do this (TOTAL *nix n00b here). This would be using the wicd's script running feature within the app itself. But if I'm wrong let me know.

The wired configuration needs to be static for the obvious reasons and I need to be able to easily change the wireless configuration should I take this laptop out for general use off my home network.

Just to state again, everything IS working but I would rather not have to muck around via command line every time I reboot. Any help here would be appreciated.

---

