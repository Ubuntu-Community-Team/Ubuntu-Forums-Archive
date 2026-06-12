---
title: "Trouble with Wired Connection - &quot;Almost Working with Manual Config.&quot;"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by MRCStalker on 2012-03-19
I'm new to Ubuntu - to be honest this is my very first day  trying it... and I've already spent hours trying to make my wired  connection work. Wireless connection works fine (I'm using my celphone as a router to post this).



  I've been using this wired network with Windows and OSX, and in both  systems I also had some trouble trying to connect in the past (and the  troubleshooters did their magic and helped me get connected).
  

Today, this is what I got:


  (I'm running Ubuntu 11.10)

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 78:2b:cb:c3:bf:8f  
          inet6 addr: fe80::7a2b:cbff:fec3:bf8f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:37521 (37.5 KB)
          Interrupt:20 Memory:e2e00000-e2e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8080 (8.0 KB)  TX bytes:8080 (8.0 KB)

wlan0     Link encap:Ethernet  HWaddr 10:0b:a9:82:55:c0  
          inet addr:192.168.43.251  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::120b:a9ff:fe82:55c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13191696 (13.1 MB)  TX bytes:3412094 (3.4 MB)

```I also have some information from Windows ipconfig /all that I ran at my friend's machine

  ```

Ipv6 Address:    <address> preferential 
Ipv4 Address:    172.26.65.23 <preferential> 
Netmask:         255.255.254.0
 Default Gateway: 172.26.64.1 
DHCP Server    : <address> 
DNS Servers    : <address>
 DNS Suffix     : <suffix>
``` The weird thing is that I've tried to configure everything manually,  using "Network Connections". When I add everything inside IPv4 Settings,  the connection is finally successful, but only for 4~5 seconds before  getting disconnected again...


**Update:**I just changed the Connection Method to "Local-Link Only", and the same described above happens: At first, it says "Connection Stablished", but after a few seconds, the wired network gets disconnected.

  If you need more info from my system, please ask. I'm considering making an update to 12.04, but I'm not sure it will work. I really hope someone can help me get connected!
  

Thanks!

---

