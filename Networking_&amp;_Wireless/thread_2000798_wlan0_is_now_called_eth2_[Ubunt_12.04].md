---
title: "wlan0 is now called eth2 [Ubunt 12.04]?"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by sanderj on 2012-06-10
My Ubuntu systems upgraded to 12.04 just have "wlan0".

However, I'm now running a fresh (live-boot) Ubuntu 12.04, and it has no wlan0, and the wireless interface is called "eth2".

Is this a new feature of Ubuntu 12.04 and/or Linux 3.0, which only becomes visible when doing a fresh install?




```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:84:3b:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:23:4d:0b:5d:13  
          inet addr:192.168.1.44  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a00:111::223:4dff:fe0b:5d13/64 Scope:Global
          inet6 addr: fe80::223:4dff:fe0b:5d13/64 Scope:Link
          inet6 addr: 2a00:111::2bdd:f004:5ee4/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8894 errors:0 dropped:0 overruns:0 frame:15296
          TX packets:8051 errors:33 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7763843 (7.7 MB)  TX bytes:1037163 (1.0 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:155088 (155.0 KB)  TX bytes:155088 (155.0 KB)

ubuntu@ubuntu:~$
```

---

### Post by praseodym on 2012-06-10
You can rename it back manually in the file **/etc/udev/rules.d/70-persistent-net.rules**

---

