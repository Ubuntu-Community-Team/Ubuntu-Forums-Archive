---
title: "Help with airodump-ng"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by inspiron630 on 2009-09-12
I'm having trouble with airodump.

my card is Broadcom 4312.

The monitor seems to start okay...

There website says my card is supported.
[https://mail.google.com/mail/?ui=2&view=bsp&ver=1qygpcgurkovy](https://mail.google.com/mail/?ui=2&view=bsp&ver=1qygpcgurkovy)
 I tried going to the forum link next to my card on that page but it won't load for me.

```
mesw@comp:~$ sudo airmon-ng start eth1 1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
2635    NetworkManager
2653    wpa_supplicant
2662    avahi-daemon
2663    avahi-daemon
3375    dhclient
Process with PID 3375 (dhclient) is running on interface eth1


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)

``````

mesw@comp:~$ sudo airodump-ng --channel 1 --write file.txt eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


```

---

