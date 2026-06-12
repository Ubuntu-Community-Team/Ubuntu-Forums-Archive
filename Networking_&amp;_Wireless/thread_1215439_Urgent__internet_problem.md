---
title: "Urgent  internet problem"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by neilcarvalho on 2009-07-17
i hv XP SP3 on my harddrive wid kaspersky antivirus, The net works perfectly fine on xp.

I installed Ubuntu yesterday nite. I configured the net ip and oder settings.The net worked for sometime.Then today morning i switched to XP and used the net there. Then after that i went back to Ubuntu. NET ISNT WORKING NOW....NO MATTER HOW HARD I TRY TO CHANGE THE SETTINGS.ALTHOUGH IT SHOWS NETWORK CONNECTED.I CANT PING TO ANY IP ACCEPT MY OWN.I REALLY WANT TO LEARN UBUNTU. i dont knw wad to do.plzz help me.

---

### Post by superprash2003 on 2009-07-17
do you use need to configure static ips in ubuntu? wont it work via DHCP? post output of **ifconfig** from the terminal

---

### Post by MaindotC on 2009-07-17
Just so you know - the fact that you also have XP has nothing to do with this issue so please don't mention it in the future.

---

### Post by martinbaselier on 2009-07-17
> **strAlan said:**
> Just so you know - the fact that you also have XP has nothing to do with this issue so please don't mention it in the future.
But it does tell something: It shows the hardware isn't defect.

---

### Post by neilcarvalho on 2009-07-17
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:1a:84:8e  
  
            inet addr:172.16.235.135  Bcast:172.16.255.255  Mask:255.255.0.0
  
            inet6 addr: fe80::21c:c0ff:fe1a:848e/64 Scope:Link
  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
            RX packets:1311 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:86379 (86.3 KB)  TX bytes:4234 (4.2 KB)
  
            Interrupt:254 Base address:0x2000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by neilcarvalho on 2009-07-17
yeah i need static ip..............

the above is wad i got after entering ifconfig

plzzz help me....

---

### Post by MaindotC on 2009-07-17
> **martinbaselier said:**
> But it does tell something: It shows the hardware isn't defect.

He already stated that it was working on a previous attempt.  Windows has nothing to do with it.

---

### Post by MaindotC on 2009-07-17
> **neilcarvalho said:**
> eth0      Link encap:Ethernet  HWaddr 00:1c:c0:1a:84:8e  
  
            inet addr:172.16.235.135  Bcast:172.16.255.255  Mask:255.255.0.0
  
            inet6 addr: fe80::21c:c0ff:fe1a:848e/64 Scope:Link
  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
            RX packets:1311 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:86379 (86.3 KB)  TX bytes:4234 (4.2 KB)
  
            Interrupt:254 Base address:0x2000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

Please enclose your output in [code] tags.  Network troubleshooting requires several steps that I don't think are necessary for us members to constantly repeat.  Please try one of [the network troubleshooting guides](http://ubuntuforums.org/showthread.php?t=25557) on the forums.  They tell you what commands to enter and why.  If you have any problems, please state specifically where you are having a problem.

---

