---
title: "Realtek RTL8190 802.11n Wireless LAN Driver?"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by Threaten on 2010-08-06
Hello. I just recently installed Ubuntu (today, actually with some help), and now I would like to get it functioning. I currently have been using a temporary USB Wireless receiver, which I cannot use for very much longer.

I was hoping on getting a driver for my installed PCI wireless card (Realtek RTL8190 802.11n Wireless LAN). 

I have looked on Realtek, and around the internet, but I cannot seem to find an answer. How can I solve this issue?

---

### Post by Threaten on 2010-08-12
This is bad form, but I am double posting because this is a severe issue that I really need help on. 

I would really appreciate someone!

PLEASE!

---

### Post by nanonils on 2010-08-12
What is the rest of your hardware? What exactly is the problem?
I somehow must have subscribed to your thread because I was quite desperate with my realtek card as well. I had a simple dns issue in the end: [http://ubuntuforums.org/showthread.php?p=9693389#post9693389](http://ubuntuforums.org/showthread.php?p=9693389#post9693389)

---

### Post by Threaten on 2010-08-12
Well as for your hardware question, what type of stuff are you looking for?

I am using a WNDR3100 (I think, maybe WNDR3300) Netgear router. Other than that, I can't think off the top of my head...hold tight while I install Speccy under Wine...but I'm not really sure what you are looking for. I am no professional computer user, and a lot of IP and NIC jargon confuse the hell out of me.

Thank you for your response, and I will try to gain something out of your thread.

---

### Post by Threaten on 2010-08-12
Well I am linked to a WNDR3100 Netgear router...other than that what "hardware" information are you looking for?

---

### Post by nanonils on 2010-08-13
Like I did in my first post linked above you need to post specs and output from some terminal commands here (use Sudo followed by the command). You have to do that while not connected to the internet I think (ie not LAN) then reconnect and then post your results).
Here is the sticky with the instructions: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Threaten on 2010-08-15
Alright. Here is my "log" as requested.

1 ) Machine Brand and Model (PC/Laptop):
HP Pavilion a6430f PC
NOTE: I am using an installed PCI Network Card.


2 ) Wireless Brand, Model and Wireless Chipset:
Realtek RTL8190 802.11n Wireless LAN is the name of the NIC. 
01:0a.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190


3 ) check interface:

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:df:dd:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1716 (1.7 KB)  TX bytes:1716 (1.7 KB)

4 ) Check for modules:
CANT FIND MY MODULE


5 ) Kernel boot messages

[   27.045621] wlan0: direct probe to AP 00:1f:33:b4:7f:68 (try 1)
[   27.045660] wlan0: deauthenticating from 00:1f:33:b4:7f:68 by local choice (reason=3)
[   27.133501] wlan0: direct probe to AP 00:1f:33:b4:7f:67 (try 1)
[   27.138129] wlan0: direct probe responded
[   27.138134] wlan0: authenticate with AP 00:1f:33:b4:7f:67 (try 1)
[   27.139728] wlan0: authenticated
[   27.139754] wlan0: associate with AP 00:1f:33:b4:7f:67 (try 1)
[   27.140977] wlan0: RX AssocResp from 00:1f:33:b4:7f:67 (capab=0x11 status=0 aid=1)
[   27.140980] wlan0: associated
[   27.144746] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.860018] wlan0: no IPv6 routers present
[   38.220828] wlan0: deauthenticating from 00:1f:33:b4:7f:67 by local choice (reason=3)
[   50.779936] wlan0: deauthenticating from 00:1f:33:b4:7f:67 by local choice (reason=3)
[   51.020012] wlan0: direct probe to AP 00:1f:33:b4:7f:67 (try 1)
[   51.021021] wlan0: direct probe responded
[   51.021025] wlan0: authenticate with AP 00:1f:33:b4:7f:67 (try 1)
[   51.022125] wlan0: authenticated
[   51.022143] wlan0: associate with AP 00:1f:33:b4:7f:67 (try 1)
[   51.023125] wlan0: RX AssocResp from 00:1f:33:b4:7f:67 (capab=0x11 status=0 aid=1)
[   51.023127] wlan0: associated
[   63.205854] wlan0: deauthenticating from 00:1f:33:b4:7f:67 by local choice (reason=3)
[  307.411490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  322.982636] wlan0: direct probe to AP 00:1f:33:b4:7f:68 (try 1)
[  322.982692] wlan0: deauthenticating from 00:1f:33:b4:7f:68 by local choice (reason=3)
[  323.071259] wlan0: direct probe to AP 00:1f:33:b4:7f:67 (try 1)
[  323.072251] wlan0: direct probe responded
[  323.072260] wlan0: authenticate with AP 00:1f:33:b4:7f:67 (try 1)
[  323.073296] wlan0: authenticated
[  323.073331] wlan0: associate with AP 00:1f:33:b4:7f:67 (try 1)
[  323.075012] wlan0: RX AssocResp from 00:1f:33:b4:7f:67 (capab=0x11 status=0 aid=1)
[  323.075018] wlan0: associated
[  323.079583] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  333.848023] wlan0: no IPv6 routers present
[  528.028089] wlan0: deauthenticating from 00:1f:33:b4:7f:67 by local choice (reason=3)
[  982.435284] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  995.220444] wlan0: deauthenticating from 00:1f:33:b4:7f:68 by local choice (reason=3)
[  995.306825] wlan0: direct probe to AP 00:1f:33:b4:7f:67 (try 1)
[  995.308414] wlan0: direct probe responded
[  995.308422] wlan0: authenticate with AP 00:1f:33:b4:7f:67 (try 1)
[  995.309649] wlan0: authenticated
[  995.309690] wlan0: associate with AP 00:1f:33:b4:7f:67 (try 1)
[  995.311043] wlan0: RX AssocResp from 00:1f:33:b4:7f:67 (capab=0x11 status=0 aid=1)
[  995.311049] wlan0: associated
[  995.316950] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1006.129013] wlan0: no IPv6 routers present
[ 1018.792875] wlan0: deauthenticating from 00:1f:33:b4:7f:67 by local choice (reason=3)
[ 1276.563311] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1290.553408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1303.430940] wlan0: deauthenticating from 00:1f:33:b4:7f:68 by local choice (reason=3)
[ 1303.522868] wlan0: direct probe to AP 00:1f:33:b4:7f:67 (try 1)
[ 1303.524453] wlan0: direct probe responded
[ 1303.524457] wlan0: authenticate with AP 00:1f:33:b4:7f:67 (try 1)
[ 1303.525910] wlan0: authenticated
[ 1303.525932] wlan0: associate with AP 00:1f:33:b4:7f:67 (try 1)
[ 1303.527423] wlan0: RX AssocResp from 00:1f:33:b4:7f:67 (capab=0x11 status=0 aid=1)
[ 1303.527427] wlan0: associated
[ 1303.533381] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1313.584016] wlan0: no IPv6 routers present


6 ) Network configuration

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:bc00(size=256) memory:fdefe000-fdefefff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:2a:d9:f1:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.4 multicast=yes wireless=IEEE 802.11abg

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:bc00(size=256) memory:fdefe000-fdefefff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:2a:d9:f1:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.4 multicast=yes wireless=IEEE 802.11abg

I want the one with Realtek in it to work.


7 ) Scan for networks:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

8 ) Ubuntu Version: 

Description:	Ubuntu 10.04.1 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit): 

2.6.32-24-generic i686

10 ) Restarting the network:

* Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.



ONCE AGAIN, Thank you very much to anyone who has the patience to go read through this and continue to help me. It is very appreciated.

---

