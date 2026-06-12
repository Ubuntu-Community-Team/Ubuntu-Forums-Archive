---
title: "IBM T42 Wireless Problems, not fixed... 8.10"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by thenewcrowd on 2009-02-01
yes i have a pre-lenovo t42 running intrepid works TOTALLY AWESOME with better graphics support fresh off the install then the last 4 releases combined, the problem is 2 days ago after a shut down my wireless turned off... and i have used tpb, gedit-ing my ibm-wireless.sh file removing and re-installing my network-manager and nothing seems to physically turn my wirless back on. fn+f5... does nothing  my card is..

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2711
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel modules: ipw2200


and my ifconfig is



eth0      Link encap:Ethernet  HWaddr 00:11:25:43:1a:1a  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe43:1a1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2795544 (2.7 MB)  TX bytes:545759 (545.7 KB)

irda0     Link encap:IrLAP  HWaddr a7:db:d6:e3  
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:130609 (130.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

as far as i can tell my wireless is off, how can i turn it back on...

---

