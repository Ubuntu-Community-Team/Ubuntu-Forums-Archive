---
title: "Difference between eth0 and wlan0"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by J3ff5 on 2011-02-08
Hi. In my pursuit to change my MAC address, I have run across several questions. I have the program macchanger, but I do not really trust its abilities to "anonymize." The program only changes my eth0 address, after which ifconfig gives an output along these lines:
```
eth0      Link encap:Ethernet  HWaddr c8:84:12:16:4e:c5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19110 (19.1 KB)  TX bytes:19110 (19.1 KB)
```However, when I connect to my home's wireless network, ifconfig adds wlan0, like this:
```
wlan0     Link encap:Ethernet  HWaddr e0:91:f5:1a:8a:00  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e291:f5ff:fe1a:8a00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2808885 (2.8 MB)  TX bytes:291533 (291.5 KB)
```Due the macchanger's apparent inability to change my wlan0 address, I am assuming this is the address that needs to be changed to provide a comfortable level of MAC anonymity. 

I have attempted simply trying things like 
```
ifconfig eth0 down
```to which I receive
```
SIOCSIFFLAGS: Permission denied
```W/ sudo:
```
jeffrey@Ubuntu:~$ sudo ifconfig eth0 down
jeffrey@Ubuntu:~$ sudo ifconfig eth0 hw ether 11:22:33:44:55:66
SIOCSIFHWADDR: Cannot assign requested address
```which I believe may have something to do with my router/firewall, more than trying to change my MAC.

In short, I am not really asking how to change my wlan0 address,or how to change my address at all. I am just wondering if any of you can tell me, or point me towards a guide that explains, the difference between eth0, lo, and wlan0, when it comes to MAC addresses, so I can try to figure this puzzle out a little smoother.

Please don't be too harsh on my nubness, thanks.

---

