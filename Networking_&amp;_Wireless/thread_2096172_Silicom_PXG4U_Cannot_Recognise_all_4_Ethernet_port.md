---
title: "Silicom PXG4U Cannot Recognise all 4 Ethernet ports"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by CyberAngel on 2012-12-19
I just bought [Silicom PXG4U Quad Port Gigabit Ethernet]("http://www.silicom-usa.com/Networking_Adapters/PXG4U-Quad_Port_Copper_Gigabit_Ethernet_PCI-X_Server_Adapter_Broadcom_based_50") and installed it in a simple PCI slot (The is no PCI-X slot on the motherboard). The system is running Ubuntu Natty 11.04 64bit server and it will only recognize 2/4 ethernet ports.

Anyone know how to possibly solve the problem?

This is the dmesg output of the system boot when load the module:

```
[    2.810786] tg3 0000:04:04.0: phy probe failed, err -19
[    2.813608] tg3 0000:04:04.0: Problem fetching invariants of chip, aborting
[    2.813632] tg3 0000:04:04.0: PCI INT A disabled
[    2.813655] tg3 0000:04:04.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.932450] tg3 0000:04:04.1: phy probe failed, err -19
[    2.935374] tg3 0000:04:04.1: Problem fetching invariants of chip, aborting
[    2.935398] tg3 0000:04:04.1: PCI INT B disabled
[    2.935418] tg3 0000:04:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.101027] tg3 0000:04:06.0: eth1: Tigon3 [partno(BCM95704A6) rev 2100] (PCIX:133MHz:64-bit) MAC address 00:e0:ed:04:bd:6e
[    3.101031] tg3 0000:04:06.0: eth1: attached PHY is 5704 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.101034] tg3 0000:04:06.0: eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.101037] tg3 0000:04:06.0: eth1: dma_rwctrl[769f4000] dma_mask[64-bit]
[    3.101061] tg3 0000:04:06.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.243735] tg3 0000:04:06.1: eth2: Tigon3 [partno(BCM95704A6) rev 2100] (PCIX:133MHz:64-bit) MAC address 00:e0:ed:04:bd:6f
[    3.243739] tg3 0000:04:06.1: eth2: attached PHY is 5704 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.243742] tg3 0000:04:06.1: eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.243745] tg3 0000:04:06.1: eth2: dma_rwctrl[769f4000] dma_mask[64-bit]
```

and this is the lspci -vv output:

```
04:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
        Subsystem: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] PCI-X non-bridge device
                Command: DPERE- ERO+ RBC=512 OST=1
                Status: Dev=04:04.0 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
pcilib: sysfs_read_vpd: read failed: Connection timed out
                Not readable
        Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: a547a199970e8370  Data: 14d7
        Kernel modules: tg3

04:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
        Subsystem: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin B routed to IRQ 19
        Region 0: Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] PCI-X non-bridge device
                Command: DPERE- ERO+ RBC=512 OST=1
                Status: Dev=04:04.1 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
pcilib: sysfs_read_vpd: read failed: Connection timed out
                Not readable
        Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: 30c48aea3ff5e3d0  Data: 1093
        Kernel modules: tg3

04:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
        Subsystem: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (16000ns min), Cache Line Size: 4 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at dfdd0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] PCI-X non-bridge device
                Command: DPERE- ERO+ RBC=512 OST=1
                Status: Dev=04:06.0 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: Broadcom NetXtreme Gigabit Ethernet Controller
                Read-only fields:
                        [PN] Part number: BCM95704A6
                        [EC] Engineering changes: 106679-15
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 34 65 34
                        [RV] Reserved: checksum bad, 26 byte(s) reserved
                Read/write fields:
                        [YA] Asset tag: XYZ01234567
                        [RW] Read-write area: 107 byte(s) free
                End
        Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: f9d56e4ebef4a5d4  Data: d7c7
        Kernel driver in use: tg3
        Kernel modules: tg3

04:06.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
        Subsystem: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (16000ns min), Cache Line Size: 4 bytes
        Interrupt: pin B routed to IRQ 16
        Region 0: Memory at dfdc0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [40] PCI-X non-bridge device
                Command: DPERE- ERO- RBC=2048 OST=1
                Status: Dev=04:06.1 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: Broadcom NetXtreme Gigabit Ethernet Controller
                Read-only fields:
                        [PN] Part number: BCM95704A6
                        [EC] Engineering changes: 106679-15
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 34 65 34
                        [RV] Reserved: checksum bad, 26 byte(s) reserved
                Read/write fields:
                        [YA] Asset tag: XYZ01234567
                        [RW] Read-write area: 107 byte(s) free
                End
        Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: fa7fb52dac9a6bfc  Data: a20a
        Kernel driver in use: tg3
        Kernel modules: tg3
```

---

### Post by CyberAngel on 2013-01-02
The card was defective! Changed and now everything works.

---

