---
title: "Broadcom BCM43228 problems."
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by kio_http on 2013-03-11
I have a Broadcom BCM43228 Wireless N Dual Band mini PCIE Network card and it does not work out of the box in Ubuntu 12.10. I used jockey-kde ("Restricted drivers") to install a proprietary driver for it and now it works. However my network card and access point support Wireless N 2.4 Ghz and 5 Ghz dual band but it only connects in Wireless G 2.4GHz single band mode.

Any ideas on how I can fixed this? 

I thought 13.04 might have a newer driver and work better but that didn't improve anything.

Also dmesg shows up a lot of errors constantly
```
[ 1445.729758] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1447.724091] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1447.724097] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1449.721725] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1449.721731] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1451.719433] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1451.719439] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1451.719518] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1451.719519] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1453.716957] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1453.716963] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)

```

---

### Post by praseodym on 2013-03-11
Imho it only works on channels 1-11 in 2,4 GHz mode. Check "iwlist chan"

---

### Post by kio_http on 2013-03-12
> **praseodym said:**
> Imho it only works on channels 1-11 in 2,4 GHz mode. Check "iwlist chan"
```
eth1      32 channels in total; available frequencies :          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 150 : 5.75 GHz
          Channel 151 : 5.755 GHz
          Channel 152 : 5.76 GHz
          Channel 153 : 5.765 GHz
          Channel 154 : 5.77 GHz
          Channel 155 : 5.775 GHz
          Channel 156 : 5.78 GHz
          Channel 157 : 5.785 GHz
          Channel 158 : 5.79 GHz
          Channel 159 : 5.795 GHz
          Current Frequency:2.412 GHz (Channel 1)



```

---

### Post by kio_http on 2013-03-13
Bump

---

### Post by kio_http on 2013-03-14
Bump

---

### Post by praseodym on 2013-03-14
Did you ever install the "backports-modules"? If yes, uninstallt them and reboot.

---

### Post by kio_http on 2013-03-14
> **praseodym said:**
> Did you ever install the "backports-modules"? If yes, uninstallt them and reboot.

No.

And I can't find any backports-modules package.

---

