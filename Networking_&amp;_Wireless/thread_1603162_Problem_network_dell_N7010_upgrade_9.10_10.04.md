---
title: "Problem network dell N7010 upgrade 9.10 10.04"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by mdragus on 2010-10-22
I installed ubuntu 9.10 and my network wasn't working, so I looked it up and I've seen that the drivers weren't correctly installed so I just installed them. The wired connection worked after that. 
I've let my software update center upgrade to ubuntu 10.04 and now neither the wired nor the wireless connections work. I tried reinstalling the driver and that worked but still no internet connection. This is the output for my ifconfig eth0 command: 

eth0      Link encap:Ethernet  HWaddr b8:ac:6f:71:f8:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4294961590 errors:4294933060 dropped:4294955884 overruns:4294961590 frame:4294938766
          TX packets:4294961590 errors:4294944472 dropped:0 overruns:4294961590 carrier:4294955885
          collisions:4294938766 txqueuelen:1000 
          RX bytes:4294961590 (4.2 GB)  TX bytes:4294961590 (4.2 GB)
          Interrupt:33 


also this is the output for the sudo lshw -c network command:



  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:71:f8:71
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.1.6 firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 memory:f0400000-f043ffff ioport:2000(size=128)

Thank you very much.

P.S. if I try to do ifup eth0 it tells me that eth0 is an unknown device. So I went to the /etc/network/interfaces file and manually edited it so eth0 is a automatic dhcp and now ifup eth0 does something but it still doesn't connect to the network.

P.P.S. I also don't have wireless.

---

### Post by P4man on 2010-10-22
IF this is a dual boot machine, make sure windows is shut down, and not hibernated and see if that helps.

---

### Post by mdragus on 2010-10-22
Unfortunately that wasn't the problem. I always shut down windows before starting ubuntu.

---

### Post by P4man on 2010-10-22
I just googled on your ethernet card, and found this:

[http://ubuntuforums.org/showpost.php?p=9446984&postcount=6](http://ubuntuforums.org/showpost.php?p=9446984&postcount=6)

However, since neither your wireless nor ethernet network work at the moment (I assume?) that might get tricky. YOu probably dont have build-essential installed, and you will need it apparently.

Where did you get the drivers that you installed in 9.10 ? Was a it a .deb package? It doesnt seem to work with 10.10 that is clear.

---

