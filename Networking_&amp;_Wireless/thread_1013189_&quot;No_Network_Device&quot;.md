---
title: "&quot;No Network Device&quot;"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by nolewatcher on 2008-12-16
Seems that there is a great deal of networking problems with the last two UBUNTU releases, 8.04 and 8.10. I've read the forums daily, even added my two bits from time to time. But I fail so far to find the answer that I think I need. I have a Gigabyte brand M/B with RTL8101 network on board. Both Hardy and Intrepid installs the driver RTL8139 for this adapter (as does Windows XP incidentally). When I run ifconfig -a it shows this:


eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 5a:74:4b:71:c0:d5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Notice that the eth0 adapter has no valid MAC address, and therefore it does not show up as a good network device. I have replaced Network Manager with Wicd, but it doesn't help. I changed the settings to STATIC, with netmask and gateway configured....still no help. Has anyone else run into this problem? What did you do to fix it? 
LINKSYS router hooked up to a Speedstream 4200 DSL modem.
I have no trouble configuring it with Windah.....

---

