---
title: "Unable to connect to internet"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by malel on 2010-01-15
I really need some help here . My ISP is 'connect' in Fiji but I can only get on to the internet using MS XP on my laptop. My desktop is running Ubuntu 9.04 and I am at my wits end trying to get it to work. The modem in one from 'Connect' with only one port so I have to unplug MS XP and plug in my Ubuntu . When in Ubuntu it keeps telling me that I am disconnected.
The modem has a tag on the back with the following:
CNT240-A11
R5022-0092-01
730983000273
With Ubuntu I am plugged into a ETH card
Any help would be appreciated thanks

---

### Post by alexfish on 2010-01-15
Hi
What type of Modem is it, how does it connect to the computer, ie' : serial , usb  etc

or where does the connection goto after the modem

---

### Post by malel on 2010-01-15
Ithink the modem is hybrid as t only has 'connect' on the top of it. It connects to the computer via ethernet card

---

### Post by superprash2003 on 2010-01-15
post output of **ifconfig** from your terminal , just to make sure your pc is getting an ip address

---

### Post by malel on 2010-01-16
I am not able to post anything because my Ubuntu is not connected to the internet and that is what is frustrating me. I am using Win XP to connect. I will try and type it out longhand.

ifconfig   (Ubuntu 9.04)

eth0    Link encap:Ethernet HWaddr 00:01:6c:a2:eb:cd
          UP BROADCAST RUNNING MULTICAST  MTU:1500   Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0.0)   TX bytes:0 (0.0.0)
          Interrupt:19 Base address:0xe800


eth1    Link encap:ethernet HWaddr 00:0e:2e:c0:90:61
          Inet6 addr:  fe80::20e:2eff:fec0:9061/64 Scope:Lin k
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2400 (2.4 KB)  TX bytes:10600 (10.6 KB)
          Interrupt:19 Base address:0xec00



Lo      Link encap:Local loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6: addr:  ::1/128 Scpe:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:160 errors:0 dropped:0 overruns:0 frame:0
         TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:12512 (12.5 KB)  TX bytes:12512 (12.5 KB)




I hope you can make something out of that thanks

---

### Post by Iowan on 2010-01-16
Some modems "lock onto" a client MAC address and won't service another. You *might* need to turn the modem off for awhile, then back on.

---

### Post by malel on 2010-01-17
Yep I have tried that but makes no difference. I have also tried to connect a dynalink router but to no avail and I cannot get onto the internet to change some settings. Like ppoA to ppoE and I really dislike this Win XP.
BTW does anyone know anything about this modem that 'connect' here in fiji are using as it just will not let me connect to the internet . It keeps telling that the line is disconnected. The modem is a CNT240-A11. This modem allows me to connect with Win XP only.

---

### Post by malel on 2010-01-26
The problem is now solved  for me at any rate. The modem from 'connect' would not connect with anything else but MS XP . I have three 'routers' with me and although I could get the computers talking to them they would not connect to the ISP . I took a couple in to the ISP (Connect) and they reconfigured my D-Link DSL-504T modem and now Ubuntu works fine. Thank goodness as I was getting fed up with XP.
Thank you to those who replied to my cry for help.

---

