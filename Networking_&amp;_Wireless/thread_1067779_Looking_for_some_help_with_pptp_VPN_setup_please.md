---
title: "Looking for some help with pptp VPN setup please"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by jimwillsher on 2009-02-12
Ui all,

I've installed the pptpd package via apt, on my Intrepid server. The server is 192.168.1.50. Subnet 255.255.255.0.

My router is 192.168.1.1, and I'm port-forwarding port TCP 1723 through the router to my Intrepid server (192.168.1.50). 

My ppptp options file contains:

localip 192.168.1.50
remoteip 192.168.1.251-253

I can connect to the VPN successfully via the router's external address and I can logon using SSH via the VPN etc, so it's all working well. I can ping the Intrepid server across the VPN.


But....I can't ping any of the other devices on my LAN.

My suspicion of the cause is that the other devices on the LAN have a Default Gateway of 192.168.1.1, e.g. the router, which is correct. However that's just a guess.

Can anyone shed any light on what I need to configure please?

Many thanks,



Jim

---

### Post by jimwillsher on 2009-02-12
Answering my own question. The solution:

echo 1 > /proc/sys/net/ipv4/ip_forward



Jim

---

