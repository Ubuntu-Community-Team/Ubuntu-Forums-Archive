---
title: "Route all traffic from my internal network through SSH tunnel running on ubuntu box"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by Milado on 2011-08-20
Hello

I would appreciate any help you can offer.

I have the following setup:

1- Ubuntu 11.04 installed on a desktop (consider it my local server)
It has two interfaces:
A) ppp0 (IP changes every time I connect to the internet) connected to the internet (3G modem).
B) eth0 (10.42.43.1) connected through a cable to a wireless router, which in return serves as an access point for all other wireless devices in my home. this router has DHCP server disabled.
This eth0 interface is set as "Shared to other computers" therefore It handles all DHCP, DNS and internet requests, and serves them through the ppp0 interface.

All is good here, but I have "SSH Tunnel Manager" installed on my local server and configured to connect to my remote server (offshore). It's a Dynamic tunnel. I can access this tunnel from my local server through 127.0.0.1:1080 and everything is OK.

Now what I want is to route all the traffic that comes from eth0 to my dynamic tunnel 127.0.0.1:1080 so I can protect the traffic that comes from other wireless devices in my home from being intercepted by my ISP.

Any help is appreciated. Thanks in advance.

---

### Post by Milado on 2011-08-21
Bumb

---

