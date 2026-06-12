---
title: "Help Setting Up Wireless"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by gecus on 2009-03-11
Hello, I am using a 2Wire wireless network adapter
```
john@john-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 045e:009d Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
**Bus 002 Device 002: ID 055d:a230 Samsung Electro-Mechanics Co.** 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 001 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000 
``` 

And was following these directions:
```
https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
```
And got an error that ndiswrapper couldn't find WlanCIG.sys (I had the file under a different name)
So, I ran a check to see if it installed right:
```
john@john-desktop:~$ ndiswrapper -l
wlanuig : driver installed
john@john-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:29:53:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87000 (84.9 KB)  TX bytes:87000 (84.9 KB)

john@john-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
So, I went to remove the driver
using ```
ndiswrapper -r wlanuig
```
but I was thrown this:
```
john@john-desktop:~$ ndiswrapper -r wlanuig
Can't remove file /etc/ndiswrapper/wlanuig/1260:3886:0004:1630.5.conf (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
Can't remove file /etc/ndiswrapper/wlanuig/1260:3886.5.conf (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
Can't remove file /etc/ndiswrapper/wlanuig/1630:0005.F.conf (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
Can't remove file /etc/ndiswrapper/wlanuig/wlanuig.sys (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
Can't remove file /etc/ndiswrapper/wlanuig/1260:3886:0003:1630.5.conf (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
Can't remove file /etc/ndiswrapper/wlanuig/wlanuig.inf (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
Can't remove directory /etc/ndiswrapper/wlanuig (Permission denied) at /usr/sbin/ndiswrapper-1.9 line 126
couldn't delete /etc/ndiswrapper/wlanuig: Permission denied
john@john-desktop:~$ 

```

So, can anyone offer any help to get me going :\ ?
Kind of a newbie to Linux, this is my first distro but I couldn't stand Windows anymore as a novice programmer.

---

