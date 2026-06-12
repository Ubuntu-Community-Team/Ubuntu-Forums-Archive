---
title: "It says I'm connected but I can't use the internet."
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Adnrw on 2009-07-29
For some reason it's not letting me acceses the internet although it says I'm connected. 
Also I was using the internet earlier. 
><
Any help would be apreciated.

---

### Post by Iowan on 2009-07-30
Wired or wireless? Please post results of **ifconfig -a**.

---

### Post by kornyam on 2009-07-30
See if you get a response from:

ping -c3 google.ca

If you do, it might be a Firefox issue. See if you have the "Work Offline" option checked off.

---

### Post by AdnrwV2 on 2009-07-31
It wouldn't let me log in so I had to use this account.
.___________.
 
And for some reason when I check the connection info the speed changes from 1Mb/s to 54Mb/s and I don't know why.
 
@Iowan; I'm wireless
```
andrew@AdnrwPC:~$ ifconfig -a
eth0     Link encap:Ethernet  HWaddr 00:11:09:d7:f7:5d  
 
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:23 Base address:0x4000
 
lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
 
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
pan0     Link encap:Ethernet  HWaddr fe:ef:6f:28:63:07 
         BROADCAST MULTICAST  MTU:1500  Metric:1
 
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
wlan0    Link encap:Ethernet  HWaddr 00:1e:2a:bb:8e:33 
         inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
         inet6 addr: fe80::21e:2aff:febb:8e33/64 Scope:Link
 
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
 
         RX packets:18 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:1000 
         RX bytes:2011 (2.0 KB)  TX bytes:6052 (6.0 KB)
 
wmaster0  Link encap:UNSPEC  HWaddr 00-1E-2A-BB-8E-33-65-33-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
 
 
@kornyam; No responce and not working offline.

---

### Post by Iowan on 2009-07-31
Gateway/DNS problem? there are a couple of threads ([here]("http://http://ubuntuforums.org/showthread.php?t=1164868") is one) that recommend copying /etc/resolv.conf file from the Live CD.

---

### Post by AdnrwV2 on 2009-08-01
I don't know what it is :/
I looked at that thread and I tried to do what they suggested (copying the resolv.conf) but it didn't work.
D:

---

