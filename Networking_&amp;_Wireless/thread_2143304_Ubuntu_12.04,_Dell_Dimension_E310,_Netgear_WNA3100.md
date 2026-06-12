---
title: "Ubuntu 12.04, Dell Dimension E310, Netgear WNA3100/Linksys WUSB11"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by lurkerjoe on 2013-05-08
I'm busting out my old desktop for use in the kitchen and decided to try Ubuntu as a new OS. Everything installed perfectly, except I'm having wireless networking problems. I have two USB adapters:

Netgear WNA3100
Linksys WUSB11 v3

The WUSB11 will connect to unprotected/WEP networks with Ubuntu 13.04, however I was unable to connect to WPA encrypted networks. Ubuntu would prompt for the network password, I would enter it, and the "connect" button would not click. I could never get past entering the password. I was thinking the adapter might have been the problem, so I purchased the WNA3100 and found no success with that. I then downgraded to Ubuntu 12.04 32-bit. The WNA3100 does nothing. The WUSB11 detects networks, but will not connect. I installed ndiswrapper and have scrounged through countless forums to try to get the Netgear adapater running. 

Right now I am wired. I was following [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) . I hit a roadblock at step #3. When I use *sudo lshw -c network*, I don't see my wireless device. 

[EDIT] Which is very confusing for me. Why will *lsusb* and *ndiswrapper -l* recognize the device, but *lshw -c network* wont? 

ALSO, *ndiswrapper -v *concerns me.

```

ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
joseph@joseph-Dell:~$ 

```

nidswrapper -l

```
bcmn43xx32 : driver installed
    device (0846:9020) present
bcmwlhigh5 : driver installed
    device (0846:9020) present
joseph@joseph-Dell:~$ ^C
joseph@joseph-Dell:~$ 


```

lsusb

```
Bus 001 Device 008: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joseph@joseph-Dell:~$ ^C
joseph@joseph-Dell:~$ 


```

sudo lshw -c network


```
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:16:76:95:c3:07
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.109 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfcef000-dfceffff ioport:dcc0(size=64)
joseph@joseph-Dell:~$ ^C
joseph@joseph-Dell:~$ 

```




I've marked this thread SOLVED. I ended up ditching both adapters and purchasing the Netgear Range Extender (WN2000RPT) and am operating with a wired/wifi connection. Working beautifully.

---

