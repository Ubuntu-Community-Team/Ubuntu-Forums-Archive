---
title: "Internet connection problem after new wireless network created Ubuntu 9.10"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by kadalashvili on 2010-10-03
Hi everyone, I want to share internet connection from my ubuntu box with my smartphone. The problem is when I try create new wireless network via GUI, I have problems with my internet connection. I guess that my machine is still connected to the internet physically, but I cannot access any website via web browser. Also, I can connect to wireless network via my smartphone, but again, I cannot browse the internet. I use Ubuntu 9.10 Desktop edition. My wi-fi adapter is TP-LINK TL-WN821N. If you need some more info - please feel free to ask. I'm not professional system administration and I don't even know what information should I provide. 

EDIT: Here are route command outputs: Before I create wireless network:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
stream-ts1.net. *               255.255.255.255 UH    0      0        0 ppp0
10.8.65.0       *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0


```
After I create wireless network:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
stream-ts1.net. *               255.255.255.255 UH    0      0        0 ppp0
10.42.43.0      *               255.255.255.0   U     0      0        0 wlan2
10.8.65.0       *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.8.65.1       0.0.0.0         UG    0      0        0 eth0

```


Thanks in advance.

---

