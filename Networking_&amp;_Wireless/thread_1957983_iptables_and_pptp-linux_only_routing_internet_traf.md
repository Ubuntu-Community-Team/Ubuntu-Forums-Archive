---
title: "iptables and pptp-linux only routing internet traffic through VPN tunnel"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by BobboBear on 2012-04-13
I have an Ubuntu server 11.10 with _one_ network card. And no free pci slots on the motherboard. I really do not want to buy an usb-network adapter if possible to avoid.

I use it primarly as an file server with samba.

I have a number of computers connected to a local network (192.168.1.*) the server included.
the connection to the internet is made with a router that has DD-WRT installed. (Router do not have enough CPU to handle PPTP encryption)

I recently bought a VPN account (PPTP) from a company and planning to use it on my server using (shield the server with an VPN tunnel using pptp-linux).

The problem is the following, I want to route all "internet" (read transmission) traffic from the server through the VPN connection, but still be able to do gigabit transfers in my local network.

Im not that good with iptables / route so im hoping for help producing a script that can be used in /etc/ppp/ip-up.d to set this up and a restore script for /etc/ppp/ip-down.d

---

