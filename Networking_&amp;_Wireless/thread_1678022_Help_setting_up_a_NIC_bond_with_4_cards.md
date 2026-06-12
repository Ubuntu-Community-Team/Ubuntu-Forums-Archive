---
title: "Help setting up a NIC bond with 4 cards"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by hosinfefer on 2011-01-29
Hi Guys

Got 4 onbards nics and would like to bond them into a single 4GB pipe. It is running a number of VM's. I can set up a link in my switch but I am stumped on ubuntu side. I think I have to make a file with entries but not sure where or how. Can anyone help out?

---

### Post by mips on 2011-01-30
[http://ubuntuforums.org/showthread.php?t=99668](http://ubuntuforums.org/showthread.php?t=99668)

---

### Post by hosinfefer on 2011-02-05
eth0      Link encap:Ethernet  HWaddr 00:e0:81:c3:c4:45  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fec3:c445/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:791764073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428923250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1113418171264 (1.1 TB)  TX bytes:34788402879 (34.7 GB)
          Memory:fe9e0000-fea00000 

eth1      Link encap:Ethernet  HWaddr 00:e0:81:c3:c5:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fea60000-fea80000 

eth2      Link encap:Ethernet  HWaddr 00:e0:81:c3:c4:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe8e0000-fe900000 

eth3      Link encap:Ethernet  HWaddr 00:e0:81:c3:c5:2f  
          inet6 addr: fe80::2e0:81ff:fec3:c52f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:118372157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50061491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166413478055 (166.4 GB)  TX bytes:4382603212 (4.3 GB)
          Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15352 (15.3 KB)  TX bytes:15352 (15.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.238.1  Bcast:172.16.238.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.197.1  Bcast:192.168.197.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Im lost.I think I want etho 0-3 to run as a bond. Did the install of ifenslave..but lost from there. Where is he getting the hardware address in the first file?

---

