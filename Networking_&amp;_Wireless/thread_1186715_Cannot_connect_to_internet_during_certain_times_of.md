---
title: "Cannot connect to internet during certain times of the day."
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by lozenges on 2009-06-13
Hey guys, 
I've had this problem for as long as i have been using Kubuntu (about 3 months now).

 I live in a dorm with free, shared Internet. Now the problem is after school at around 1630 when everyone gets back from school, the Internet will slow down to a crawl and if my computer is not switched on already, i will not be able to use the Internet.

 I've tried Konqueror and Firefox, (I prefer Firefox) both do not work. I can though, connect to Skype. To surf the Internet again i have to wait till about 2am in the morning.

I recently did an update and it got worse. google took about 2 mins to load if it even loads at all (this is when my computer has been on for the entire night so i can surf the net.) other sites take forever! At first i thought it was the internet problem but after i disconnected the ethernet cable and tested the speed with wifi from my room mate's table, i am surfing the net with decent speed. i am now certain it is either the port or my computer. 

Some students here buy a router for the same internet connection, funny thing is, i am able to surf the internet whatever time it is if i am using the wireless signal (this is not a solution as i have to borrow my roommate's table to use the wireless, my table is too far away to recieve any signal) 

So my question is.. why is this so? and how am i able to fix it? 

The school just provides a direct ethernet port to connect our laptops to with a ethernet cable, the ports looks alot like a modified phone jack so there is nothing to change and modify on the harware side and buying a router is not on my mind.

If you need me to elaborate more on my situation, please let me know and i will explain in greater detail

Thank you.

---

### Post by lozenges on 2009-06-13
I did a ```
ifconfig
``` when i switched off the wifi and have the ethernet cable plugged in. and the output was ```
eth1      Link encap:Ethernet  HWaddr 00:1d:72:e5:97:79
          inet addr:172.17.166.175  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:72ff:fee5:9779/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:956837 (956.8 KB)  TX bytes:37255 (37.2 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:93672 (93.6 KB)  TX bytes:93672 (93.6 KB)
```and this is the output with only the wifi
```
eth1      Link encap:Ethernet  HWaddr 00:1d:72:e5:97:79  
          inet6 addr: fe80::21d:72ff:fee5:9779/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:21377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                          
          RX bytes:1348498 (1.3 MB)  TX bytes:42768 (42.7 KB)   
          Interrupt:16                                          

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:95201 (95.2 KB)  TX bytes:95201 (95.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:28:89:94
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe28:8994/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1266895 (1.2 MB)  TX bytes:468914 (468.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4E-28-89-94-39-39-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```this is with both of them plugged in 
```
eth1      Link encap:Ethernet  HWaddr 00:1d:72:e5:97:79  
          inet addr:172.17.166.175  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:72ff:fee5:9779/64 Scope:Link              
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1              
          RX packets:22126 errors:0 dropped:0 overruns:0 frame:0          
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0          
          collisions:0 txqueuelen:1000                                    
          RX bytes:1396759 (1.3 MB)  TX bytes:51940 (51.9 KB)             
          Interrupt:16                                                    

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:95201 (95.2 KB)  TX bytes:95201 (95.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:28:89:94
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe28:8994/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1277797 (1.2 MB)  TX bytes:473862 (473.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4E-28-89-94-39-39-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```hope it'll help
thanks again

---

### Post by Hobgoblin on 2009-06-13
Is the wifi router connected to the same network?

Possibly a DNS issue?  Do you know what DNS servers the wifi router is using?

---

### Post by superprash2003 on 2009-06-14
when connected via wifi you get a 192.x.x.x ip but when connected via wired you get 172.x.x.x ip.. is that the same network?

---

