---
title: "Inernet Connectivity Issues Ubuntu 8.04"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by vasquezj on 2009-05-14
I installed the Ubuntu 8.04 into a Dell Optiplex EX170 and I am not able to connect to the internet. This behaivor is the same regardless of setting the network on remote, dhcp or static. 
 
In each configuration, I am able to ping the internal subnet and internet (i.e. pinging [www.yahoo.com]("http://www.yahoo.com/") and [www.google.com]("http://www.google.com/")). But when I try to get updates for the system, the system is not able to reach the sites. All ubuntu sites are able to be resolved by the DNS and they can be reach by pinging from a terminal. 
 
I have tried all that I can think of but I am still unable to reach the internet through firefox. 
 
I would appreciate any ideas.... 
 
P.S. Firefox is able to open internal sites (intranet).. Also, ethtool and lshw -C network shows that the OS was able to recognized the hardware and applied the respective drivers.
 
Thanks ...
 
Jaime :confused::confused:

---

### Post by Crafty Kisses on 2009-05-14
So just to confirm this because I'm not quite understanding the problem, you can ping websites and you actually receive replies from the server, but you can't browse when you open Firefox?

---

### Post by Peter09 on 2009-05-14
Looks like a routing problem, can you show the output of

```
route
```

---

### Post by vasquezj on 2009-05-14
You are correct. I am able to ping (internal and the internet using DNS or IP) and access internal sites but I not able to access any internet sites  using firefox.

---

### Post by Peter09 on 2009-05-14
Also you need to check your DNS servers are setup in your router

---

### Post by vasquezj on 2009-05-14
They are setup with the correct DNS as I have other computers accessing the ineternet without any problem.

---

### Post by Peter09 on 2009-05-14
Alos if you are confident about DNS go to firefox->edit->preferences->Advanced->network

and check that you have not set a manual proxy. It should be system proxy (assuming that you have no proxy)

---

### Post by Crafty Kisses on 2009-05-14
Can you please post the results of the following?
```
route
```
I'd also like to know if you can view Google by opening Firefox and entering this in the navigation bar:
```
74.125.45.100
```
See if you can access Google that way, also you should see if you can resolve an address by running the following:
```
nslookup google.com
```

---

### Post by vasquezj on 2009-05-14
Sorry for the delay, I had to wait to get into the office to get the commnad outputs. 
 
here is the output from the commands. 
jaime@bspark:/opt/openfire/plugins$ nslookup google.com
Server: 192.168.1.2
Address: 192.168.1.2#53
Non-authoritative answer:
Name: google.com
Address: 209.85.171.100
Name: google.com
Address: 74.125.67.100
Name: google.com
Address: 74.125.45.100
jaime@bspark:/opt/openfire/plugins$ 
 
jaime@bspark:/opt/openfire/plugins$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 eth1
link-local * 255.255.0.0 U 1000 0 0 eth1
default 192.168.1.250 0.0.0.0 UG 100 0 0 eth1
jaime@bspark:/opt/openfire/plugins$ 
 
Also, when I try to browse to google.com or to the ip 74.125.45.100, the browser does not display anything. It just says loading.... and does not present anything.
 
192.168.1.250 is my main firewall/router and 192.168.1.2 is my internal DNS. 
 
In addton, I just enabled remote desktop in the ubuntu machine and I am able to connect without any problem. Yet, I am not able to browse the internet. 
 
P.S. output from other commands:
root@bspark:/# ethtool eth1
Settings for eth1:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Half
Port: MII
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: g
Wake-on: g
Current message level: 0x00000007 (7)
Link detected: yes
root@bspark:/# 
 
root@bspark:/# lshw -C network
*-network 
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth1
version: 02
serial: 00:11:11:78:5f:b3
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A ip=192.168.1.240 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
root@bspark:/# 
 
root@bspark:/# lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
root@bspark:/#
 
jaime@bspark:/etc$ ifconfig
eth1 Link encap:Ethernet HWaddr 00:11:11:78:5f:b3 
inet addr:192.168.1.240 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:23581 errors:0 dropped:0 overruns:0 frame:0
TX packets:23682 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1785171 (1.7 MB) TX bytes:17032212 (16.2 MB)
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:76443 errors:0 dropped:0 overruns:0 frame:0
TX packets:76443 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:228137211 (217.5 MB) TX bytes:228137211 (217.5 MB)
jaime@bspark:/etc$ 
 
It appears that I need to have the loopback active for the system to respond to pings. Is this how it should be???
 
Multicast is defined as:
 
lo  member:1 Group:ALL-SYSTEMS.MCAST.NET
eth1 member:1 Group:224.0.0.251
eth1 member:1 Group:ALL-SYSTEMS.MCAST.NET

---

