---
title: "Ubuntu 10.04 on Macbook - Internet Connectivity Issues"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by tomahawk77 on 2010-08-03
Greetings.

I am using Ubuntu 10.04 (64 bit) on my Macbook pro (kernel 2.6.32). I am visiting India from the US, and have been trying to get my laptop to work with my ISP's (BSNL)  high speed DSL internet service. It's been a lot of trouble to say the least. Here's the skinny.

Initially I was provided with Nokia Siemens modem (can't remember the model no) and I was able to connect to the internet on and off. Google Chrome would indefinitely get stuck at "Resolving Host" whenever I typed in a URL. For some reason, the ISP decided to replace the modem instead, and now I have a Teracom (T2-B) modem. It seemed to have done the trick, since I was able to have relatively stable internet connection for the past couple of days or so, but now I am back to square one - I can only connect to the internet on and off. 

What seems to work sometimes though is if I unplug all the wires from the modem, and connect them back. But lately that does not seem to be working either. 

I tried re-installing the ethernet card (BCM 4322) drivers, and also tried to manually specify the ISP's DNS in the internet connection settings. Neither of these worked.  

Any help will be highly appreciated. 

Thanks in advance.
-Andy

---

### Post by dineshs on 2010-08-03
please read post #7 in
[http://ubuntuforums.org/showthread.php?t=1539138](http://ubuntuforums.org/showthread.php?t=1539138)
note:the teracom modem config will be similar to C2110 siemens .So in this site 
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) see C2110

---

### Post by tomahawk77 on 2010-08-03
Great, thank you very much ! It is working now. We'll see how long this happy situation continues :D

---

### Post by tomahawk77 on 2010-08-03
OK, so maybe I spoke too soon. It seems that the connection seems to work fine, but once I reboot, the problem comes back on. Now I need to unplug the modem, and also "reboot" the modem several times, before I am able to connect to the internet. 

Any suggestions?

---

### Post by dineshs on 2010-08-04
1)which method did you try?bridge or PPPoE?
2)please post the output of```
ifconfig -a
```and ```
ping -c3 4.2.2.1
```when the connection is [COLOR="SeaGreen"]not working[/COLOR]

---

### Post by tomahawk77 on 2010-08-04
I configured according to the instructions on the website you had mentioned. It is certainly PPPoE and not Bridged. 

Please see below for the outputs you requested. 

Thanks again.

andy@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr d4:9a:20:be:36:72  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d69a:20ff:febe:3672/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:465437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:473562098 (473.5 MB)  TX bytes:66229884 (66.2 MB)
          Interrupt:28 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr f8:1e:df:da:71:05  
          inet6 addr: fe80::fa1e:dfff:feda:7105/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:1 dropped:0 overruns:0 frame:35594
          TX packets:136 errors:54 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15368 (15.3 KB)  TX bytes:19720 (19.7 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133306 (133.3 KB)  TX bytes:133306 (133.3 KB)

pan0      Link encap:Ethernet  HWaddr 1a:23:b0:98:9b:ac  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



andy@laptop:~$ ping -c3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=53 time=229 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=53 time=229 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=53 time=227 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 227.623/228.731/229.461/0.887 ms

---

### Post by dineshs on 2010-08-04
Hope you got these outputs when the connection was not working.If so it is a DNS issue.To solve,
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select eth0 - click edit
select ipv4 
method-automatic DHCP addresses only
Give DNS as 4.2.2.1
apply.

Any progress?

---

### Post by tomahawk77 on 2010-08-04
Well I am actually finding it hard to say whether it's working or not. Because it works on and off. And when it works, it's very very slow - so you don't even know if it's working or not. 

I did try to specify the ISP's DNS and then the Open DNS you provided. It seemed to be "working" with the ISP's DNS but not with 4.2.2.1.

---

### Post by dineshs on 2010-08-04
When it is not working(when pages are not loading),
1)Is the [COLOR="Purple"]DSL[/COLOR] lamp stable?(DSL lamp should be stable 3 minutes after switching ON the modem)
2)If DSL is stable,what about the [COLOR="Purple"]internet[/COLOR] lamp?

---

### Post by tomahawk77 on 2010-08-04
Sorry about the delay in writing. Just was not able to connect. 

The DSL light is solid green, but the internet light is either flickering (most of the times) or solid green also. 

Not sure what's going on here. I was initially suspecting that it could be a modem compatibility issue (64 bit OS on a 32bit modem?)..

---

### Post by dineshs on 2010-08-04
from the ifconfig output> RX bytes:473562098 (473.5 MB) TX bytes:66229884 (66.2 MB)and the status of internet lamp I think there is traffic through eth0 .....
Can you try bridge mode? ie configure the modem in bridge then
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

### Post by tomahawk77 on 2010-08-04
I created the Bridged connection after deleting the existing PPPoE connection and creating a new bridged connection.

The network manager does not connect using the bridged connection - it simply keeps going back to the default "Auto eth0" connection.

---

### Post by dineshs on 2010-08-05
please continue PPPoE mode and when you have difficulties check
```
ifconfig -a
``` and ```
ping -c5 4.2.2.1
```post back
Also pl read(Not sure if this is related)
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by tomahawk77 on 2010-08-05
Greetings. My apologies for the delay in posting. BSNL folks had taken away my modem. They finally "re-configured" it and only just returned it. My internet connection is working fine now. I have no idea what they did - I will enquire today, and then post back. 

Thank you very much for your timely help, and patience.

Andy

---

