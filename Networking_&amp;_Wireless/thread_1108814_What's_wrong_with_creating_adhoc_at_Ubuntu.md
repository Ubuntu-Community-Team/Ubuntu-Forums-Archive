---
title: "What's wrong with creating adhoc at Ubuntu?"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by binbash on 2009-03-28
Hey guys, i am using my old toshiba with fedora 10 to create my adhoc, and it works perfect.I just click create new wireless, name it etc , then edit it and select dhcp addresses only at ipv4 settings of adhoc.That is all.But at ubuntu jaunty or intrepid i can not create one(but i can connect of course).When i create it i can't connect to that pc (me and others).What is wrong with ubuntu?Does fedora use a special patch or ubuntu's network manager is crap?

---

### Post by superprash2003 on 2009-03-28
in your terminal type ifconfig and post output..so your able to create an adhoc network but not access its files? are you able to ping the other machine?

---

### Post by binbash on 2009-03-28
eth0      Link encap:Ethernet  HWaddr 00:1d:92:4b:92:c7  
          inet addr:94.54.36.125  Bcast:94.54.63.255  Mask:255.255.192.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:6271826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2211788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1906445565 (1.9 GB)  TX bytes:165032512 (165.0 MB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:156486 (156.4 KB)  TX bytes:156486 (156.4 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.105.1  Bcast:192.168.105.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.121.1  Bcast:172.16.121.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:70:8d:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-70-8D-5E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
        

No one can connect to that adhoc, even the machine which adhoc is created on.I tried all settings at ipv4 tab (i mean the method).I have a cable modem which is plugged in on ethernet.

I tried to connect it on 4 notebooks (3 ubuntu , 1 fedora 10) and 1 windows machine.All can connect to adhoc which is created by fedora 10.

---

