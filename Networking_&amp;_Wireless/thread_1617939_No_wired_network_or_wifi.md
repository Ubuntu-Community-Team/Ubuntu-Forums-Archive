---
title: "No wired network or wifi"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by Redcap557 on 2010-11-10
Hello.  I am very new to Linux.

I just installed Ubuntu 10.10 tonight on my Acer Aspire One D250 and have no internet at all.  I know both the wireless and wired internet work, as I am dual booting WinXP as well.  I don't know what to do, as I am very tired of XP, but I am also at a loss as to how to fix this problem.

Any help would be greatly appreciated.

---

### Post by uncaspi on 2010-11-10
Do you see the cards when you click the network icon upper right panel?
Please post the content of sudo /sbin/lshw -C network

---

### Post by Redcap557 on 2010-11-10
It detects that I have both a wired and wireless interface, but it will access neither of them.

```

redcap@Redcap-AAO:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:7a:c9:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:6c:92:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=half firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)


```

---

### Post by uncaspi on 2010-11-10
Ok it load both drivers. I would first of all search the threads for this cards to see if there is any problems related to the drivers.

---

