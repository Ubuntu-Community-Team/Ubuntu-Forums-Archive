---
title: "my wireless card is not detected"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by herbert tamayo on 2010-11-03
Hi, after install the b43 driver in ubuntu, my wireless card is down, here it is some important data:

sudo lspci -vvnn | grep 14e4
```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

sudo lshw -C network
```

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:39:4f:33
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:a000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:24:2c:74:37:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.34-020634-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

sudo lsmod | grep b43
```

b43                   194727  0 
mac80211              262371  1 b43
cfg80211              172363  2 b43,mac80211
led_class               3455  2 b43,hp_accel
ssb                    46615  1 b43

```

uname -r
```

2.6.34-020634-generic

```

sudo cat /var/log/jockey.log | tail
```

2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003054bc02sc00i00')
2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'pci:v00001002d0000438Csv0000103Csd00003054bc01sc01i80')
2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-11-03 13:18:28,138 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003054bc0Csc05i00')
2010-11-03 13:18:28,139 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17de5a8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-11-03 13:18:28,663 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled
2010-11-03 13:18:29,322 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled

```

sudo cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Also, in the "hardware drivers" applet, the b43 driver is up and running.

But my wireless card is not detected, wicd can't see the wireless, just the wired card, so my questions are:

1. what else should I check?
2. what steps should I use to bring up my wireless card since the b43 driver looks ok?
3. anything else?

regards

---

### Post by herbert tamayo on 2010-11-03
[UPDATED]
After typed: iwconfig, I found my wireless card as WLAN1, so I typed:
```

sudo iwconfig wlan1 up

```

And I've got this error:
```

SIOCSIFFLAGS: unknown error 132

```

So, I searched about it and I found this:
```

rfkill list

```

And I found that some process were blocking my card, using soft/hardware

To fix this i did:
```

sudo rfkill unblock all
sudo ifconfig wlan1 up

```

[B][I][COLOR="Red"]And that's it, my wifi card is up and running.
[/COLOR][/I][/B]

I found in wicd manager that i have to edit the info of my wireless card, previously to b43 i was using the STA driver, and my wireless card was eth2, I put that name in wicd, now I changed to wlan1 and I can see the access point.

At this point, everything is cool, i don't have any access point near at this moment but I will later, i will let you know if I have some problem later

---

