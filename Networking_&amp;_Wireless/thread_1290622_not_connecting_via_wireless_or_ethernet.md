---
title: "not connecting via wireless or ethernet"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by cocoapro on 2009-10-13
I just downloaded and installed ubuntu 9.04 side by side with vista on my new acer aspire 5517 laptop and everything installed correctly as far as i can tell but it wont find any wireless networks (wireless card issue?) and even more so it wont connect to the internet even when i have the ethernet cable plugged in.  I'm pretty much a newbie when it comes to this part of linux and im not sure exactly whats going on.  Any help would be greatly appreciated

---

### Post by Iowan on 2009-10-13
Easiest way to collect some information is via command line (terminal). Post results of **ifconfig -a** and **lshw -C network**.

---

### Post by cocoapro on 2009-10-13
ifconfig -a gives results:
lo   Link encap:Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:180 errors:0 dropped:0 overruns:0 frame:0
      TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:14048 (14.0 KB)  TX bytes:14048 (14.0 KB)

pan0  Link encap:Ethernet   HWaddr e2:40:2a:b4:be:90
           BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:0     TX bytes:0

and lshw -C network gives:

*-network UNCLAIMED
description: Network controller
product: AR9285 Wireless Network Adaptor (PCI-Express)
vendor: Atheros Communications Inc.
physical id:0
bus info: pci@0000:02:00.0
version:01
width:64 bits
capabilities:bus_master cap_list
configuration:latency=0
*-network UNCLAIMED
description:Ethernet controller
product:Attansic Technology Corp.
vendor:Attansic Technology Corp.
physical id: 0
bus info: pci@0000:08:00.0
version:c0
width:64 bits
clock:33MHz
capabilities:bus_master cap_list
configuration:latency=0
*-network DISABLED
description:Ethernet interface
physical id: 1
logical name: pan0
serial:e2:40:2a:b4:be:90
capabilities:ethernet physical
configuration:broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

hopefully thats helpful

---

### Post by Iowan on 2009-10-13
Hopefully, [this]("http://ubuntuforums.org/showthread.php?t=1286503") one will help with the wireless.
Dunno if something in [here]("http://ubuntuforums.org/archive/index.php/t-1244898.html") can help with the ethernet connection...

---

