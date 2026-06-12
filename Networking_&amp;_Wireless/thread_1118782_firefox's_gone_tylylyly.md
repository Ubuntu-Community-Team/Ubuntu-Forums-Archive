---
title: "firefox's gone tylylyly"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by sn0m on 2009-04-07
Internet is so painfully slow. Firefox gone loopy since last update. I've tried so many times to post here, but Firefox thinks of it for about ten minutes and after that it asks me what to do with a PHP file....:mad: I'm posting this via internet explorer by the way.
Is this a bad joke or a big mama's posterior size bug...
Why does an upgrade have to be such a pain....
Anyway enough ranting, any good samaritan out there to help me with it.
Regards
Sokol

---

### Post by superprash2003 on 2009-04-07
in your terminal type ifconfig and post output..consider using opendns servers as well

for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by sn0m on 2009-04-08
sn0m@sn0m-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:4e:75:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15341 (15.3 KB)  TX bytes:15341 (15.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:86:b4:75  
          inet addr:192.168.15.228  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe86:b475/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:571110 (571.1 KB)  TX bytes:139183 (139.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-86-B4-75-34-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Stupendoussteve on 2009-04-08
I would try backing up your old profile and seeing if that helps, sometimes the profiles get a little bloated and buggy. They are stored in .mozilla, renaming that folder should have Firefox start a fresh profile.

---

