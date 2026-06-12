---
title: "Help with airodump-ng error"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by therikoxide on 2010-02-11
I ran:
$sudo airmon-ng stop ath0
$sudo airmon-ng start wifi0
then:
$sudo airodump-ng wlan0 but received the following error:

octl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

---

