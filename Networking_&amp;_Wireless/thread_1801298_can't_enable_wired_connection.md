---
title: "can't enable wired connection"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by arnicainthemembrane on 2011-07-10
Hi, I'm trying to get my wired connection up and running.


When i go to Network Connections I get eth0 which I try to "save", causing a Wired Connection 1 to pop up, and then I try to enable both or either and there's no dice whatsoever.

ping just get me unknown host.

ifconfig yields:

eth0      Link encap:Ethernet  HWaddr 00:26:18:5d:4a:fe  
          inet6 addr: fe80::226:18ff:fe5d:4afe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1504040 (1.5 MB)  TX bytes:9626 (9.6 KB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1280 (1.2 KB)  TX bytes:1280 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:37:e2:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


...any suggestions? wifi works fine. I'm using an usus Eeepc HA1005.

---

### Post by ScousaJAY on 2011-07-10
hi arnicane,

sounds like we might have the same problem  on the same system, a 1005HA..however, im using 11.04 (natty). i had problems with both the wireless and wired connection but i managed to get the wireless working, im still waiting to see if anyone answers my thread reguarding the wired ethernet,

is your ethernet network adapter an Atheros AR8132  ?   


[http://ubuntuforums.org/showthread.php?t=1800188](http://ubuntuforums.org/showthread.php?t=1800188)


im gonna keep an eye on your thread aswel just to see if we can get any answers :)

---

### Post by arnicainthemembrane on 2011-07-10
Yeah and Yeah, I've got 11.04 running fine, and the wifi is fine too, just nothing on the wired. Judging by how many people have looked at my post so far I'd venture to suggest it isn't an easy fix...

---

### Post by ScousaJAY on 2011-07-10
oh you have 11.04 also, i was looking on the info next to your post and it says your using 9.10 lol :)... 

i hope we can get it going, wireless is too slow for downloading movies ha

---

