---
title: "wifi error message"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by tongsengpakronilezat on 2011-08-17
Today i reinstalled my Ubuntu 11.04 on my Acer Aspire L-3600, because i failed to activate my wifi connection last week. Now, i'm writing this message using cable connection. But, my wifi still fail. Please help me to overcome this. Here are my data :

iwconfig :

lo        no wireless extensions.
eth0      no wireless extensions.

ifconfig -a :

eth0      Link encap:Ethernet  HWaddr 00:1c:25:2e:44:68  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe2e:4468/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18394890 (18.3 MB)  TX bytes:1281012 (1.2 MB)
          Interrupt:18 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

sudo lshw -C network :

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe9fc000-fe9fffff
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 00
       serial: 00:1c:25:2e:44:68
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.5-7 ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:feae0000-feafffff ioport:ec00(size=32)

Then, i also do as suggested in the 'sticky thread' : System > Administration > Synaptic Package Manager > Search:  firmware-b43-lpphy-installer > Click Mark > Click install >  Close.
 Also failed.

Before that, i've tried < [http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4311](http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4311) > as suggested in the network supported hardware list, download the file but then stopped cause i didn't know what to do . . .

I know i have the wifi device, i don't have the correct driver ... but, i don't know how to . . .
Please somebody give me any hints  . . . 


thanks . . .

---

