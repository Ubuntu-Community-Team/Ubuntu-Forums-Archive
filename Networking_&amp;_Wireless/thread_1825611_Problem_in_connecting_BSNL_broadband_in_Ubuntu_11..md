---
title: "Problem in connecting BSNL broadband in Ubuntu 11.04"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by LavenderBlack on 2011-08-15
Hi all,
My laptop is Toshiba Satellite L640. I was initially using ubuntu 10.10,   in which i configured bsnl broadband as a dsl connection and  configured the port using "sudo pppoeconf" command. It was working fine.  Few days back I upgraded to 11.04 and net got disconnected after that. I  am unable to configure and connect as before.  Here are some outputs  that could be useful. Can someone help me on this???


> 
lavender@lavender-Satellite-L640:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:e8:b0:71  
          inet6 addr: fe80::ca0a:a9ff:fee8:b071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:22396 (22.3 KB)  TX bytes:24693 (24.6 KB)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr e8:39:df:3e:ae:a2  
          inet6 addr: fe80::ea39:dfff:fe3e:aea2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8366 (8.3 KB)  TX bytes:8366 (8.3 KB)

> 
lavender@lavender-Satellite-L640:~$ plog
Aug 14 17:56:11 lavender-Satellite-L640 pppd[2208]: Using interface ppp0
Aug 14 17:56:11 lavender-Satellite-L640 pppd[2208]: Connect: ppp0 <--> eth0
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: CHAP authentication failed: User not found
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: CHAP authentication failed
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: Connection terminated.
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: Exit.

> 
lavender@lavender-Satellite-L640:~$ ifconfig ppp0
ppp0: error fetching interface information: Device not found
Please let me know if any more info is needed..
Thank you..

---

### Post by dineshs on 2011-08-17
1)Are you using wired?wireless? or both?Can you post the ourput of ```
sudo dhclient eth0
``` when ethernet cable is connected.
pppoeconf command is used when your modem is in bridge mode.It is always better to configure the modem in pppoe mode for an always ON connection.Difference between the two modes is explained [here]("http://www.syncnext.com/bsnl/broadband/bridge-vs-pppoe-modem-mode-bsnl-broadband/105.html")

---

