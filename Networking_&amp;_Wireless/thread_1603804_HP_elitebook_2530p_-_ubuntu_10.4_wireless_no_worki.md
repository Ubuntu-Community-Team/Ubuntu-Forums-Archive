---
title: "HP elitebook 2530p - ubuntu 10.4 wireless no working"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by digitalkn1ght on 2010-10-23
hi guys,

i new too ubuntu , i installed 10.4 last night. i cant get the wireless to work

HP elitebook 2530p 

any help would be great

thanks



02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

d9172@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:c3:c1:95  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fec3:c195/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4450820 (4.4 MB)  TX bytes:436216 (436.2 KB)
          Memory:94800000-94820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

d9172@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions

---

