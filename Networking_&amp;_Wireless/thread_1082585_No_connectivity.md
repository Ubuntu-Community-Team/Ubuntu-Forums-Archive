---
title: "No connectivity"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by landshrk on 2009-02-27
My GF has a Dell Inspiron E1505. It had a sh*tload of trojans and spyware and whatnot. Backed up the important things, wiped, defragged, and installed Intrepid on it.

Install went fine (off my USB flash drive), but when I went to run a hardline ethernet (for the updates, as the wireless NEVER works right off the bat for me on these damn machines), I got nothing.

No wireless. No ethernet. Nothing I can do to update and finish this pain once and for all.

Any ideas? Google's been useless (as it can be when you're a bit of a n00b at this). I really just want to see if there's any way I can copy a file onto her machine so that it will actually do its job and recognize the wireless card it has.

Any ideas are very welcome and greatly appreciated.

Thanks.

---

### Post by Crafty Kisses on 2009-02-28
If there's anyway you can get the results to these commands and post them here on the forum, that'd be great:
```
lspci
lsusb
sudo lshw -C network
```

---

### Post by landshrk on 2009-02-28
> **Codename said:**
> If there's anyway you can get the results to these commands and post them here on the forum, that'd be great:
```
lspci
lsusb
sudo lshw -C network
```

Okay, here:

```
 lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


etc...

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

...

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I left out (most) of the things which seemed unnecessary, only including the ones pertaining to network workingness.

```
 lsusb:

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Entire printout there.

```
 sudo lshw -C network:

*-network
     description: Network controller
     product: BCM4311 802.11b/g WLAN
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:0b:00.0
     version: 01
     width: 32 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: driver=b43-pci-bridge latency=0 module=ssb
*-network
     description: Ethernet interface
     product: BCM4401-B0 100Base-TX
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:03:00.0
     logical name: eth0
     version: 02
     serial: 00:15:c5:c2:e0:39
     size: 10MB/s
     capacity: 100MB/s
     width: 32 bits
     clock: 33MHz
     capabilities: pm bus_master cap_list ethernet physical mii 10bt-fd 100bt 100bt-fd autonegotiation
     configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twister pair speed=10MB/s
*-network:0 DISABLED
     description: Wireless interface
     physical id: 1
     logical name: wlan0
     serial: 00:18:f3:e2:9c:47
     capabilities: ethernet physical wireless
     configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
     description: Ethernet service
     physical id: 2
     logical name: pan0
     serial: d6:d8:0b:33:e7:94
     capabilities: ethernet physical
     configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

And that's the entire printout for lshw -C network.

Thanks man.

---

### Post by Crafty Kisses on 2009-02-28
Hey there my friend! This is the wireless card you have:
```
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```
I think if you follow the instructions in [this]("http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy") thread, you can get everything up and running. If those instructions don't help let me know, and I can further assist you.

---

