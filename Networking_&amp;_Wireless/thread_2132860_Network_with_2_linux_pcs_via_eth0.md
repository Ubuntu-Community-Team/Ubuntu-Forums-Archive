---
title: "Network with 2 linux pcs via eth0"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by luizgguidi on 2013-04-06
Hey guys,

I was wondering if anyone could help me setup a network between my two linux systems as I can't connect the two computers via eth0 with after a fresh system installation in one of them - the other system (xubuntu) should be working fine as I had it working before. The eth0 driver and cross over  cable is working properly as it connects to my internet router if I try  to get internet from it.

I have set  up IPs for both of them (different for each, using 'ifconfig'). I have  installed samba and its related packages. When I plug it in, it attempts  connection and I can ping each computer and even access its shared  directories but the connection is never 'established' and eventually  drops. I've set up IPv6 as ignore in both computers too

Here are some of the info that might be relevant/useful

sudo lshw -C network
```
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ad:c3:19
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=b44  driverversion=2.0 duplex=full latency=64 link=yes multicast=yes  port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:41:32:7c
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=b43  driverversion=3.5.0-17-generic firmware=666.2 ip=192.168.0.19 link=yes  multicast=yes wireless=IEEE 802.11bg
```

Also,
sudo ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:ad:c3:19  
          inet6 addr: fe80::215:c5ff:fead:c319/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1137808 (1.1 MB)  TX bytes:515515 (515.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:621507 (621.5 KB)  TX bytes:621507 (621.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:41:32:7c  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe41:327c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:957414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:821320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1190337678 (1.1 GB)  TX bytes:141410305 (141.4 MB)
```

And,
sudo gedit /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

Thanks a million!

---

### Post by moody_mark on 2013-04-06
From the ifconfig output above it looks like only the wireless interface has an ip address. It sounds like you are trying to connect the two machines directly? If so then you will need to configure a static IP on each and use a ethernet crossover cable. Ensure you see the link light on your interface cards, if you dont then there's a problem with your cable. Connecting to a router you'll need a normal (non-crossover) cable. See this for more information:

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

Its not clear if you have setup a static IP on each but you'll normally best doing this through network manager (right clicking the network icon on the toolbar and selecting "edit connections"). This page might give you some more information

[https://help.ubuntu.com/community/UbuntuLTSP/StaticIP](https://help.ubuntu.com/community/UbuntuLTSP/StaticIP)

---

### Post by luizgguidi on 2013-04-07
This is brilliant! Thanks a lot - worked perfectly!

---

