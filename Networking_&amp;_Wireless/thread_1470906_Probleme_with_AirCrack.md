---
title: "Probleme with AirCrack"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Finalflo on 2010-05-03
Hy,

I have some problemes with my wifi when I want to use AirCrack.

First I have Ubuntu 10.4 on a Dell Laptop XPS 16.

Here's what I get when I try airmon-ng

> root@florent-linux:~# airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
1114    NetworkManager
1116    avahi-daemon
1120    avahi-daemon
1260    wpa_supplicant
5141    dhclient
Process with PID 5141 (dhclient) is running on interface eth1


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)



When I enter lspci I get

> 04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


And when I enter airodump-ng

> root@florent-linux:~# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


Thanks !

---

### Post by K.Mandla on 2010-05-04
Moved to Networking and Wireless.

---

