---
title: "Unable to connect to internet"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by bradley8424 on 2009-03-18
When I booted my machine, running Ubuntu 8.10, this morning I was not able to connect to the internet. However, I am getting a valid IP address from my DHCP server, and no other clients on the network are having this problem. I can ping IP addresses inside the network but can't access anything outside. Could someone help me please?

---

### Post by helgman on 2009-03-18
You can start out by trying to figure out if your computer know it's way around the network:
```
route -n
```
Look for a route with the destination 0.0.0.0. Without it your computer might not know the way out from it's subnet.

You also might want to take a look at the DNS-settings. Try to ping Google
```
ping -c 4 www.google.com
```
and if that doesn't work try
```
ping -c 4 209.85.227.99
```
If you can ping the IP but the FQDN (name) you might want to blame DNS (take a look at /etc/resolv.conf).

Is this a network where the computers worked before or is it the first time it visits?

Regards,
Helgman

---

