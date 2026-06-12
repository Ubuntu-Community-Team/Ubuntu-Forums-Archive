---
title: "NM &amp; Hidden Wireless Networks"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by Mintsoft on 2009-03-15
Hi all,

I'm having some trouble getting network manager to connect to my hidden wireless connection, if I put broadcast SSID on (on the router) then it works, connects no problem. I switch broadcast SSID off, click NM, connect to hidden wireless network, put in the SSID & WPA2 key. It sits and thinks for a bit then finally pops up with the "Network Manager requires a network key" dialog, even though it's definately the right one!

I'm reasonably sure this worked ok in 8.04, although I seem to remeber it didn't 'save' the settings.Mind you I was using ndiswrapper for the wireless, I switched to the native when it came out in this version I think.

Incase this helps anyone:
```

rob@Vostro:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 03
       serial: 00:1f:e2:8b:d8:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=10.0.0.44 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:53:17:7f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:8d:39:99:30:53
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

