---
title: "Aircrack Help"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by cmoney12051 on 2009-04-11
im trying to get aircrack to work on my laptop. i installed it ith the ubuntu distros and when i run the airmon command it says its monitoring and then when i run the airodum this is what i get

```
~$ sudo airmon-ng start eth1 13


Interface	Chipset		Driver

eth1		UNKNOWN		wl (monitor mode enabled)

~$ sudo airodump-ng eth1 
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

```

i have tried using wireshark captures but then i always get this

```
~$ sudo aircrack-ng /test.cap
Opening /test.cap
This file is not a regular 802.11 (wireless) capture.
Read 0 packets.

No networks found, exiting.


Quitting aircrack-ng...
```

please help. thanks

---

### Post by taylor102387 on 2009-04-11
Well I know for one once you use airmon-ng to start a interface on moniter mode, it creates a new interface called mon0 and you use mon0 as if it was your real interface. Im pretty new too but I managed to learn simple bash scripting and created a script here: [http://code.google.com/p/aircrack-ng-bash-script/](http://code.google.com/p/aircrack-ng-bash-script/) You can download that and save it on your desktop and double click it like an icon and it will do all the typing for you. You just need to follow the on-screen instructions.

As for wireshark, just use airodump-ng, it's much easier!

you can just download the script below

||
||
||
\/

---

