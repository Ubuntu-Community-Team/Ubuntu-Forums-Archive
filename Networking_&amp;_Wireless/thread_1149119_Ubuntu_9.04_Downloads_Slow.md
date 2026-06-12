---
title: "Ubuntu 9.04 Downloads Slow"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by xtjacob on 2009-05-04
I recently put Ubuntu 9.04 on my computer with a WG111v2 and WPA Personal. It says it works out of the box and the Internet works fine but when I download something it starts out fast at around 400 kb/s and then drops to 2651 B/s and in one case it got down to 728 B/s. Output of ifconfig is:
```

eth0      Link encap:Ethernet  HWaddr 00:13:72:d6:b6:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:14:6c:6c:68:2b  
          inet addr:192.168.200.123  Bcast:192.168.200.255    Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe6c:682b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:253119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369722540 (369.7 MB)  TX bytes:16563002 (16.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-6C-6C-68-2B-38-32-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Any help will be appreciated.

---

### Post by umaxtu on 2009-08-08
I have the exact same problem

---

### Post by wojox on 2009-08-08
Try going to System > Admin > Software Sources
First Tab;
Look for Download from: Pick a server closer to you.

---

### Post by firen on 2009-08-08
Try googling for some online bandwidth speed testing services and see if it reports similar stats.

---

### Post by dsiddens on 2009-11-14
The following is a cut and paste from my recent post at Launchpad bug # 482917.


I'm using a Thinkpad 43p, 2GB, and Ubuntu 9.04. The dowload speeds, as reported by Ubuntu's System Monitor runs in the 20 to 80 Kib/s. Mostly around 35Kib/s. The ISP (Century Link) sent out a tech and he reported that the line was good (above a minimum of 9Mb/s. We actually were getting slightly above 11Mb/s on some other machines. We tried three other computers all of which were running some issue of Windows XP. The XP machines all clocked download speeds above 9Mb/s using Speakeasy.net in either a hard wired or WiFi connection.

I just ran another speed test and compared the result to the Ubuntu System Monitor: While the external site said about 54Kib/s, System Monitor reported about 12Kib/s.

This slow rate is observed with fire fox, thunderbird, pan.

Also, I don't know if this is a related or different problem, but sometimes system performance slows to a crawl. When I check System Monitor, it shows the CPU running 100%. When I look at what is running the two top consumers of CPU cycles are Firefox and System Monitor to the additive measure of about 80%. The slow download speed is not directly related to Firefox being open or not, e.g., Pan is downloading, Firefox is not opened... slow download speed. Or, Firefox is downloading and Pan is not opened... same slow download speed.

ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 9.04
Package: firefox-3.0 3.0.15+nobinonly-0ubuntu0.9.04.1
ProcEnviron:
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: firefox-3.0
Uname: Linux 2.6.28-16-generic i686

**** added to this post****

doug@drakus-captain-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:41:10:fd:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:c9:2a:00  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fec9:2a00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:13037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8543 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5807651 (5.8 MB)  TX bytes:1647264 (1.6 MB)
          Interrupt:21 Base address:0x2000 Memory:a8401000-a8401fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50200 (50.2 KB)  TX bytes:50200 (50.2 KB)

doug@drakus-captain-laptop:~$

---

