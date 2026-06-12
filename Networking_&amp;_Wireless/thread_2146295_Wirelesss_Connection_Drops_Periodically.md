---
title: "Wirelesss Connection Drops Periodically"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by throese on 2013-05-18
Yeah, it happens quite often now and I don't know why. It was working just fine from the day I bought it. Hope you guys can help me figure this out.

Netgear Wireless Adapter N150

S/N: 27222CB50C739

[ATTACH=CONFIG]242725[/ATTACH]

Problem Solved: Had to put the adapter in a different port on the computer.

---

### Post by praseodym on 2013-05-18
Deactivate the hardware encryption of the driver:
```

echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```and replug the stick

---

