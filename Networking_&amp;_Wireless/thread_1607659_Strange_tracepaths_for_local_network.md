---
title: "Strange tracepaths for local network"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by sugarwellington on 2010-10-28
Hi, noob here. I've been having strange local network behavior with my Ubuntu 10.04 box.  First off DNS was pretty flakey, but I replaced the automated DHCP servers with 8.8.8.8 and 4.4.4.4  ... that seemed to help.  

Now I see very strange behavior in my local network, the symptoms of which are frequent dropped connections trying to use FTP, VNC, or Samba to try and connect to my other machines.  I did a tracepath and got this back:

tracepath 192.168.1.136
 1:  192.168.1.105 (192.168.1.105)                          0.112ms pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 3:  192.168.1.105 (192.168.1.105)                        3002.961ms !H
     Resume: pmtu 1500 

and sometimes something like this back:
tracepath 192.168.1.136
 1:  192.168.1.105 (192.168.1.105)                          0.139ms pmtu 1500
 1:  no reply
 2:  192.168.1.136 (192.168.1.136)                          1.576ms reached
     Resume: pmtu 1500 hops 2 back 128 

tracert from one of my windows boxes makes a lot more sense and looks like this:
Tracing route to 192.168.1.136 over a maximum of 30 hops

  1    <1 ms    <1 ms    <1 ms  192.168.1.136

Trace complete.


This problem seems like it must extend to my external network connections to as my tracepath for [www.google.com]("http://www.google.com") looks like this:
tracepath 192.168.1.136
 1:  192.168.1.105 (192.168.1.105)                          0.139ms pmtu 1500
 1:  no reply
 2:  192.168.1.136 (192.168.1.136)                          1.576ms reached
     Resume: pmtu 1500 hops 2 back 128 
dmcewan@yoda:~$ tracepath [www.google.com]("http://www.google.com")
 1:  192.168.1.105 (192.168.1.105)                          0.096ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.122ms 
 1:  192.168.1.1 (192.168.1.1)                              1.232ms 
 2:  c-67-188-180-1.hsd1.ca.comcast.net (67.188.180.1)    227.988ms 
 3:  no reply
 4:  be-80-ar01.oakland.ca.sfba.comcast.net (68.85.154.217)  48.539ms 
 5:  pos-0-5-0-0-cr01.sacramento.ca.ibone.comcast.net (68.86.90.137)  24.596ms 
 6:  pos-0-7-0-0-cr01.sanjose.ca.ibone.comcast.net (68.86.85.46)  85.374ms asymm  5 
 7:  68.86.87.6 (68.86.87.6)                               78.621ms asymm  6 
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 


Anyways, my ifconfig is below, please let me know what diagnostic info might help shed some light on this.  I've already come dangerously close to destroying my system by messing with nsswitch.conf and other conf files... I need some guidance.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:a9:18:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4836 (4.8 KB)  TX bytes:4836 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:88:63:89  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe88:6389/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13754933 (13.7 MB)  TX bytes:2084217 (2.0 MB)
          Interrupt:16 Memory:ffffc90000c68000-ffffc90000c68100 

THANK YOU!

---

### Post by zenon222 on 2010-11-04
I have the same issue.

```
$ tracepath www.google.com
 1:  192.168.11.7 (192.168.11.7)                            0.105ms pmtu 1454
 1:  192.168.11.1 (192.168.11.1)                            0.979ms 
 1:  192.168.11.1 (192.168.11.1)                            0.890ms 
 2:  wnpgmb0517w-ad04-lo2.mts.net (142.161.133.201)        45.252ms 
 3:  wnpgmb0229w-dr05-v956.mts.net (142.161.133.65)        53.593ms 
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1454
     Resume: pmtu 1454 
```

---

