---
title: "problem bringing up network"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by madfoxhound on 2009-02-12
i was having problems bring up my network. here is the commands i did

```
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:34:d2:88  
          inet addr:10.0.1.100  Bcast:10.0.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

# ifconfig eth0 up
SIOCSIFFLAGS: Device or resource busy
```

---

