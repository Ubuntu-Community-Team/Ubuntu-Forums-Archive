---
title: "PPTP and network bridge"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by kevpatts on 2010-11-18
Hey all,

I have a problem on my work PC. I need to set up a permanent network bridge so that my virtual machines can see my LAN, but I also need to regularly connect in to a PPTP VPN. These seem to be mutually exclusive.

By the way, I have NO need for my VMs to send traffic over the VPN, in case you thought I was getting at that.

PPTP seems to only be done by the "network-manager" service and the bridge can only be done using the "networking" service (as in /etc/network/interfaces).

To set up the bridge, I have to list eth0 in the file mentioned above, but if I do that it means network-manager cannot use eth0 and therefore it can't connect to the PPTP VPN!

At the moment I change between them by commenting/uncommenting the bridge lines in /etc/network/interfaces and reboot. Is there anything I can do short of getting a second NIC?

Kevpatts

---

### Post by nexius on 2011-03-31
if you are still concerned to know how you can use your PPTP connections with Network Manager and configured bridge interface, let me show you my trick:

1.) Configure your wired interface to have a static address "127.0.1.1/8" and a default gateway that is "0.0.0.0"; This just make you connection active but not interfering with a bridge interface;
2.) Configure your bridge interface as usual adding your wired interface to the bridge;
3.) Add your default gateway gateway as usual using terminal.

Now you can see that you have a working bridge interface with the useful feature of the NetworkManager working too.

Hope this could help. if I was not too clear in may explanation, please let me know and I'll try to help you to find the right way.

Bye
Stefano

---

