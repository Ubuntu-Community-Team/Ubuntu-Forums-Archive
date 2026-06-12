---
title: "B0rken Wireless"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Jayzilla on 2006-06-19
I can't reach any websites, or even ping my wireless router.  Yet, KWifiManager shows my signal as 100%.  

iwconfig returns:

```
johnjay@johnjay-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Warning: Driver for device eth1 has been compiled with version 20
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

eth1      IEEE 802.11b/g  ESSID:"heavyjay"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:E0:98:DA:02:6A
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=186/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Any ideas?

EDIT: My router interface sees this box when it's wired up, but not when I try to use to wireless.  When I disconnect and reconnect, it doesn't give me an IP.

---

### Post by kb3hkg on 2006-06-20
how are you disconnecting and reconnecting? And how are you trying to obtain the ip, what commands?

---

### Post by goodmaj on 2006-06-20
Are you using ndiswrapper?

---

