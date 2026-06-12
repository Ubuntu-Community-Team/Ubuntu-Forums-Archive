---
title: "Atheros AR9485 wireless detcet network but can' connect to WPA2-LEAP"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by dantheman27 on 2013-07-18
I just installed Ubuntu 12.04 and everything worked fine excep at my school where they ask for a id and password. All the network are detected but when I try to connect to the one, it stay connecting until it said BAD Password on Wicd.

Thanks all for your help

Daniel

---

### Post by praseodym on 2013-07-19
Deactivate the hardware encryption of the driver

```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

