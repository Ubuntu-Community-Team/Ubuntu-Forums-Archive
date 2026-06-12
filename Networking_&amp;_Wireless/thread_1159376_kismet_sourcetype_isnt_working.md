---
title: "kismet sourcetype isnt working"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by fishywishy on 2009-05-14
hi im having trouble getting kismet to work. for the source type ive got:

sourcetype=ath9k,wlan0,atheros

it stops at ath9k

i do "lsmod | grep ath" and i get: mac80211   217208   1   ath9k

i have a Atheros AR5008 AR5BXB72 802.11n Mini PCIe Wireless Card and im running madwifi-ng drivers

however ive just read and confirmed that "sourcetype=ath5k,wlan0,atheros" works, but its slower. how can i get ath9k to work?

---

