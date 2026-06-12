---
title: "BCM4321 Inop following upgrade to 10.10"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by CarbineReloaded on 2010-10-16
Was running Ubuntu 10.4 until last night when I was prompted to upgrade to 10.10.

Following the upgrade, my BCM4321 wifi card will not work.  My wire'd connection and tethering my android mobile phone will allow online access.  

Below is my wifi card..... I have gone to Admin > Additional Drivers and disabled/re-enabled the drivers without luck.  When I click the little wireless icon where I would normally select my wireless network, it says "no network devices available."


eth1      Link encap:Ethernet  HWaddr 00:1a:73:f2:71:ce  
          inet6 addr: fe80::21a:73ff:fef2:71ce/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:32 dropped:0 overruns:0 frame:5136
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 



I would like to avoid having to do a clean install of 10.10 on this laptop as I have a ton of information saved on it and don't have the time to dedicate setting everything back up.

Edit to add:

** sudo lshw -C network** 
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:12:a5:49
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.107 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
       resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=8)
  *-network
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:f2:71:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by ArgusVision on 2010-10-16
I installed 10.10 on a friend's Acer 4520 last Wednesday. I believe it has the same broadcom card and is having similar connectivity issues. It worked for a few hours, then strangely enough stopped. I think it may have to do with the interface being assigned as eth1 and not being seen as a wireless interface. When she went to System > Administration > Network Tools and Selected the eth1 interface it was listed as an ethernet interface (hardwire) instead of wireless. There's a post from back in 2007 that seems like it maybe interesting. 
        [http://ubuntuforums.org/archive/index.php/t-338332.html](http://ubuntuforums.org/archive/index.php/t-338332.html)
The intermittent name change experienced by this user could be similar to what we're experiencing. (Although that's purely conjecture at this point.)
I won't be able to get my hands on her PC again until tomorrow at the earliest. But could you post your /etc/network/interfaces file contents?
Thank's

---

### Post by TBABill on 2010-10-16
My BCM4312 would see networks and never connect in 10.10. No fixes anywhere that worked so I reverted. Hope you get it going soon and can post the fix for others. This problem seems spread across many different brands and models.

---

