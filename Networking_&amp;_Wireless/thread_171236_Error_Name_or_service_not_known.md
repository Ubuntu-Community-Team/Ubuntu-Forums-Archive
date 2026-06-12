---
title: "Error: Name or service not known"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by darkrad on 2006-05-06
i changed router ip from 192.168.2.1 to 192.168.0.1, so i changed in /etc/network/interfaces the address and gateway to 192.168.0.4 and 192.168.0.1. then i do 
```
ifdown wlan0 
```and ```
ifup wlan0
```. but after few moments i get: > "Error: Name or service not known". My /etc/network/interfaces is here: > # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
 
auto wlan0
iface wlan0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        gateway 192.168.0.1
        name Wireless LAN card
        wireless_channel 11
        wireless_mode managed
        wireless_essid belkin54g

what's missing? before changing those 2 lines:
        address 192.168.0.4
        gateway 192.168.0.1
internet worked good.
Anything i can do?

---

### Post by darkrad on 2006-05-06
internet works, but why that error shows up?

---

### Post by darkrad on 2006-05-06
ok, fixed, was the entry in /etc/resolv.conf that was not available.

---

