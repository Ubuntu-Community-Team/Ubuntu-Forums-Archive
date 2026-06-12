---
title: "airodump-ng not working... wireless card maybe?"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by davidmiller252 on 2009-02-12
I tried using airodump-ng, and this is what i got:
```
root@david-laptop:/home/mobile# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

```

I'm not sure what that means. How do I fix this?

btw... my wireless card is a Broadcom BCM4310 802.11b/g (rev 1) and I just installed the restricted drivers for it and everything is working better than with NDISwrapper. before it said that monitor mode was disabled and after I installed the new drivers it said monitor mode was enabled..

Plz help! thanx

---

