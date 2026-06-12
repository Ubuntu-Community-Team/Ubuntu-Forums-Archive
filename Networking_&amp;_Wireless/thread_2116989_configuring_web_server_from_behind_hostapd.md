---
title: "configuring web server from behind hostapd"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by attam on 2013-02-17
I am having trouble accessing my apache2 web server (running owncloud) from outside the LAN in my home. My network setup is as below:
In my home, I am connected to the internet via cable modem/vpn which goes into a xubuntu 12.10 laptop running hostapd to serve as a wireless access point for other devices in the apartment (eg, phone, laptop). I have an apache2 web server setup on another xubuntu 12.10 laptop which connects wireless to the AP.

Graphically it is like this:

cable modem --> ethernet --> laptop running hostapd (10.10.0.1) >>> (wifi connection)>>> laptop running apache2 server/owncloud (10.10.0.3)

I am able to connect to my AP and access the internet from my second laptop. I am also able to access my owncloud site from within my home (works on both laptops), but when I try to connect to the owncloud site from outside the LAN, it's not working.

I am somewhat of a beginner, so please consider this when replying.
Thanks...

---

