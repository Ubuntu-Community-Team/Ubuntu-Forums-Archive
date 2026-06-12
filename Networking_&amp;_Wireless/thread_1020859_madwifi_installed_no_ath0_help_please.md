---
title: "madwifi installed no ath0? help please"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by sin360 on 2008-12-24
I've installed madwfi 094,currently running 8.04 64 bit. But I do not have ath0, this is my output from dmesg. 
[  144.581838] wlan: 0.9.4
[  156.719921] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  156.764136] ath_pci: 0.9.4
It shows in used in the restricted modules panels. When I run ifconfig all it shows me is eth0 and lo no ath0. Here is my lsmod output.
ath_pci               107568  0 
ath_hal               220016  1 ath_pci
wlan_scan_sta          16384  0 
wlan                  226336  2 ath_pci,wlan_scan_sta

Can someone help.
Thank You

---

