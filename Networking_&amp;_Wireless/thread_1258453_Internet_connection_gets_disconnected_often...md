---
title: "Internet connection gets disconnected often.."
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2009-09-05
My internet connection gets disconnected often and this is my plog output..

karthick@karthick-desktop:~$ plog
Sep  5 12:18:11 karthick-desktop pppd[3371]: local  IP address 59.92.105.4
Sep  5 12:18:11 karthick-desktop pppd[3371]: remote IP address 59.92.104.1
Sep  5 12:22:11 karthick-desktop pppd[3371]: No response to 4 echo-requests
Sep  5 12:22:11 karthick-desktop pppd[3371]: Serial link appears to be disconnected.
Sep  5 12:22:11 karthick-desktop pppd[3371]: Connect time 4.0 minutes.
Sep  5 12:22:11 karthick-desktop pppd[3371]: Sent 375760 bytes, received 2280021 bytes.
Sep  5 12:22:11 karthick-desktop pppd[3371]: Connection terminated.
karthick@karthick-desktop:~$ 

Help me to solve this problem..Thanks in advance

---

### Post by hal10000 on 2009-09-05
We need a little bit more info about your network configuration.
Wha kind of network adapter do you use (wireless or wired)?
Post the output of the commands [COLOR="Red"]ifconfig[/COLOR] and [COLOR="Red"]route[/COLOR]
Your ip-address looks very strange, it's not from the private address ranges, which would start with **192.168.X.Y**, **172.16.X.Y** or **10.X.Y.Z**

Do i understand right, sometimes you get a connection and sometimes not?

---

### Post by karthick87 on 2009-09-05
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:17:70  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:feab:1770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:643201 (643.2 KB)  TX bytes:76586 (76.5 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:689535 (689.5 KB)  TX bytes:689535 (689.5 KB)

route
karthick@karthick-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.96.24.1      *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by shredder12 on 2009-09-05
> **getyourkarthick said:**
> My internet connection gets disconnected often and this is my plog output..

karthick@karthick-desktop:~$ plog
Sep  5 12:18:11 karthick-desktop pppd[3371]: local  IP address 59.92.105.4
Sep  5 12:18:11 karthick-desktop pppd[3371]: remote IP address 59.92.104.1
Sep  5 12:22:11 karthick-desktop pppd[3371]: No response to 4 echo-requests
Sep  5 12:22:11 karthick-desktop pppd[3371]: Serial link appears to be disconnected.
Sep  5 12:22:11 karthick-desktop pppd[3371]: Connect time 4.0 minutes.
Sep  5 12:22:11 karthick-desktop pppd[3371]: Sent 375760 bytes, received 2280021 bytes.
Sep  5 12:22:11 karthick-desktop pppd[3371]: Connection terminated.
karthick@karthick-desktop:~$ 

Help me to solve this problem..Thanks in advance

I used to have a similar problem while using broadband.. and I had to turn off the modem and then switch it on again..
Its jst a temporary solution and pretty annoying too..
but I never got a permanent solution to the problem..

---

