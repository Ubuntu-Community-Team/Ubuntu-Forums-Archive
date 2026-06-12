---
title: "Ethernet randomly stoped working"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by blacknight31091 on 2009-10-01
Hi i have the newest version of ubuntu and today randomly my Ethernet connection just stoped working for no reason. here is the message logs for what happens when i plug in my cable. (yes the lights are on, on the network card)
Oct  1 14:27:57 Lancer kernel: [  516.420558] tg3: eth0: Link is down.
Oct  1 14:27:59 Lancer kernel: [  518.878241] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct  1 14:27:59 Lancer kernel: [  518.878249] tg3: eth0: Flow control is off for TX and off for RX.
Oct  1 14:28:06 Lancer kernel: [  525.725085] tg3: eth0: Link is down.
Oct  1 14:28:07 Lancer kernel: [  527.308671] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct  1 14:28:07 Lancer kernel: [  527.308679] tg3: eth0: Flow control is off for TX and off for RX.
Oct  1 14:28:10 Lancer kernel: [  529.742957] tg3: eth0: Link is down.
Oct  1 14:28:12 Lancer kernel: [  531.335161] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct  1 14:28:12 Lancer kernel: [  531.335169] tg3: eth0: Flow control is off for TX and off for RX.

I am so confused and i have no idea what to do. 
also when i enter ifconfig in terminal here is what comes up

eth0      Link encap:Ethernet  HWaddr 00:1c:23:53:ef:9e  
          inet6 addr: fec0::a:21c:23ff:fe53:ef9e/64 Scope:Site
          inet6 addr: 2002:8681:98cd:a:21c:23ff:fe53:ef9e/64 Scope:Global
          inet6 addr: fe80::21c:23ff:fe53:ef9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2611160 (2.6 MB)  TX bytes:132135 (132.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42636 (42.6 KB)  TX bytes:42636 (42.6 KB)

virbr0    Link encap:Ethernet  HWaddr 96:ed:6b:39:e8:de  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::94ed:6bff:fe39:e8de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:84266 (84.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:7c:cf:0d  
          inet addr:172.16.149.42  Bcast:172.16.149.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe7c:cf0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6454851 (6.4 MB)  TX bytes:1650939 (1.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-7C-CF-0D-66-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

please help thanks

---

