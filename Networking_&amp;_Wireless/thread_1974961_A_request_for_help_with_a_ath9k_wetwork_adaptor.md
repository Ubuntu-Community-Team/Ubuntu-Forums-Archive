---
title: "A request for help with a ath9k wetwork adaptor"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by Trevor_Jones on 2012-05-06
I have a TP link USB wireless adaptor that has stopped working since I upgraded to 12.04 two days ago. It did work before upgrading and my 3G modem is still working fine.

lsusb gives:
Bus 001 Device 006: ID 0cf3:1006 Atheros Communications, Inc. TP-Link TL-WN322G v3 / TL-WN422G v2 802.11g [Atheros AR9271]

lsmod | grep ath gives:
Module Size Used by
ath9k 116206 0
mac80211 460117 1 ath9k
ath9k_common 13781 1 ath9k
ath9k_hw 375829 2 ath9k,ath9k_common
ath 19187 3 ath9k,ath9k_common,ath9k_hw
cfg80211 179123 3 ath9k,mac80211,ath
compat 13247 5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg8 

Any suggestions?
Thanks
Trev

---

### Post by chili555 on 2012-05-06
I believe the correct driver for your device is ath9k_htc and not the similar ath9k. How does ath9k get loaded? May I see:```
cat /etc/modules
```

---

### Post by Trevor_Jones on 2012-05-06
Thanks chili555 the first line of your post solved the problem.
I downloaded the package ath9k_htc-installer_1-0-4.deb - ran it and my network adaptor arose from the dead.
One little query remains. In the two days I was chasing the wrong driver I downloaded and tried to use lots ath9k (without _htc) stuff. Do I have to do any housekeeping and if so what and how?
Once again thanks for spotting my stupdity

---

### Post by chili555 on 2012-05-06
The only thing you need to do is look in /etc/modules to be sure that ath9k is not being explicitly loaded. If it appears in there, remove it. You should be all set, but if not, please post back.

Please use Thread Tools at the top to Mark Solved.

---

