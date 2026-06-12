---
title: "No connection to LAN or wireless"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2010-06-29
Using Hardy on a laptop.
Can't access the web via lan cable or wireless.
Followed the guide in the docs section, but got nowhere.
I can ping the router on the lan, but can't ping further.
iwconfig tells me that it can see my ESSID but that "Access Point: Not-Associated", whatever that means.
Is there any other connection guide available that I can access to grind my way through this?
Thanks

---

### Post by Iowan on 2010-06-29
What does **ifconfig -a** report about your interfaces? Does **sudo lshw -C network** show aliases, drivers, etc?

---

### Post by Buster95 on 2010-06-30
Thanks for the response,
My response was delayed because I had to source a flash drive to transfer the output records you requested from my non-operational machine to another machine.
At the time of copying these files, the laptop was not connected to any hard wired ethernet or wireless network. However, it was indicating three nearby protected wireless routers at near full strength.
When connected to the hard wired ethernet at home, the only thing that seems to change are the RX / TX packets which seem to "handshake" normally with the router.
When I deselect the ethernet and try the wireless, it detects my home wireless router at around half strength (by the indicator bars), but doesn't connect.
Both the ethernet (eth0)and  the wireless (wlan0) settings are on "roaming".

dexter@dexter-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:90:f5:57:ba:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:78200 (76.3 KB)  TX bytes:78200 (76.3 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:15:af:12:7d:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-12-7D-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sudo lshw -C network
sudo] password for dexter:  
  *-network                
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:90:f5:57:ba:bb 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:15:af:12:7d:b7 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

