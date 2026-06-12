---
title: "Cannot connect to internet through Ubuntu12.04(Unity)"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by abrarrakib on 2012-06-16
Hi,
I have recently installed Ubuntu 12.04(Unity)64-bit on my desktop which also has Windows 7(dual boot).
My internet connection is a cable modem one provided by Hathway which requires a login username & password.

I am able to connect to the internet in Windows but not through Ubuntu. I have to login (connect) to the internet through Windows, restart the system in Ubuntu, only then can I access the internet in Ubuntu. Kindly let me know how can I access the internet directly through Ubuntu. I mean is there any network setting that need to be set or changed. I'm providing some of my details as follows.
Thanking you.


abrar-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:82:59:3d  
          inet addr:27.7.49.241  Bcast:27.7.55.255  Mask:255.255.248.0
          inet6 addr: fe80::223:54ff:fe82:593d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2280158 (2.2 MB)  TX bytes:378116 (378.1 KB)
          Interrupt:47 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84368 (84.3 KB)  TX bytes:84368 (84.3 KB)


abrar-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


abrar-PC:~$ route -n
Kernel IP routing table

Destination     Gateway        Genmask          Flags    Metric    Ref     Use Iface
-----------------------------------------------------------------------------------
0.0.0.0         27.7.48.1      0.0.0.0            UG       0        0      0  eth0
27.7.48.0       0.0.0.0        255.255.248.0      U        1        0      0  eth0
169.254.0.0     0.0.0.0        255.255.0.0        U        1000     0      0  eth0

---

### Post by praseodym on 2012-06-16
Hi,

start the network-manager from terminal

```
gksu nm-connection-editor
```
and add your login/PW in "DSL"

---

### Post by sachinjr on 2012-10-22
> **praseodym said:**
> Hi,

start the network-manager from terminal

```
gksu nm-connection-editor
```
and add your login/PW in "DSL"

Hi I am having the same problem as the original poster, but the above solution did not work for me. Hathway internet works in Windows 7 but not in Ubuntu 12.04 (i have a dual boot laptop). 

Hathway did not provide any user name and password. So i dont know what to enter in the network manager dialog box. 

For windows, the internet connection worked without any intervention on my part. i just plugged in the ethernet cable and it started to work. is there anything in Ubuntu that needs to be done that I am missing?
thanks.

---

