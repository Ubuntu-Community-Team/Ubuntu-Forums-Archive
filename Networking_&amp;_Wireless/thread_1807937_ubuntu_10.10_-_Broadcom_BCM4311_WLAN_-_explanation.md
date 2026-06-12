---
title: "ubuntu 10.10 - Broadcom BCM4311 WLAN - explanation"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by uran101 on 2011-07-19
Hi!

I recently had some problems with my Broadcom Corporation BCM4311 802.11b/g WLAN Adapter , but I followed the instructions on the following page:

[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

and I managed to fix everything. Thank you, Ayunthia.
What happened was that I installed a fresh Ubuntu, but the wireless simply didn't work. Ethernet was fine, though.

What I would like to know is what went wrong. Why didn't everything work right from the beginning? I'd really appreciate it if someone would like to explain it to me.

Outputs: (recreated because the situation is different now, but they reflect the state the configuration was in)

dmesg
```
firmware:  requesting b43/ucode5.fw
firmware: requesting b43-open/ucode5.fw
ERROR:  firmware file "b43/ucode5.fw" not found
"b43-open/ucode5.fw" not found
```

lspci
```
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:17:08:3a:53:19  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```


Thank you!!!

Nenad

---

