---
title: "Configuring network with 2 network interfaces"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by guest_user on 2012-11-12
I have 2 interfaces on my kubuntu 12.04 computer, 
- eth0 which is a local lan connection with no connection(dhcp network 192.168.11.0, router 192.168.11.1) to the internet and
- wlan0 which is a wireless connection with a a connection(dhcp network 192.168.1.0, router 192.168.1.254) to the internet.

When I try to connect to a website like [www.google.com](www.google.com), it redirects me to the 192.168.11.1 router.

Using dig [www.google.com](www.google.com), I found that the nameserver is set to 127.0.0.1 and that it resolves to 192.168.11.1. 

How can I change it to use the DNS servers of wlan0 instead?

FYI, I have changed the routing tables default gateway to 192.168.1.254.

---

### Post by dannyboy79 on 2012-11-12
within your /etc/network/interfaces file you can add a line like this below the interface

dns-nameservers 192.168.1.254 8.8.8.8 8.8.4.4

those are google open dns servers after your router which is an option if your router doesn't support dns resolve forwarding.

---

