---
title: "pppoe via wlan"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by ummah on 2009-02-06
Hi!
I've downloaded the ubuntuME and installed in my acer aspire 5520, but i have a problem with the wireless.
First it didn't recognized my hardware, but i did the configure with the drivers of windows with ndiswrapper. 
But the real problem is then when i type pppoconf, it output me:
> Sorry, I scanned 3 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process wich controls the modem
Any idea what's going on..
How do i solve this??

---

### Post by superprash2003 on 2009-02-06
post output of ifconfig from the terminal.. are you able to ping your router?

---

### Post by sedawk on 2009-02-06
I'm confused!

So far I have seen these setups:

1) DSL modem connected to a PC with a patch cable.
PPPoE settings are configured on the PC.

2) DSL modem and router (with or without WLAN) connected
with a patch cable.
In this case the router uses PPPoE to talk to the modem.
PPPoE settings are configured in the router.

3) all-in-one-box (modem and router and wireless)
Similar to 2, only the cable is replaced by an internal bus.


How does your setup differ from the above examples?
If you need PPPoE over wireless, my conclusion would be
you have a wireless DSL modem without embedded router?
Sounds funny!

---

### Post by ummah on 2009-02-06
ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:1b:38:73:d2:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4409 (4.4 KB)  TX bytes:4409 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:06:11:7e  
          inet6 addr: fe80::21f:3aff:fe06:117e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1600 (1.6 KB)  TX bytes:2142 (2.1 KB)
          Interrupt:19 Memory:d0400000-d0410000


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"WebSTAR"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.


lshw -C network
> *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:73:d2:1e
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:06:11:7e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:ab:8b:bd:98:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


dhclient wlan0
> Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:3a:06:11:7e
Sending on   LPF/wlan0/00:1f:3a:06:11:7e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by ummah on 2009-02-06
> **sedawk said:**
> I'm confused!

So far I have seen these setups:

1) DSL modem connected to a PC with a patch cable.
PPPoE settings are configured on the PC.

2) DSL modem and router (with or without WLAN) connected
with a patch cable.
In this case the router uses PPPoE to talk to the modem.
PPPoE settings are configured in the router.

3) all-in-one-box (modem and router and wireless)
Similar to 2, only the cable is replaced by an internal bus.


How does your setup differ from the above examples?
If you need PPPoE over wireless, my conclusion would be
you have a wireless DSL modem without embedded router?
Sounds funny!

Brotha,
Look up my wireless was working in vista and in opensuse 11.1 when i moved to ubuntu is not working the cause i don't know...
I've got a pc connected to dsl with pppoe from xp and a laptop with ubuntume.

Scientific Atlanta
A Cisco Company
Subscriber Networks
> 
Model EPC2434&#8482; Wireless Home Gateway with
Two-Line Embedded Media Terminal Adapter 
Subscriber Networks 

---

### Post by ummah on 2009-02-07
Brothers any idea what to do??

---

### Post by superprash2003 on 2009-02-07
the problem is you arent getting an ip address.. your ifconfig doesnt show any ip.. you could try setting up static ip under system->admin->network

---

### Post by ummah on 2009-02-07
but I don't have any static, I use dynamic look know I've connected with cable from router not with wifi:

ifconfig:
> ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:3a:06:11:7e  
          inet6 addr: fe80::21f:3aff:fe06:117e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10440 (10.4 KB)  TX bytes:8550 (8.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:73:d2:1e  
          inet6 addr: fe80::21b:38ff:fe73:d21e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22991876 (22.9 MB)  TX bytes:2543840 (2.5 MB)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30614649 (30.6 MB)  TX bytes:30614649 (30.6 MB)

pan0      Link encap:Ethernet  HWaddr f6:5b:3b:94:0f:e4  
          inet6 addr: fe80::f45b:3bff:fe94:fe4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.128.137.74  P-t-P:10.128.128.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:24273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:22131292 (22.1 MB)  TX bytes:1979866 (1.9 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-06-11-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60173 errors:0 dropped:0 overruns:0 frame:1372
          TX packets:788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:5290774 (5.2 MB)  TX bytes:44721 (44.7 KB)
          Interrupt:19 

How to make working with wireless know this, cause it  doesn't work:
> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:"WebSTAR"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:FC:17:8D:52   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:26911  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.


---

### Post by ummah on 2009-02-08
Any idea pls!

Also when I do with wifi-radar "Acquiring IP address" it send the msg:
Could not get the IP address!!!
I've used a DHCP, and also know i use this method.

---

### Post by ummah on 2009-02-08
Do u copy!!
any idea or i have to move to the ******* winshit

---

### Post by ummah on 2009-02-08
plss!!:(

---

### Post by superprash2003 on 2009-02-08
well your outputs have changed..what im saying is that you arent getting a local ip from your router.. so its best to setup static ip .. this should help you [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

