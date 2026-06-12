---
title: "atheros card problem, not working"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by donmateo147 on 2013-02-19
hi guys,
have a problem with atheros ethernet card after recent system update.

uname -a
```
Linux donmateo-vaio 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr f0:bf:97:8e:65:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:20790 (20.7 KB)  TX bytes:20811 (20.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304953 (304.9 KB)  TX bytes:304953 (304.9 KB)

wlan0     Link encap:Ethernet  HWaddr cc:af:78:c6:24:ba  
          inet addr:10.42.0.89  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ceaf:78ff:fec6:24ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4868346 (4.8 MB)  TX bytes:1302360 (1.3 MB)
```

lsmod | grep atl
```
lsmod | grep atl
atl1c                  41229  0 
compat                 25755  1 atl1c
```

lspci | grep net
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
```

Module is loaded but still nm won't connect. I have never had problems with this card. Could you help?

---

### Post by donmateo147 on 2013-02-19
sitting here whole day and its still not working...any ideas guys?

---

