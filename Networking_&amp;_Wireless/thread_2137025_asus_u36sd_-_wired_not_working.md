---
title: "asus u36sd - wired not working"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by ntesla123 on 2013-04-19
I a using an asus u36sd. When I put a network cable into the machine while using ubuntu, nothing  happens. Whan I use windows, the cable is detected perfectly.

Test output:
     ```


     
lspci | grep Ethernet

```
 
gives the output:
     

```

05:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0) 
     
```
    
```

ifconfig | grep -A 5 eth0 

```

gives the output
     

```

eth0      Link encap:Ethernet  HWaddr 54:04:a6:3c:30:69                  UP BROADCAST MULTICAST  MTU:1500  Metric:1                RX packets:0 errors:0 dropped:0 overruns:0 frame:0                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                collisions:0 txqueuelen:1000                 RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


```

---

