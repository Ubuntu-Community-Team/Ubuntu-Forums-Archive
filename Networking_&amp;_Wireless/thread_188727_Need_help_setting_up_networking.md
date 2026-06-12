---
title: "Need help setting up networking"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by ani_m_17 on 2006-06-04
I have a netgear WG311v2 wireless network card.
During Kubuntu installation the card was detected but it said "autoconfiguration of network failed". Anyway...I decided to select the option of configuring the network later but now I don't know how to configure it exactly.

My current /etc/network/interfaces file contains the following

*****************************************************
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug 
script grep
map wlan0

iface wlan0 inet dhcp
wireless-mode managed
wireless-essid banyan

auto wlan0

iface eth0 inet
********************************************************

wlan0 is the wireless interface and my wireless network name is banyan. I put all that info in but networking is still now working :(
Please help on how to go about configuring the network with dhcp.
Since I am very new to linux, a step-by-step approach would really help.

Thanks

---

