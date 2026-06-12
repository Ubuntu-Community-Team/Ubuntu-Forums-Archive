---
title: "Internet sharing over virtual interface?"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by abishur on 2012-12-16
I'm trying to be a cheapskate here and use a single ethernet device to attach to my LAN & WAN.  The application is that I want to filter internet traffic through dansguardian.

I have my own personal router (which is what the PC is connected to) whose IP address is let's say 192.168.0.1

I then have it connected to my ISP provided router which we'll say is IP address 192.168.2.1

In the end I want to route traffic from my personal router to my PC and then to the ISP router all on the same NIC.

To accomplish this I've created a bridge Br0 and gave it the IP address 192.168.0.3 and a virtual ethernet adapter Eth0:0 and gave it the IP address 192.168.2.3

I can successfully ping both networks from my PC, but I can't successfully route internet traffic over it.

I've done this often using two ethernet cards but I'm woefully ignorant when it comes to virtual adapters so I'm not sure if this can even be done or not.  Can anyone point me in the right direction?

---

