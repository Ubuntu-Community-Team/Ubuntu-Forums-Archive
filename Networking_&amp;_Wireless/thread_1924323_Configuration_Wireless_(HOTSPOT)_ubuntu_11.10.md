---
title: "Configuration Wireless (HOTSPOT) ubuntu 11.10"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by hostkit on 2012-02-12
when I make my dhcp configuration using (wireless laptop whitout adhoc) or 
```
sudo apt-get install hostapd
sudo apt-get install dhcp3-server
```

/sbin/iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
for ppp0 (modem)

/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
for LAN

I run through the rc.local, so if i want to connect to the LAN / modem must be change the configuration

how to let it run the automatic configuration. so if i use eth0 automatic use eth0 configuration, if i use ppp0 automatic use ppp0 configuration.

---

