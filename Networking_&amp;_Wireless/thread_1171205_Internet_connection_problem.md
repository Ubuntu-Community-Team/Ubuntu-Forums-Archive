---
title: "Internet connection problem"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by ankurdh on 2009-05-27
hello everyone,

      I got my copy of jaunty some days ago. Previously i had hardy. after the installation i configured the internet connection using pppoeconf. Everything was fine for that session. From the next sessions, there has been a very interruptive connection problem.

    There is no problem getting connected to the internet. But after sometime, all the pages that are loading stop and when i tried plog at the terminal, it shows

"serial link appears to be down"
"connection terminated"
"modem hangup"

initially i thought it was a prob with the internet. But internet is working fine in windows. I want internet in linux also. With hardy, everything was fine. never faced this prob.
Actually things were fine for the first session also. I could download a whole big shell file for netbeans, without interruption. But now this prob has become very irritating. . 

please help me . ..

regards,
ankur.

---

### Post by Rofko on 2009-05-28
There seem to be a lot of problems with wifi in jaunty.

There are several threads on the issue - maybe this is your problem?

[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

No-one seems to be able to some up with a solution.

---

### Post by superprash2003 on 2009-05-28
is this a DSL or dialup?

---

### Post by ankurdh on 2009-06-09
@superprash
its bsnl broadband. i hav unlimited plan. it works just fine in windows. . 

plz help . . :(

i've referred to so many other forums. . changed the interface file in /etc/network as suggested in some community . . stil. . it jus doesn seem to get fine . . .  

:( previously i had hardy. . it was fine with hardy also. . i was so excited abt using a full fledged, daily updated jaunty . . . :(

---

### Post by superprash2003 on 2009-06-10
post output of ifconfig from the ubuntu terminal

---

### Post by ankurdh on 2009-06-10
@superprash
this is the output of the ifconfig command.


ankur@ankur-desktop:~$ ifconfig
[LEFT] eth0      Link encap:Ethernet  HWaddr 00:13:20:66:9e:a2  
[/LEFT]
                        inet6 addr: fe80::213:20ff:fe66:9ea2/64 Scope:Link 
[LEFT]                        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
[/LEFT]
                        RX packets:814 errors:0 dropped:0 overruns:0 frame:0
                        TX packets:792 errors:0 dropped:0 overruns:0 carrier:0
              collisions:1 txqueuelen:1000 
                        RX bytes:838273 (838.2 KB)  TX bytes:181664 (181.6 KB)
   
lo              Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
                        inet6 addr: ::1/128 Scope:Host
                        UP LOOPBACK RUNNING  MTU:16436  Metric:1
                        RX packets:4 errors:0 dropped:0 overruns:0 frame:0
                        TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
                           inet addr:59.92.251.51  P-t-P:59.92.240.1  Mask:255.255.255.255
                          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
                         RX packets:15 errors:0 dropped:0 overruns:0 frame:0
                         TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:3 
                         RX bytes:713 (713.0 B)  TX bytes:613 (613.0 B)

ppp1      Link encap:Point-to-Point Protocol  
                         inet addr:59.92.248.232  P-t-P:59.92.240.1  Mask:255.255.255.255
                         UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
                         RX packets:758 errors:0 dropped:0 overruns:0 frame:0
                         TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:3 
                         RX bytes:817952 (817.9 KB)  TX bytes:162971 (162.9 KB)

---

### Post by superprash2003 on 2009-06-10
why do you have 2 ppps? post output of **sudo dhclient eth0**

---

### Post by ankurdh on 2009-06-17
ankur@ankur-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:20:66:9e:a2
Sending on   LPF/eth0/00:13:20:66:9e:a2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 112739 seconds.

this was what i got on dhclient eth0 command.

---

### Post by Iowan on 2009-06-17
If it's Ubuntu, then [this]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339882") one may not apply.

---

