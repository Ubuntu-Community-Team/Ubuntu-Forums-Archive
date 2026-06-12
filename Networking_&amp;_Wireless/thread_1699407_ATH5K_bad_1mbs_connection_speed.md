---
title: "ATH5K bad 1mb/s connection speed"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by atomicben on 2011-03-03
I've just erased my drive and installed 10.10 hoping to get this card (DWL-G510) working. I didn't have any luck in Lucid.

Now I'm running2.6.35-27-generic-pae and the card is detected and seems to find networks (although it seems the signal strengths seem a bit low considering how close I am to the AP).

The problem is that when I first connect to my AP it will say I'm connected with either 54 mb/s or 48 mb/s but very quickly this number drops to 1mb/s (see screenshot)

I've run all that standard commands to help you help me. They are pasted here:

$ dmesg | grep ath5k
> 
```

[ 12.513400] ath5k 0000:03:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 12.513519] ath5k 0000:03:02.0: registered as 'phy0'
[ 13.823306] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)

```$ ifconfig
> 
```

eth0 Link encap:Ethernet HWaddr 00:25:22:18:87:24
inet addr:192.168.0.103 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::225:22ff:fe18:8724/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:604198 errors:0 dropped:0 overruns:0 frame:0
TX packets:886569 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:216381197 (216.3 MB) TX bytes:1110490380 (1.1 GB)
Interrupt:42

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:342 errors:0 dropped:0 overruns:0 frame:0
TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:45019 (45.0 KB) TX bytes:45019 (45.0 KB)

wlan1 Link encap:Ethernet HWaddr 00:11:95:ca:91:65
inet addr:192.168.0.110 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::211:95ff:feca:9165/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:776 errors:0 dropped:0 overruns:0 frame:0
TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:238088 (238.0 KB) TX bytes:13771 (13.7 KB)

```$ iwconfig
> 
```

lo no wireless extensions.

eth0 no wireless extensions.

wlan1 IEEE 802.11bg ESSID:"ATOMIC"
Mode:Managed Frequency:2.437 GHz Access Point: 00:23:69:30:ED:29
Bit Rate=1 Mb/s Tx-Power=27 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=63/70 Signal level=-47 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

vboxnet0 no wireless extensions.

```$ lshw -C network
> 
```

WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: 02
serial: 00:25:22:18:87:24
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.103 latency=0 multicast=yes
resources: irq:42 ioport:e800(size=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:feae0000-feafffff
*-network
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: 2
bus info: pci@0000:03:02.0
logical name: wlan1
version: 01
serial: 00:11:95:ca:91:65
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k driverversion=2.6.35-27-generic-pae firmware=N/A ip=192.168.0.110 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
resources: irq:23 memory:febf0000-febfffff
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes

```$ lsmod | grep ath
> 
```

ath5k 130403 0
mac80211 231959 1 ath5k
ath 8153 1 ath5k
cfg80211 144694 3 ath5k,mac80211,ath
led_class 2633 1 ath5k

```
$ lspci -vnn (edited to save space)
> 
```

03:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
Subsystem: D-Link System Inc AirPlus G DWL-G510 Wireless PCI Adapter(rev.B) [1186:3a16]
Flags: bus master, medium devsel, latency 168, IRQ 23
Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ath5k
Kernel modules: ath5k

```

---

### Post by atomicben on 2011-03-03
Well, this is pretty embarrassing but I must be honest...

When I was looking at the connection speed I wasn't actually using that connection because I was using my eth0 wired connection.  When I tuned that off the wlan1 kicked in and started going around 48-52kb/s.  

I had NO idea that this was the *actual* speed of the connection.  Back when I used this card with windows it would stay constant which always indicated to me that whatever it read was the supported speed between me and my router.  I'd only ever see it drop if I had a bad connection or some other problem.

Sorry for the false alarm and thanks to anyone who took the time to read this thread.

---

