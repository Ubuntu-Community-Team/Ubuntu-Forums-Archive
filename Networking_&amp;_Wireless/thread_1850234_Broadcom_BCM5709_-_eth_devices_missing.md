---
title: "Broadcom BCM5709 - eth devices missing"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by gtdaqua on 2011-09-26
I have an IBM x3550 M3 server with integrated Broadbcom 5709 Dual-NICs and an add-on card with the same model running 10.04.3 LTS and the latest kernel is seeing only the integrated NICs. It doesn't see the add-on card.

However, lspci | grep -i ether shows:

> 
0b:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
0b:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
1a:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet
1a:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet


The first two are working. Those are the integrated ones. The last two "were" working until now. I assume bnx2 is the driver but it isn't apparently loaded for the the last two cards. 

Can anyone help out?

Here is a lshw -C network 

```

 *-network:0             
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 20
       serial: e4:1f:13:45:04:c4
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.0.2 duplex=full firmware=5.2.2 NCSI 2.0.6 ip=192.168.5.87 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:28 memory:92000000-93ffffff
  *-network:1
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0.1
       bus info: pci@0000:0b:00.1
       logical name: eth1
       version: 20
       serial: e4:1f:13:45:04:c6
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.0.2 duplex=full firmware=5.2.2 NCSI 2.0.6 ip=0.0.0.10 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:40 memory:94000000-95ffffff
  *-network:0 [color=red]**UNCLAIMED[/color]**
       description: Ethernet controller
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:1a:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:97a00000-97a3ffff
  *-network:1 [color=red]**UNCLAIMED[/color]**
       description: Ethernet controller
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0.1
       bus info: pci@0000:1a:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:97a40000-97a7ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: e6:1f:13:49:e4:7b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=yes multicast=yes

```

And finally the last portion lspci -v
```

0b:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
	Subsystem: IBM Device 03a9
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at 92000000 (64-bit, non-prefetchable) [size=32M]
	Capabilities: <access denied>
	[color=green]**Kernel driver in use: bnx2[/color]**
	Kernel modules: bnx2

0b:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
	Subsystem: IBM Device 03a9
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at 94000000 (64-bit, non-prefetchable) [size=32M]
	Capabilities: <access denied>
	[color=green]**Kernel driver in use: bnx2[/color]**
	Kernel modules: bnx2

1a:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet
	Subsystem: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet
	Flags: fast devsel, IRQ 30
	Memory at 97a00000 (64-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: bnx2

1a:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet
	Subsystem: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet
	Flags: fast devsel, IRQ 37
	Memory at 97a40000 (64-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: bnx2

```

---

### Post by gtdaqua on 2011-09-29
Update:

Found out that the NIC was actually faulty! The same NIC didn't work on windows too with latest drivers - kept showing the Yellow Exclamation in Device Manager.

Must call Dell support to replace this Broadcom NIC.

---

### Post by bababooey on 2011-10-21
btw my buddy told me that one of the eth0 ports has a huge problem, I forget exactly what it was. I jjust use eth0/port 1 and the IMM port. The rest are unused. I havent had time to find out more detials regarding this ethernet port issue, and their website is noit very helpful. Did you hear about this?

---

### Post by FiVAL on 2011-11-28
Hmmm... I'have the same issue but I don't think it's hardware related in my situation. When I do an "rmmod bnx2" and then a "modprobe bnx2" everything (eth0 AND eth1) works perfect!

Is it also in you case? Or is it really the hardware?

---

### Post by icrush on 2012-02-19
hi 

I had the same issue. HP DL360 G5 Ubuntu 11.10. after the setup eth0 wasnt "unclaimed"

the onetime command "rmmod bnx2 && modprobe bnx2"  works for me - thank you!

---

