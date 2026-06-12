---
title: "Replacing an ethernet driver"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by taojian on 2010-10-19
I recently bought a Lenovo K23 laptop with which I am much pleased. The wireless card works off a Broadcom proprietary driver, and I eventually figured out how to install that and get wireless.

However, in the process I nuked my ethernet capabilities. When I first installed ubuntu (10.10 off a USB drive, it has no disk drive), the wireless wouldn't work, but I plugged the ethernet in and got a connection right off, no problem.

Then came the long dark struggle with the wireless, and when I came out of it, I had no ethernet, ie no "wired connection" option in the network applet at all. I actually reinstalled the entire system, wiping the hard drive and starting again, and still wired connection will not respond, which makes me think I've deleted something pretty fundamental. There is a green and yellow light on my ethernet port, and they are on all the time, no matter whether the ethernet is plugged in or not.


Here's everything:

```

uname -a

Linux pellet 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

```
```

ifconfig

eth1      Link encap:Ethernet  HWaddr 00:26:82:96:71:5a  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:fe96:715a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:298849 errors:0 dropped:0 overruns:0 frame:57236
          TX packets:214669 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:449807910 (449.8 MB)  TX bytes:18476675 (18.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


```

```

lspci -nn | grep -i net

06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

```

sudo lshw | -C network

06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:96:71:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.7 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f4500000-f4503fff

```

```

cat /etc/udev/rules.d/70-persistent-net.rules

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:ae:1d:c8:39:08", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:82:96:71:5a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:82:96:71:5a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

```

dmesg | grep eth

[   10.391818] eth0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   10.420436] udev[371]: renamed network interface eth0 to eth1
[   29.490035] eth1: no IPv6 routers present

```

I don't quite know what I'm looking at, but it kind of looks like I have no ethernet NIC at all…? The above were taken with the ethernet cable plugged in, presumably that's why ifconfig thinks eth1 has an IP address of 192.168.0.7. Does that mean I'm close?

Any and all suggestions desperately appreciated!

---

### Post by taojian on 2010-10-19
Also: no wired connections show up under Preference > Network Connections either&#8230;

---

### Post by psusi on 2010-10-19
Looks like your ethernet controller is fried.

---

### Post by taojian on 2010-10-20
That's what I was afraid of&#8230;

---

### Post by taojian on 2010-10-20
That's what I was afraid of…

---

