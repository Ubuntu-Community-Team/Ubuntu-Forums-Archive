---
title: "Slow network throughput"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by heiNey on 2010-12-05
Hi,

I was wondering if someone could help me with this.

I recently purchased a D-Link DNS-321 and have been trying to transfer files to it.  Ubuntu is showing that I am getting ~4.5MB/s MAX.  

This NAS has a 10/100/1000 interface.  I have a router and switch that are also 10/100/1000 (all D-Link).  My motherboard is a Gigabyte GA-965P-DS3 with a 10/100/1000 NIC onboard.

I enabled Jumbo Frames on the switch and set the MTU to 9000.  I also went into network tools and set the MTU on this computer to 9000.  The computer and the DNS-321 are all wired through the router and switch using cat5e cables.

Is there anything else I can do to increase the throughput?  I read on other forums that people get ~15MB/s, so I am not sure if it is an Ubuntu issue.

```


eth0      Link encap:Ethernet  HWaddr 00:1a:4d:62:9e:e6  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe62:9ee6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:66092298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49706942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:389195539 (389.1 MB)  TX bytes:3618016714 (3.6 GB)
          Interrupt:16 

```

---

