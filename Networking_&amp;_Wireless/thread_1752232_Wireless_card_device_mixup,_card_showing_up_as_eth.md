---
title: "Wireless card device mixup, card showing up as eth0"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by georgeos on 2011-05-07
Hi there 
 I'm testing the security on my network (wpa) and when I type airmon-ng into the console I see my wireless card as eth0 and that's also the only device I see (at least I think it's my wireless card, all wireless functions are working). When I try to continue typing airodump-ng eth0 I get the following error:  

> ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth0 <#>'
Sysfs injection support was not found either.

Does anyone have any ideas on how to fix this?

Thanks
Georgeos

---

