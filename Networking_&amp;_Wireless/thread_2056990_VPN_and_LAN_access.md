---
title: "VPN and LAN access"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by Ptallqvist on 2012-09-12
I tried a search, but the threads had no answers. Except [this]("http://ubuntuforums.org/showthread.php?t=847235&highlight=VPN+LAN+access") one, it had an answer but I couldn't understand it. :)

So, my internet access goes through a VPN, but I'd like to be able to access my local network (192.168.100.etc) directly. How can I set this up?

---

### Post by Ptallqvist on 2012-09-12
I did some experimenting and found the solution myself.
-Edit connections
-IPv4 Settings
-Routes
-Address: the address you want to exclude from the VPN, I guess a range would work as well?
-Netmask: I guess this depends on the router? Anyway, I used the LAN default.
Gateway: Your router's ip.

Not too difficult after I summoned the necessary courage to try it.

---

