---
title: "WiFi Help (ProNets WP81R1)"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by Drune Grey on 2012-05-02
**Machine Brand/Model**

Gateway DX4300-15e

**Network Info**
05:05.0 Network controller: Realtek Semiconductor Co., Ltd. Device [10ec:8190]

eth0

Link encap:Ethernet HWaddr 90:fb:a6:2d:cb:f8
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17

loopback is running fine

getting "no wireless extensions."

Code:
> sudo lshw -C network
Provides
*-network UNCLAIMED
description: Network Controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 5
bus info: pci@0000:05:05.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=64 maxlatency=64 mingnt=32
resources: ioport:e800(size=256) memory:febff000-febfffff

**Version Number**
Ubuntu 11.10

Code:
> $ uname -mr
Provides

3.0.0-12-generic i686

Code:
> $ sudo /etc/init.d/networking restart
Provides

* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces... [OK]

**Also of note**
I'm running Ubuntu as a Live Stick booting from my USB
Any help would be appreciated thank you.

---

### Post by Drune Grey on 2012-05-08
Don't mean to overstep just hoping a bump will help.

---

### Post by Drune Grey on 2012-05-10
Update. I thought that actually installing Ubuntu might help and so I did just that, however I'm still not able to figure out the wireless issue. It seems as if my wireless card isn't even being recognized. It is a PCI card not a usb. Any help is appreciated, thank you.

---

