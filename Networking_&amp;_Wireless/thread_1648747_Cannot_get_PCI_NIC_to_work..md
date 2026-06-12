---
title: "Cannot get PCI NIC to work."
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by brad82 on 2010-12-19
Hey all,

I recently purchased a TP-Link Gigabit PCI Network Adapter for my fileserver, due to its Gigabit potential.

I installed the card, and I can see it when I run lspci, however I cannot get a network connection through it.

I do have a onboard NIC that works.

I have added a section in /etc/network/interfaces for eth1 and then done the ritual ifup eth1 (with a networking restart) but with no avail.

If I plug a cable into the onboard NIC I can access the server via both IPs .4/.5, but if I plug it into the PCI NIC it cant find the server.

Card: [http://www.overclockers.co.uk/showproduct.php?prodid=NW-016-TP](http://www.overclockers.co.uk/showproduct.php?prodid=NW-016-TP)
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:01:80:04:7e:e5  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr d8:5d:4c:81:5b:b0  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::da5d:4cff:fe81:5bb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4356 (4.3 KB)  TX bytes:468 (468.0 B)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2874 (2.8 KB)  TX bytes:2874 (2.8 KB)

```


lspci

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
```

01:04.0: PCI Card
01:08.0: Onboard NIC

---

### Post by brad82 on 2010-12-21
*Shameless Bump*

I know bumping is frowned upon here, but I cant find anything around relating to my problem, the strange thing is when I plug a cable in, the connection light illuminates, but also the action light flickers as though data is being transferred. However when I ping the device on either 192.168.0.4, or 192.168.0.5 I get no response if the cable is in the PCI NIC. If it is in the onboard NIC then I get a pingback from both IPs

---

### Post by grahammechanical on 2010-12-21
If eth1 is the PCI NIC, then according to ifconfig it is UP and RUNNING. Whereas, eth0 is only UP. I would say that you are connected using eth1. If you type in a terminal nm-tool you will find out the carrier speed of your active connections.

Regards.

---

### Post by brad82 on 2010-12-21
Ah ok, ill have a go with that see what happens!

Thanks

---

### Post by brad82 on 2010-12-24
Ok so I had another look at ifConfig, when I swap the cable over from the PCI card to the on board nic, obviously eth0 becomes RUNNING, now while eth0 is running the network connection will work as intended, and I can ping to and from another PC on the network. If I put it back in PCI card eth1 becomes RUNNING, however this time I cannot ping to/from the box.

Interestingly also when eth1 is running it is indeed receiving packets, but is not transmitting any. 

Any ideas as to what could be going wrong?


EDIT: I have run ifdown eth0 and everything seems to be running ok! (I guess this was maybe a bit of a n00b mistake to have both interfaces running?) :D

---

