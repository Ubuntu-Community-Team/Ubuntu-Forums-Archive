---
title: "Aircrack-ng help on Inspiron 1525"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by The Sorrow on 2009-07-07
Hello, i recently moved from Windows to Ubuntu 8.10 on my Dell Inspiron 1525 and have run into a problem using the Aircrack-ng suite. I use airmon-ng start eth1 to put the card into monitor mode and then type in airodump-ng to start capturing packets but it returns with this

root@******:/home/******# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP link type is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead. Make
Sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

i spent a couple hours researching and tinkering and found nothing. My card has been said to support promiscuous mode so im stuck. Please help

---

