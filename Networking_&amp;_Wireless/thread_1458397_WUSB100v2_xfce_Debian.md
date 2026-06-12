---
title: "WUSB100v2 xfce Debian"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by KMartDebian on 2010-04-19
Hey everyone,

I was able to successfully put together the driver with the Linksys WUSB100 v2 using ndiswrapper. 

Here is what i get from ndiswrapper -l:
```
rt2870: driver installed
device (1737:0078) present (alternate driver: rt2870sta)
```

But, the catch is where it maps to: ra0 instead of wlan0. This has caused me problems in order to get it to connect through network-manager or in the terminal.

ifconfig output for ra0:
```
ra0:

Link encap: Ethernet HWaddr 00:1e:e5:e8:14:e6
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:2592 (2.5 KiB)
```

iwconfig ra0:

```
Ralink STA ESSID:"11n-AP" Nickname:"RT2870STA"
Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s
RTS thr:off Fragment thr:off
Encryption key:off
Link Quality=10/100 Signal level:0dBm Noise level:-97 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

iwlist scan produces no results on ra0

uname -mr
```
2.6.26-2-686 i686
```

Hope this information helps someone to point me in the right direction!

---

### Post by KMartDebian on 2010-04-20
Probably forgot to mention this is an old Jetbook so I have debian/xfce in order not to chew up the small amount of memory on it.

---

