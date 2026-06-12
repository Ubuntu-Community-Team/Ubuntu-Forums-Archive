---
title: "Low txpower"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by skyfow89 on 2011-07-10
I'm using backtrack5. I'm getting either 7, 13, or 17 dBm txpower, depending on which channel. I've tried boosting it with iwconfig, but if I try to set it to anything about 17, it says invalid syntax. 
lsmod | grep ng indicates that I'm using the following drivers:
```
cfg80211              152934  3 rtl8187,ath9k,mac80211
```If you need any additional information, please ask. I'm kind of a noobie when it comes to linux as well as wi-fi technology, so I would appreciate your assistance. There are wi-fi connections around that other people can see but I can't, even with airodump-ng.

---

### Post by Dangertux on 2011-07-10
> **skyfow89 said:**
> I'm using backtrack5. I'm getting either 7, 13, or 17 dBm txpower, depending on which channel. I've tried boosting it with iwconfig, but if I try to set it to anything about 17, it says invalid syntax. 
lsmod | grep ng indicates that I'm using the following drivers:
```
cfg80211              152934  3 rtl8187,ath9k,mac80211
```If you need any additional information, please ask. I'm kind of a noobie when it comes to linux as well as wi-fi technology, so I would appreciate your assistance. There are wi-fi connections around that other people can see but I can't, even with airodump-ng.

Are you getting a lot of missed beacons? It sounds like you may be too far from the AP. Also, have you considered using a directional antenna, might help performance.

Edit : Also the Atheros drivers are usually known for having power problems.

---

