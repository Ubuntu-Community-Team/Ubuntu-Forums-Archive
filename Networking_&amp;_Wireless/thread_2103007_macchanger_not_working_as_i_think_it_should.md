---
title: "macchanger not working as i think it should"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by skrite on 2013-01-08
hey all, 
trying to set a temporary mac on wlan1. 

i have read a lot of tutorials regarding macchanger that seem pretty easy. However, i don't ever get the 'faked' mac.

here is what happens
i take that device down.. ifconfig wlan1 down.. then..

```
sudo macchanger --mac 00:11:22:33:44:55 wlan1
Permanent MAC: 00:c0:ca:6c:9a:06 (Alfa, Inc.)
Current   MAC: 00:c0:ca:6c:9a:06 (Alfa, Inc.)
New       MAC: 00:11:22:33:44:55 (Cimsys Inc)
```

any ideas? thanks

---

