---
title: "[SOLVED] can ping the router but no internet"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by sam1948 on 2009-01-27
just added dns server name to "resolv.conf"
in my case my dns is the router

```
sudo gedit /etc/resolv.conf
```
in the bottom add this line
```
namesrver dns_server_ip
``` 
(in my network it is the router 192.168.1.1)

---

