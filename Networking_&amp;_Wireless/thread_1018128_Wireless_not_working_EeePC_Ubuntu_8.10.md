---
title: "Wireless not working EeePC Ubuntu 8.10"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Zipper-Shut on 2008-12-21
Hi, My Name is Emilie... I've been using linux for awhile but im still a newbie at alot of things....

But, i need help.

I just installed Ubuntu 8.10 on my EeePC 900, and i can get the wired connection working, just not the wireless....
I googled the problem and found [this]("https://help.ubuntu.com/community/EeePC/Fixes") to be of some help....

It now shows under the two connection computers panel a wireless network option.... but i still cannot get the wireless to work.
I did run into a problem with the help document though.... > "sudo modprobe ath5k" that part.



Am i doing something wrong??

Here is my ifconfig:
emilie@emilie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:a2:90:0c  
          inet addr:10.120.208.191  Bcast:10.120.209.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1676 (1.6 KB)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:05:74:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-05-74-94-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)





Need anything else to help me please ask... and give instructions because like i said before, i'm still a newbie, even though ive been around linux for awhile.

Thank you in advance!
Emilie

---

