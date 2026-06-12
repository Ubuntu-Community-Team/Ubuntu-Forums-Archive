---
title: "can't connect to internet after acpi update"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2009-01-18
Yesterday I installed, I think it was, an acpi update with update manager. It was the only update available, so I'm fairly certain the problem is down to that.

Since I restarted, I can't connect to the internet. I can connect to the network, and it says there is network activity both ways, but I can't connect to the internet or intranet. Firefox and opera just hang on a blank white screen.

I am on a university network, so I have to log in through the intranet (and through a proxy server I think), but doing this has never been a problem before.

---

### Post by superprash2003 on 2009-01-18
go to the terminal and type ifconfig and post output..

---

### Post by themusicalduck on 2009-01-18
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:14:85:0c:11:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

eth1      Link encap:Ethernet  HWaddr 00:06:4f:5c:03:ca  
          inet addr:172.16.73.97  Bcast:172.16.73.255 Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe5c:3ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1166278 (1.1 MB)  TX bytes:87259 (87.2 KB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7828 (7.8 KB)  TX bytes:7828 (7.8 KB)

I'm using eth1.

---

### Post by themusicalduck on 2009-01-18
bump

EDIT: nevermind, it magically started to work again.. very strange.

---

### Post by oygle on 2009-01-18
I had exactly the same thing, see [http://ubuntuforums.org/showthread.php?t=1042755](http://ubuntuforums.org/showthread.php?t=1042755)

---

### Post by themusicalduck on 2009-01-18
How weird that it fixed itself after a few reboots.. I just hope it continues to work when I start it up again tomorrow!

---

