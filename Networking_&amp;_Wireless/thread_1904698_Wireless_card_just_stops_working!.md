---
title: "Wireless card just stops working?!"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by alexandari on 2012-01-05
Greetings,I'm using the Atheros ar5007eg wireless card on my toshiba laptop. I'm currently using Debian Squeeze,and I have the following problem:
Whenever I use the wireless for more than...10 minutes,it just stops. Yes,just stops. No networks in range,restarting the card doesn't work.

**ifconfig** shows the following:
 
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:15:41:e9  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe15:41e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146756 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261955673 (249.8 MiB)  TX bytes:17175332 (16.3 MiB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162448 (158.6 KiB)  TX bytes:162448 (158.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:2f:14:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:90623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115629452 (110.2 MiB)  TX bytes:7311398 (6.9 MiB)
```

This is what **dmesg** shows after I do a networking restart
```
[ 8082.690218] ath5k phy0: noise floor calibration timeout (2457MHz)
[ 8083.082467] ath5k phy0: gain calibration timeout (2462MHz)
[ 8083.412733] ath5k phy0: noise floor calibration timeout (2462MHz)
[ 8083.802356] ath5k phy0: gain calibration timeout (2412MHz)
[ 8084.130221] ath5k phy0: noise floor calibration timeout (2412MHz)

```


Now,I would really like to point out some other things:

Yes,I know that the ath5k drivers are bad unless you update your kernel to a newer version than 2.6.28.1. I'm with the 2.6.32-5-686 version now. I have tried using the ath9k driver,nothing happens.

I think that's all,I would be really happy if you could help

---

### Post by TBABill on 2012-01-05
Have you tried moving from network manager to Wicd? My AR5001 works surprisingly well with wicd where it had many problems with network manager, but I can't explain why.

---

### Post by alexandari on 2012-01-05
> **TBABill said:**
> Have you tried moving from network manager to Wicd? My AR5001 works surprisingly well with wicd where it had many problems with network manager, but I can't explain why.

Wow,thanks for the reply,I think I got this solved. Using WICD for more than an hour now,everything seems to be in order. Thank you so much! I will bump if something goes wrong :KS

---

### Post by TBABill on 2012-01-06
No problem of all...best of luck to you.

---

