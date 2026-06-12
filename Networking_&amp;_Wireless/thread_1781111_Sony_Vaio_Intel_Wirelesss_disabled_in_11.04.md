---
title: "Sony Vaio Intel Wirelesss disabled in 11.04"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by major.tal on 2011-06-13
Hey all,

Wireless which was working perfectly in Ubuntu 10 is now disabled in 11.04. Dual boot to Vista verified the hardware is ok.

Reading related posts I applied the following:

**sudo lshw -C network**

> 
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


**rfkill list all**

> 
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no


**sudo lshw -C network**

> 
*-network 
description: Ethernet interface
product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth2
version: 82
serial: 90:1d:92:d9:d4:14
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full ip=10.0.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:17 ioport:3000(size=256) memory:f8000000-f80000ff
*-network DISABLED
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 61
serial: 00:1d:e0:b4:30:b1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
resources: irq:45 memory:fa000000-fa001fff
tal@tal-VGN-FZ430E:~$ sudo lshw -C network
*-network 
description: Ethernet interface
product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth2
version: 82
serial: 90:1d:92:d9:d4:14
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full ip=10.0.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:17 ioport:3000(size=256) memory:f8000000-f80000ff
*-network DISABLED
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 61
serial: 00:1d:e0:b4:30:b1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
resources: irq:45 memory:fa000000-fa001fff


The hardware switch does not seem to function (not even the attached LED).

Wired Ethernet works well.

**dmesg|grep wla**

> 
[   24.746249] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   24.746253] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   24.749541] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.749553] iwlagn 0000:06:00.0: setting latency timer to 64
[   24.757843] iwlagn 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   24.796767] iwlagn 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   24.796770] iwlagn 0000:06:00.0: Device SKU: 0Xb
[   24.797556] iwlagn 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   24.797708] iwlagn 0000:06:00.0: irq 45 for MSI/MSI-X
[   24.942597] iwlagn 0000:06:00.0: loaded firmware version 228.61.2.24
[27088.983078] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[38217.132202] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[39337.735401] iwlagn 0000:06:00.0: RF_KILL bit toggled to disable radio.
[39337.752525] iwlagn 0000:06:00.0: Not sending command - RF KILL
[39337.752535] iwlagn 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[39337.752542] iwlagn 0000:06:00.0: Error setting new RXON (-5)
[39337.756496] iwlagn 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[39337.756496] iwlagn 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[39337.756496] iwlagn 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[39337.756496] iwlagn 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[39344.871474] iwlagn 0000:06:00.0: RF_KILL bit toggled to enable radio.
[39355.724154] ADDRCONF(NETDEV_UP): wlan0: link is not ready


After posting to the Hardware & Laptops forum, they suggested applying

> 
sudo ifconfig wlan0 up


The wireless LED lit up, and **ifconfig** shows the wireless interface:

> 
eth2      Link encap:Ethernet  HWaddr 90:1d:92:d9:d4:14  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::921d:92ff:fed9:d414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:457142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:418192667 (418.1 MB)  TX bytes:49477210 (49.4 MB)
          Interrupt:17 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23945556 (23.9 MB)  TX bytes:23945556 (23.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:b4:30:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



But nothing at the IP level.
Also, after a few minutes in which my laptop went to screensaver and locked up the wireless was disabled again.

Please help! My laptop is meaningless without the wireless...

---

### Post by major.tal on 2011-06-16
Someone?
Please?

---

### Post by lesser on 2011-06-16
It looks you have a working interface. Don't know why it locks, check ```
dmesg
``` for hints.

When the wireless light is lit, can you try
```
iwlist wlan0 scan
```This should give you a list of access points around. Not all cards support this command, if you get an error, try 
```
iwlist wlan0 ap
``` instead.
If you get a list, you can try
```
sudo iwconfig wlan0 mode managed essid "<your_AP_here>"
```which tells your card to connect to <your_AP_here> and get set up by DHCP from that AP.

---

### Post by major.tal on 2011-06-16
Thanks for your reply!

When I try **dmesg**:

```
[294433.330331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

When I issue **iwlist wlan0 scan**:
```
wlan0     No scan results
```

and when I issue **iwlist wlan0 ap**:
```
wlan0     Interface doesn't have a list of Peers/Access-Points
```

Any ideas?

---

