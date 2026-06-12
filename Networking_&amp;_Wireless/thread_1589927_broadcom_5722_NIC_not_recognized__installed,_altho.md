---
title: "broadcom 5722 NIC not recognized / installed, although driver present"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by brbr on 2010-10-07
Hello, I just installed Ubuntu Server 10.04 LTS, running kernel 2.6.32-24-server, on a brand new Dell T110 server, supposedly fully compatible with Ubuntu Server.

I have two NICs: one ONBOARD, the other additional on PCI.
both of them are Broadcom netXtreme 5572.

on the first boot of the system, I could see both cards as eth0 and eth1 (with ifconfig)
I configured eth0 as static IP (as planned), and did not configure eth1.

after rebooting, one of the two NICs "disappeared": it does not appear in ifconfig at all.

the one that disappeared is the ONBOARD one. I investigated a bit and found the following things:

the card is SEEN, but not "installed", it appears as "UNCLAIMED" in lshw:

  ```
*-network UNCLAIMED
       description: Ethernet controller
       product: NetXtreme BCM5722 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:df9f0000-df9fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5722 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:10:18:60:23:64
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5722-v3.09 ip=10.129.167.25 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:35 memory:dfaf0000-dfafffff
```
so I checked my dmesg and found a few strange lines, showing, there actually is a problem bringing up this card:

```
[    3.737506] tg3: Could not obtain valid ethernet address, aborting.
[    3.737527] tg3 0000:04:00.0: PCI INT A disabled
[    3.737535] tg3: probe of 0000:04:00.0 failed with error -22
[    3.737553]   alloc irq_desc for 17 on node -1
[    3.737555]   alloc kstat_irqs on node -1
[    3.737560] tg3 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.737566] tg3 0000:05:00.0: setting latency timer to 64
[    3.793529] eth0: Tigon3 [partno(BCM95722A2202G) rev a200] (PCI Express) MAC address 00:10:18:60:23:64
[    3.793532] eth0: attached PHY is 5722/5756 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.793534] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.793536] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
```
that actually shows that one NIC is recognized, the other is not.

I researched a bit more, with lspci -v:

```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
        Subsystem: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
        Flags: fast devsel, IRQ 16
        Memory at df9f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data <?>
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-00-00-fe-ff-00-00-00
        Kernel modules: tg3

05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
        Subsystem: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
        Flags: bus master, fast devsel, latency 0, IRQ 35
        Memory at dfaf0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data <?>
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 64-23-60-fe-ff-18-10-00
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: tg3
        Kernel modules: tg3

```here I could see that the MAC address is 00-00-00-FE-FF-00-00-00, which, according to some forum posts on several websites, could be an issue.

I've researched everything I could on the net, and found out several people having slightly comparable issues, but they usually involve different HW, and do not provide a proper explanation / solution... I would appreciate if anyone around here has some info to share !

thanks

---

### Post by P4man on 2010-10-07
Can you remove the PCI card and see if the onboard works then?
Ive had issues in the past with 2 identical PCI tv tuner cards and 2 identical PCI USB controllers. Only one would work if both where inserted, but either would work fine alone. (also in windows btw, so probably a bios issue in my case).

---

### Post by brbr on 2010-10-08
I actually removed the PCI card, and the onboard card was suddenly recognized.
at that moment, the MAC address was not null !
I configured the interface the way I wanted, and it worked.
I stopped, then plugged back the PCI card and rebooted.
both NICs were then recognized !

problem solved, although I have not much clue why !

thanks for the tip about removing the card !

---

