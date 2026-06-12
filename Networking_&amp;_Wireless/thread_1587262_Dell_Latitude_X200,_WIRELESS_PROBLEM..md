---
title: "Dell Latitude X200, WIRELESS PROBLEM."
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by twilightindie123 on 2010-10-03
Hi everyone,

I just recently installed Lubuntu on my DELL LATITUDE and my WIRELESS card seems to not be installed:

eth0      Link encap:Ethernet  HWaddr 00:06:5b:89:c6:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9472 (9.4 KB)  TX bytes:9472 (9.4 KB)


It used to work perfectly with Xubuntu, is there a way I can make Lubuntu to recognize it?

Thanks in Advance.

---

### Post by twilightindie123 on 2010-10-03
bump!

---

### Post by spiky001 on 2010-10-03
Have you check for drivers  can you connect eth0 you will need output of ```
lspci
```

---

