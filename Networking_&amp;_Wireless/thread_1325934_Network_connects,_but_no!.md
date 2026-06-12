---
title: "Network connects, but no!"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by marcwhitaker on 2009-11-13
Brand new Aspire 751h, I wiped XP and installed 9.04. (I tried 9.10, but wireless didn't work at all.)

Anyway, WIFI worked great, WPA-2 at work, so I updated everything after the install. Since then, I can'tget the wireless to work. The network manager says there are networks, it asks for passphrases, it says it's connected, the router says I'm connected with an IP address, but Firefox and update cannot connect.

Here's some stuff to look ate:
```

susana@poppy:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:f1:28:ca
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:15:10:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.2.196 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:5c:12:52:e9:93
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
susana@poppy:~$ 

```

I'm not completely daft, I've installed Ubuntu on two notebooks and two desktops over the last couple of years.

Anyone have any advise to offer?

---

### Post by marcwhitaker on 2009-11-14
More info: I can pull up the router config page by typing in the IP, so it seems the problem is with DNS, but only on wireless, and only on this new machine.

  * I have a wireless connection to this new notebook. The Router confirms this, but I can't connect to anything but my router.
  * I can ping Google.
  * Everything works when I use the ethernet connection.
  * Everything works on another wireless notebook sitting beside the new one.

I'm at a loss. HELP!

---

