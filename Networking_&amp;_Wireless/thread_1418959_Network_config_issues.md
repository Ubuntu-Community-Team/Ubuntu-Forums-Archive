---
title: "Network config issues"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by mbailey on 2010-03-01
I recently upgraded to Karmic and in the process, was asked whether I'd like to keep my existing network config. I said yes, because this machine has a static IP on my home network because it is a web server. 

Everything works fine - it can serve web pages, I can remote into it, except when I try to log in, either via NX or the console & use the internet for update or browsing. I can't connect to anything because my network is configured to use ifupdown(eth0). Once I manually change it to Auto Eth1 using the metwork icon in the toolbar, all is well. How do I get just one interface, or at least make the manual change permanent?

Interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
address 192.168.1.98
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by chili555 on 2010-03-01
Manual configuration (/etc/network/interfaces) and Network Manager ("using the metwork icon in the toolbar") don't work and play well together. If you have a home server that you are not going to haul down to the coffee shop, then manual, static configuration without Network Manager will work perfectly well. I suggest you remove NM in Synaptic and enjoy.

Your interfaces file looks perfect.

---

