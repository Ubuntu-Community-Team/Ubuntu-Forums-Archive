---
title: "my wifi card isnt showing up under the right port! help!"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by fozbolt on 2009-08-12
my wifi card is showing up under my eth1 port instead of the wlan port. is there anyway to make it show up under the wlan port??

---

### Post by Iowan on 2009-08-12
Here's a [similar]("http://ubuntuforums.org/showthread.php?t=1199030") thread.
My laptop also labels the wifi as eth1, but since it works, I let it.

---

### Post by fozbolt on 2009-08-13
it allowed me to rename it but that didnt solve my problem. 

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

does anyone know what this means?

---

