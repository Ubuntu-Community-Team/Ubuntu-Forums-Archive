---
title: "ndiswrapper woe"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by funty127 on 2006-04-23
Hello,

I have got a Linksys WMP11 pci wireless card. I installed ndiswrapper. I can see me access point using the command "iwconfig wlan0". However, it shows Encryption: off even when I have a WEP key. Quality also shows 0. Using "dhcpcd wlan0" i cannot get the net going. I have also modified /etc/rc.conf to start the net at start up which does not work either. Can anyone please suggest what I am doing wrong. I have used the following commands in terminal,

```
iwconfig wlan0 mode managed
iwconfig wlan0 essid bxxxxxxx
iwconfig wlan0 key open s:xxxxxxx
```

Thanks.

---

