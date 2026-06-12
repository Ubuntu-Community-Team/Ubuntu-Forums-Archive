---
title: "problem running sudo airodump-ng eth1"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by brayden13 on 2009-04-10
brayden@brayden-laptop:/$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

that is the problem i have. I do not really know what to do, eth1 is my card.
I'm having a nice little look at my neighbours net connection, they are a little stupid and today got WLAN, too bad I'm the world's worst neighbour.:lolflag:

oh yeah just remembered to tell ya my wireless adapter is a Broadcom one (i cannot remember the the exact one right now but there are supported drivers)

---

### Post by kevdog on 2009-04-10
Please give us your driver type, and all the commands you have used to get your broadcom card in monitor mode (such as the iw command).

---

### Post by brayden13 on 2009-04-10
It has always been monitoring. I turned it off for a bit earlier to make a fake MAC address, but I used
```
sudo airmon-ng stop eth1
To stop it.
and
sudo airmon-ng start eth1
to start it
```

---

### Post by brayden13 on 2009-04-10
*BUMP* Can someone please help me with this? I went to Synaptic package manager and looked up Sysfs and installed it but that didn't help either.

---

