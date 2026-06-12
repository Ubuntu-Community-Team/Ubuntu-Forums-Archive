---
title: "RaLink RT2600 | 10.04 SERVER"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by staticextasy on 2010-07-16
Okay so i'm at a snag, Wireless works in Desktop installation using the network manager, however wireless doesn't connect in SERVER installation. 

A) I have read documents over and over on wifidocs, google searches, and other tweaks

My problem is i'm using a belkin PCMCIA card that is recognized by 10.04 server edition but i can not get it to connect to a WPA encrypted router.

the model is RaLink rt2600 802.11 MIMO

here is iwconfig

```
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:off/any
Mode:Managed Access Point: Not-Associated  Tx-Power=20 dBm
Retry long limit: 7 RTS thr:off Fragment thr:off
Power Management:off
```

Here is ifconfig

```
wlan0 Link encap:ethernet HWaddr 00:22:75:00:88:9d
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


Obviously my device is not connected.

Power light is active on the device.

could someone please help me configure this to get it working.

---

