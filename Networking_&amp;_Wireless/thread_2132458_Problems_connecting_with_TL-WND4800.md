---
title: "Problems connecting with TL-WND4800"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by DeHaven on 2013-04-04
I have been searching through a bunch of different forums and i haven't managed to get this to work. My network requires a device name, and mac address in order for it to connect  (netgear) and i have managed to get my laptop, running ubuntu 12.04, on that network. When i tried getting my desktop on it it simply wouldn't connect so i took off the filters and it didn't see that there was a connnection, and when it did it still asked for a password.
Has someone had this issue before or know why i can't seem to connect even with no filters?
Some information on drivers.
 
dehaven@dehaven-tower:~$ lspci | grep Network00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
04:00.0 Network controller: Atheros Communications Inc. AR9300 Wireless LAN adaptor (rev 01)

dehaven@dehaven-tower:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:60:00:ca:d3:29  
          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:feca:d329/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141588 errors:0 dropped:2 overruns:0 frame:0
          TX packets:87442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190489549 (190.4 MB)  TX bytes:8142109 (8.1 MB)
          Interrupt:20 Memory:f2100000-f2120000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300269 (300.2 KB)  TX bytes:300269 (300.2 KB)


wlan0     Link encap:Ethernet  HWaddr a0:f3:c1:0c:00:ea  
          inet6 addr: fe80::a2f3:c1ff:fe0c:ea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39150 (39.1 KB)  TX bytes:44950 (44.9 KB)

---

