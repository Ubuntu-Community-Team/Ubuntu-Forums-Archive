---
title: "Slow/No ethernet connection"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by andraro on 2010-09-07
Hi, 

obviously, I have just started using Linux. I have installed Ubuntu 10.04 on my Acer 5735z (specs an be found [here]("http://www.linlap.com/wiki/acer+aspire+5735z")). 

PROBLEM:
I manage to get a wireless connection with my pc, but when trying to use an Ethernet cable to connect the result is a slow Internet connection which jump online/offline. I have checked the cable and the connection to the router all hardware is working good (!)

I have ran ifconfig and the result is:
>  
eth0      Link encap:Ethernet  HWaddr 00:1d:72:d3:e8:fa  
          inet6 addr: fe80::21d:72ff:fed3:e8fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5478184 (5.4 MB)  TX bytes:1088412 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14916 (14.9 KB)  TX bytes:14916 (14.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:51:88:58  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fe51:8858/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55270533 (55.2 MB)  TX bytes:4992434 (4.9 MB)


when I tried to activate the eth0 via:

> sudo ifconfig etho0 up

I get an error 

> etho0: ERROR while getting interface flags: No such device

WHAT THE HELL COULD BE THE PROBLEM?

Thanks for all responses

---

### Post by BkkBonanza on 2010-09-07
Your spelling...

> sudo ifconfig etho0 up 

it's not etho0 it's eth0  (that's a zero)

---

### Post by andraro on 2010-09-07
yeap very stupid of me

---

### Post by Warren1482 on 2010-09-07
I have the same problem  as you. I tried that command and then it asked me for my sudo password. Do you know what I should type in for my sudo password?

---

### Post by andraro on 2010-09-09
> **Warren1482 said:**
> I have the same problem  as you. I tried that command and then it asked me for my sudo password. Do you know what I should type in for my sudo password?
You should have set a password at the beginning. The sudo gives administrative access to the user. So if you have a password that logs you in that is it.

---

