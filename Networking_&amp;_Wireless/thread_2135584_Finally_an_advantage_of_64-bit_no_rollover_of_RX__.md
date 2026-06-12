---
title: "Finally an advantage of 64-bit: no rollover of RX / TX bytes in ifconfig :-)"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by sanderj on 2013-04-14
It looks like I finally found an advantage of 64-bit: no rollover of RX / TX bytes in ifconfig ;)

```
sander@flappie:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:24:54:e8:54:31  
          inet addr:83.128.1.2  Bcast:83.128.1.255  Mask:255.255.252.0
          inet6 addr: fe80::224:54ff:fee8:5431/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6490043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3153270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8568780588 (8.5 GB)  TX bytes:1965826863 (1.9 GB)
          Interrupt:19 
```

See the "(8.5 GB)". Great.

On 32-bit Ubuntu (13.04), after about 4.2 GB (2^32) the RX bytes counter rolls over to 0 GB. BTW: I would think 32-bit should not be a problem for a counter, but apparently it is...


EDIT

After 8 hours of fully loading my 300 / 300 Mbps connection:

```
sander@flappie:~/oud-Downloads$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:24:54:e8:54:31  
          inet addr:83.128.1.2  Bcast:83.128.1.255  Mask:255.255.252.0
          inet6 addr: fe80::224:54ff:fee8:5431/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176506360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88250953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:265741060173 (265.7 GB)  TX bytes:7640086455 (7.6 GB)
          Interrupt:19 
```

"265.7 GB" ... that's a decent counter! :)

---

### Post by permittivity22 on 2013-04-16
nice :)

---

