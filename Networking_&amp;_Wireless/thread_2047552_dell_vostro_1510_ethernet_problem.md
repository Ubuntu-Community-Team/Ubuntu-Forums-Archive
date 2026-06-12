---
title: "dell vostro 1510 ethernet problem"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by ai.karanam on 2012-08-25
hi,
i recently dual boot my system with window 7 and ubuntu 12.04...... i can't access internet through wired connection...inspite of lan cable in the socket....it says network cable unplugged....but i can access the net from windows 7......
Actually,during the instllation phase for ubuntu when it tries to check the network connection.....it was giving the same message.....that network cable is unplugged...

previously...i was using ubuntu 10.04 along with windows xp.....then it was working fine.....

here is some information u may find useful.....
ifconfig -a
---------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:21:70:e7:cc:93  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105328 (105.3 KB)  TX bytes:105328 (105.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:dc:04:ed  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
------------------------------------------------------------------

sudo lshw -class network


 *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:e7:cc:93
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=no multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:f8620000-f862ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2b:dc:04:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---------------------------------------------------------------------

sudo ethtool eth0


Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: pumbg
    Current message level: 0x00000033 (51)
    Link detected: no
---------------------------------------------------------------------

---

### Post by ai.karanam on 2012-08-25
hi,
i recently dual boot my system with window 7 and ubuntu 12.04...... i  can't access internet through wired connection...inspite of lan cable in  the socket....it says network cable unplugged....but i can access the  net from windows 7......
Actually,during the instllation phase for ubuntu when it tries to check  the network connection.....it was giving the same message.....that  network cable is unplugged...

previously...i was using ubuntu 10.04 along with windows xp.....then it was working fine.....

here is some information u may find useful.....
ifconfig -a
---------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:21:70:e7:cc:93  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105328 (105.3 KB)  TX bytes:105328 (105.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:dc:04:ed  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
------------------------------------------------------------------

sudo lshw -class network


 *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:e7:cc:93
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=no  multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:f8620000-f862ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2b:dc:04:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43  driverversion=3.2.0-23-generic-pae firmware=N/A link=no multicast=yes  wireless=IEEE 802.11bg

---------------------------------------------------------------------

sudo ethtool eth0


Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: pumbg
    Current message level: 0x00000033 (51)
    Link detected: no
---------------------------------------------------------------------

---

### Post by mörgæs on 2012-08-26
Threads merged. Please don't double-post.

Do you get wired internet access in a live boot of (for example) Xubuntu 12.04?

---

### Post by ai.karanam on 2012-08-27
i don't have access to xubuntu 12.04. No new versions of ubuntu are supporting my hardware....

---

### Post by mörgæs on 2012-08-28
When I mentioned double-posting I also meant posting on more than one web site. As you can see, it does not make people more willing to help.

---

### Post by ai.karanam on 2012-08-28
I deeply regret inconvenience caused by me. I was desperate. I was need of immediate solution . so is there any solution for my problem.

---

### Post by ai.karanam on 2012-08-28
thanx for the support,
i had solved the problem....hi guys if u have same problem...just visit the following link-


[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

and select appropriate package.extract it and run the shell file...
it removes any new driver installed and replaces with the supported version....

:-)   ):P

---

### Post by ai.karanam on 2012-08-29
i think the problem is not solved yet. it was working for the first time. But, when i restarted my system it is again stopped to detect the cable. same problem persists..

---

