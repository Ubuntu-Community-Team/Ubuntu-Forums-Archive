---
title: "Can't get DGE-528T ethernet card to work on Karmic amd64"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by denarced on 2010-06-11
The title pretty much says it all.
By upgrading to latest kernel(2.6.31-22) the card was recognized but it still doesn't quite work. I'm not that good at this but I'll paste some stuff that I think is related to solving a problem such as this.
lspci -vv
```

05:06.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
	Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 8000 [size=256]
	Region 1: Memory at d3006000 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 40080000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: r8169
	Kernel modules: r8169


```
lshw
```

  *-network DISABLED
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: eth2
       version: 10
       serial: 00:26:5a:bf:8b:fe
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:16 ioport:8000(size=256) memory:d3006000-d30060ff memory:40080000-4009ffff(prefetchable)

```
dmesg
```

[    3.504542] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.504802] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    3.504807]   alloc irq_desc for 16 on node 0
[    3.504810]   alloc kstat_irqs on node 0
[    3.504819] r8169 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    3.504843] r8169 0000:05:06.0: no PCI Express capability

```

---

### Post by denarced on 2010-06-11
Hah, answer was simple.
Put the cable in the right slot :D

---

