---
title: "wireless card is driving me insane!!!!!!!!!!!!!!"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by colinireland on 2009-09-02
Hello,

I am running ubuntu 9.04 on a Dell 1545 with the bcm4312 wireless card. I have been having a very strange problem with my wireless card. Every so often it seems to just stop working. The computer recognises that it is there as 

lspci | grep BCM gives:
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

ifconfig eth1 gives:
 Link encap:Ethernet  HWaddr 00:24:2c:71:a0:55  
          inet6 addr: fe80::224:2cff:fe71:a055/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 


If I go to System > Administration > Hardware Drivers it tells me that the broadcom STA driver is activated and currently in use. 
However, when I click the icon near the clock to connect to a wireless network it shows nothing!

**Wired Network**
disconnected
**Wireless Networks**
------------------
VPN Connections >
------------------
Connect to a hidden...........

If I plug in my external wireless card I get:

**Wired Network**
disconnected
**Wireless Network (Dell BCM4312 802.11b/g)**
**Wireless Network (Linksys WUSB54G)**
* Home Network
----------------------------------------------------
VPN Connections    >>
---------------------------------------------------
etc.................

I used to be able to resolve this by booting to the 2.6.28-14 kernel but now nothing but the loopback address is listed under ifconfig and the system > administration > hardware drivers shows nothing. This is really driving me crazy. I have had this problem a couple of times before and I dont know what to do. It is a new laptop so I didnt mind doing a fresh install the first few times. Can anybody explain to me what is going on and how I can sort this out once and for all. 

Thanks Colin

---

### Post by hal10000 on 2009-09-02
Maybe the b43 driver from the linux-backports package can help you. (If you don't have them already installed)

---

