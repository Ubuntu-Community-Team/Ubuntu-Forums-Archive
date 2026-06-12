---
title: "How to enable VPN forwarding"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by ewinkley on 2010-06-28
Being new to Ubuntu and Linux in general...

I am trying to set up my ubuntu 10.08 desktop to route traffic from the LAN out it's VPN connection.  I've installed Webmin, but for the life of me cannot get not only packets out the VPN, but I can't get the system to route ANY packets, to the internet or anywhere.

Basically, the routers on both ends of the link (here at the office and a remote office) don't support hardware VPN connections, and I need both networks available to both physical sites.

Environment:
Local office:
(1) Ubuntu 10.08 desktop, with LAN card, 10.0.1.108 (eth0), and VPN adapter (ppp0) with IP 192.168.1.108 (I've set up Webmin with PPTP connection to connect at boot), and this system has DNS installed and functioning
(multiple) Windows 7 systems configured with DHCP, with default gateway set to 10.0.1.108
(multiple) MAC OS systems configured  with DHCP, with default gateway set to 10.0.1.108

Remote office:
(multiple) Windows 2003/2008 servers, one running Routing and Remote access

Can someone direct me or help me figure this out?  Being a newbie, I need pretty explicit directions - and prefer to use Webmin user interface.

Thank you.

---

### Post by Charlietje on 2010-06-28
Hey,

As far as I know, VPN forwarding must be supported by your router.

When you use VPN, the TCP/IP packets are encapsulated.
If your router doesn't support VPN, it can not read the packet and it's dropped.


Regards
Carl

---

### Post by ewinkley on 2010-06-28
The router(s) does support VPN - I have rules that allow port 1723 tcp and GRE; and I can connect from any system outside the office network.  So I believe the router supports it.

I need to figure out how to allow traffic to be routed through the ubuntu machine to the remote network.  I've read that this is possible; just can't put it all together.

I've installed webmin for simple firewall management on ubuntu, configured the PPTP settings within webmin, and added a masquerade rule.

---

