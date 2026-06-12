---
title: "Wireless not working"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by kickwin on 2009-06-28
I recently installed Ubuntu on my laptop and I tried many things posted about getting wireless to work but to no avail. Mainly those things were to do with tweaking ndiswrapper. I was wondering if you guys could help this novice out. I am using a Dell Inspiron 1300 laptop and the wireless card is *Dell Wireless 1370* WLAN MiniPCI Card. Thank you.

Here is my ifconfig
```
raml@raml:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6c:05:df  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6c:5df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99227709 (99.2 MB)  TX bytes:6570151 (6.5 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```Here is my iwconfig.
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by Augsburg on 2009-06-28
Here are some other forum that may help:

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[http://ubuntuforums.org/showthread.php?t=120383](http://ubuntuforums.org/showthread.php?t=120383)
[http://www.experts-exchange.com/Hardware/Laptops_Notebooks/PC_Laptops/Q_23237481.html](http://www.experts-exchange.com/Hardware/Laptops_Notebooks/PC_Laptops/Q_23237481.html)

---

