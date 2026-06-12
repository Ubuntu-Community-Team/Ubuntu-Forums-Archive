---
title: "Both network connections down laptop"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by soapwater on 2009-03-22
Since yesterday I don't have any network connection on my laptop.
It has a wireless and a wired network card. After a power failure in the building, I tried to connect to a different network, since than I lost my wireless. Today I noticed that also the wired network doesn't work anymore.

Could anyone help me reconfiguring it because I don't know what I'm doing anymore. (newbee Ubuntu user :))

lspci -v | less gives me

```
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Et
hernet (rev 90)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 2419
        Flags: bus master, medium devsel, latency 173, IRQ 5
        I/O ports at 2000 [size=256]
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 38020000 [disabled] [size=128K]
        Capabilities: <access denied>

00:06.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 
01)
        Subsystem: Creatix Polymedia GmbH Unknown device 2001
        Flags: medium devsel, IRQ 10
        Memory at d0006000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>
```

lshw -C network gives me:

```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:40:ca:c6:d8:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wifi0
       version: 01
       serial: 00:07:ca:01:c0:26
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.6.3 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
```

---

