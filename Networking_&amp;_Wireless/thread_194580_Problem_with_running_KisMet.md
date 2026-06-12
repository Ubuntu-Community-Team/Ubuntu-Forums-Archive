---
title: "Problem with running KisMet"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by snakeyes37 on 2006-06-11
I keep getting this error in the terminal windows when attempting to run KisMet,


```

root@AUDIE:~# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (eth1): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Source 0 (eth1): Opening ipw2200 source interface eth1...
FATAL: pcap reported netlink type 1 (EN10MB) for eth1.  This probably means you're not in RFMON mode or your drivers are reporting a bad value.  Make sure you have the correct drivers and that entering monitor mode succeeded.
root@AUDIE:~#

```


I'm trying to get it to work with Intel Wireless Card 2200 B/G


This is how my source looks in the kismet.conf files, source=ipw2200,eth1,eth1


Thanks.

---

### Post by chili555 on 2006-06-13
Did you do sudo iwconfig eth1 mode monitor? Any errors or messages?

---

### Post by wildseven on 2006-07-16
> **snakeyes37 said:**
> I keep getting this error in the terminal windows when attempting to run KisMet,


```

root@AUDIE:~# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (eth1): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Source 0 (eth1): Opening ipw2200 source interface eth1...
FATAL: pcap reported netlink type 1 (EN10MB) for eth1.  This probably means you're not in RFMON mode or your drivers are reporting a bad value.  Make sure you have the correct drivers and that entering monitor mode succeeded.
root@AUDIE:~#

```


I'm trying to get it to work with Intel Wireless Card 2200 B/G


This is how my source looks in the kismet.conf files, source=ipw2200,eth1,eth1


Thanks.


lol. sry this may be a little late, eeek poster 4 weeks ago lol. your source is wrong.
it should be
source=ipw2200,ethX,ipw2200

x = w/e u are using.

hope this helps ^^

---

