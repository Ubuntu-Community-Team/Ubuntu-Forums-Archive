---
title: "please help set up a wi-fi connection router-ubuntu 10.04"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by eR2 on 2011-08-01
I apologize for probably starting a topic that has been discussed over and over here but I feel I have reached a point where I won't be able to set up the network without the help of the community - so, please help!

A long story short: I've been using a 10.04 Ubuntu PC, it had (PPP&#1086;E) Internet connection and shared it with a Windows 7 netbook through a wi-fi card. I cannot recall how exactly I set this up (after reading so many forums) but I've set static ip and gateway in etc/network/interfaces for the PC. I also had to specify some of the wi-fi settings through "sudo iwconfig wlan0..." (essid, ad-hoc type etc.) every session, since I couldn't do it through Network Manager for some reason. The connection worked ok most of the time, but I couldn't set up protection for it, also when I attached to the PC my Windows smartphone I lost my Internet connection, and so on, so I decided to make it the right way.

I got a Zyxel Keenetic router, attached it to the Ubuntu PC through a cable, changed the gateway to 192.168.1.1, set up the MAC address for the router, the PPPoE and DHCP settings. Windows 7 immediately got on-line, Ubuntu couldn't. 
I changed interfaces to 
[spoiler]
interfaces
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
address 192.168.1.40
netmask 255.255.255.0
gateway 192.168.1.1
[/spoiler]

I tried setting up NM, it seemed to establish a wi-fi connection ('Auto' appeared before the essid name), but as soon as I detached the cable from the router, it lost the connection again, no ping. If I put the cable back and reboot, I can get on-line again, very low speed, though. 

At this point I realized I messed things up so much I couldn't fix it without the community help. I don't even understand where to start from.

PS More stupid questions:
1. Who has priority over who? Network Manager or interfaces? If I change smth in interfaces, it doesn't appear in the NM settings and vice versa, so what has more priority for the system? 
2. NM doesn't show my PPPoE connection - is this normal?
3. NM doesn't show my PC and router cable connection - is this normal?

Thanks!

---

### Post by chili555 on 2011-08-01
Network Manager and manual methods; e.g. /etc/network/interfaces seldom work and play well together. NM has a tight grip on networking and it will be difficult to wrest control in *interfaces*. Moreover, if you have set up the router with PPPoE information such as user and password, it shouldn't be necessary to do it again in *interfaces*:> auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
I'd think you could connect easily and quickly with NM and this *interfaces* file:```
auto lo
iface lo inet loopback
```> as soon as I detached the cable from the router, it lost the connection again, no ping. If I put the cable back and reboot, I can get on-line again, very low speed, though. It sounds like wired is working and wireless is not. Let's have a look at your wireless card details. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by eR2 on 2011-08-02
**chili555**
Thanks a lot for your detailed answer. I did just as you suggested - cleaned interfaces and NM immediately connected. Everything works now. Thanks for the NM vs. interfaces explanation - obviously I didn't realize how the two interacted.

Thanks again! Ashamed it was so easy :)

---

### Post by chili555 on 2011-08-02
No worries. I love when hard problems have easy answers! I'm glad it's all working as expected.

---

