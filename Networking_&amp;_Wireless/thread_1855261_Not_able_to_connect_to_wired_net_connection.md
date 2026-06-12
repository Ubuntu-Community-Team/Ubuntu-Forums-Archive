---
title: "Not able to connect to wired net connection"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by varunsaini on 2011-10-05
I have Ubuntu 11.04 and Win 7. wired net is working fine in Win 7 but not in Ubuntu. This is what I am getting for ifconfig -
varun@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:b8:79:9b  
          inet6 addr: fe80::a6ba:dbff:feb8:799b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:746 (746.0 B)  TX bytes:5599 (5.5 KB)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:6e:eb:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by poolet on 2011-10-06
I suppose that your wlan0 interfaces working fine... Right??

Please open up a new terminal and type::

```
lsmod 
```

```
lshw - C network
```

and paste the output here!!!

---

