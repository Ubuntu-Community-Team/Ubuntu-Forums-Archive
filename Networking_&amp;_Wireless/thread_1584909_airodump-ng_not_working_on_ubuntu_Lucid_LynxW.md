---
title: "airodump-ng not working on ubuntu Lucid LynxW"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by pato wlmc on 2010-09-29
Well, I'm following some tut on pen testing, to crack my own wep key ( This this is like the third time I do so, but this laptop is new, so i think this wireless card is not supported )

well this is the error I get from airodump-ng:
```
patowlmc@patowlmc-laptop:~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
```

An this are all the previous commands I entered before that one:

```
patowlmc@patowlmc-laptop:~$ sudo airmon-ng


Interface	Chipset		Driver

eth1		Unknown 		wl

patowlmc@patowlmc-laptop:~$ sudo airmon-ng stop eth1


Interface	Chipset		Driver

eth1		Unknown 		wl (monitor mode disabled)

patowlmc@patowlmc-laptop:~$ sudo ifconfig eth1 down

patowlmc@patowlmc-laptop:~$ sudo airmon-ng start eth1


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
873	NetworkManager
878	avahi-daemon
879	avahi-daemon
976	wpa_supplicant


Interface	Chipset		Driver

eth1		Unknown 		wl (monitor mode enabled)


patowlmc@patowlmc-laptop:~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

```

And here I attach some log files i think could help you.

Thanks for your answers.

P.D. SORRY FOR MY TERRIBLE ENGLISH!! =)

---

### Post by LU][or on 2010-10-08
I've got the same problem...

I suppose we are not the only ones who are in search of the solution, I've googled a lot of time and found this 

[http://forum.aircrack-ng.org/index.php?PHPSESSID=c6a75677fe67905309ec075233b219bb&topic=5859.0](http://forum.aircrack-ng.org/index.php?PHPSESSID=c6a75677fe67905309ec075233b219bb&topic=5859.0)

The guys tells us that wl drivers has no monitor support...

---

### Post by divaniti on 2011-02-28
i have the same problem with my: BCM 4312
any ideas

---

### Post by spiky001 on 2011-02-28
Have a look here [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)

Also here [http://ubuntuforums.org/showthread.php?t=1020170](http://ubuntuforums.org/showthread.php?t=1020170)

---

