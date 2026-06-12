---
title: "Atheros wifi do not stat automaticaaly anymore"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by dentaku65 on 2013-01-28
Hi,

my Atheros ath9k do not start automatically anymore; the system comes up without wifi connection, in order to start I have to insert the command manually:
```
sudo modprobe ath9k
```

My card is:
```
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
```

Xubuntu 12.10

If I put ath9k in /etc/modules the wifi starts automatically, but I guess that is not the corret way, I mean I supposed that modprobe should manage this.

TIA

---

