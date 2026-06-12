---
title: "Wired network connection problem"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by biyan on 2011-08-13
Hi,
 
I have problem in connecting to wired network. Actually my wired network worked fine a few days ago. But now the connection does not work.
 
```

biyan@biyan-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:d3:30:6d:86 
inet addr:10.2.250.250 Bcast:10.2.255.255 Mask:255.255.0.0
inet6 addr: fe80::216:d3ff:fe30:6d86/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:189 errors:0 dropped:0 overruns:0 frame:0
TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:45583 (45.5 KB) TX bytes:15422 (15.4 KB)
Interrupt:16 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:104 errors:0 dropped:0 overruns:0 frame:0
TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:7343 (7.3 KB) TX bytes:7343 (7.3 KB)

``````

biyan@biyan-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for biyan: 
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.
[ OK ]

``````

biyan@biyan-laptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

``````

biyan@biyan-laptop:~$ dmesg | grep eth0
[ 2.049176] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:16:d3:30:6d:86
[ 2.049182] tg3 0000:02:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[ 2.049185] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[ 2.049189] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[ 22.421346] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 23.997833] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 23.997837] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX
[ 23.998061] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 34.756024] eth0: no IPv6 routers present
[ 171.025390] tg3 0000:02:00.0: eth0: Link is down
[ 1996.198623] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 1996.198631] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX

``````

biyan@biyan-laptop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
Subsystem: Lenovo Device 3be7
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
Latency: 0
Capabilities: <access denied>
Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 00002000-00002fff
Memory behind bridge: d8000000-d80fffff
Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
Subsystem: Lenovo Device 3bec
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 45
Region 0: Memory at d8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
I/O behind bridge: 00003000-00003fff
Memory behind bridge: d4000000-d5ffffff
Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
I/O behind bridge: 00004000-00004fff
Memory behind bridge: d6000000-d7ffffff
Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
Subsystem: Lenovo Device 3bec
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 23
Region 4: I/O ports at 1800 [size=32]
Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
Subsystem: Lenovo Device 3bed
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin B routed to IRQ 19
Region 4: I/O ports at 1820 [size=32]
Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
Subsystem: Lenovo Device 3bee
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin C routed to IRQ 18
Region 4: I/O ports at 1840 [size=32]
Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
Subsystem: Lenovo Device 3bef
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin D routed to IRQ 16
Region 4: I/O ports at 1860 [size=32]
Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
Subsystem: Lenovo Device 3bf0
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 23
Region 0: Memory at d8404000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
I/O behind bridge: 00005000-00005fff
Memory behind bridge: d8100000-d81fffff
Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
Subsystem: Lenovo Device 3bf2
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Capabilities: <access denied>
Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
Subsystem: Lenovo Device 3bf4
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin B routed to IRQ 19
Region 0: I/O ports at 01f0 [size=8]
Region 1: I/O ports at 03f4 [size=1]
Region 2: I/O ports at 0170 [size=8]
Region 3: I/O ports at 0374 [size=1]
Region 4: I/O ports at 18b0 [size=16]
Capabilities: <access denied>
Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
Subsystem: Lenovo Device 3bf5
Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Interrupt: pin B routed to IRQ 10
Region 4: I/O ports at 18e0 [size=32]
Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300] (prog-if 00 [VGA controller])
Subsystem: Lenovo Device 3bf6
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 43
Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
Region 1: I/O ports at 2000 [size=256]
Region 2: Memory at d8000000 (32-bit, non-prefetchable) [size=64K]
[virtual] Expansion ROM at d8020000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: radeon
Kernel modules: radeon
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Subsystem: Lenovo Device 3bf9
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 46
Region 0: Memory at d4000000 (64-bit, non-prefetchable) [size=64K]
Expansion ROM at <ignored> [disabled]
Capabilities: <access denied>
Kernel driver in use: tg3
Kernel modules: tg3
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Subsystem: Intel Corporation Device 1002
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 44
Region 0: Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: iwl3945
Kernel modules: iwl3945
0a:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
Subsystem: Lenovo Device 3be6
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 168, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 22
Region 0: Memory at d8106000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
Memory window 0: 80000000-83fff000 (prefetchable)
Memory window 1: 84000000-87fff000
I/O window 0: 00005000-000050ff
I/O window 1: 00005400-000054ff
BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
0a:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
Subsystem: Lenovo Device 3be6
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 22
Region 0: Memory at d8105000 (32-bit, non-prefetchable) [size=2K]
Region 1: Memory at d8100000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: firewire_ohci
Kernel modules: firewire-ohci, ohci1394
0a:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
Subsystem: Lenovo Device 3be6
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 22
Region 0: Memory at d8104000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: tifm_7xx1
Kernel modules: tifm_7xx1
0a:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
Subsystem: Lenovo Device 3be6
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 22
Region 0: Memory at d8105800 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: sdhci-pci
Kernel modules: sdhci-pci

```Please help! Thanks in advance!
 
Biyan.

---

### Post by thefasterblueone on 2011-08-13
try this:```
ifconfig eth0 up
```

---

### Post by biyan on 2011-08-13
Tried, but no luck. :-(
Still cannot connect to the internet.

---

### Post by Sef on 2011-08-13
Have you added any software or updated your system just before the problems started?

---

### Post by thefasterblueone on 2011-08-13
Did you run this again?

```
sudo /etc/init.d/networking restart
```


I assume you are using Network-Manager, if so you might want to try WICD to manage your network.

---

### Post by biyan on 2011-08-13
No, I have not done anything to my system.

---

### Post by biyan on 2011-08-13
Here is the message:
```

biyan@biyan-laptop:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.
[ OK ] 

```

---

### Post by biyan on 2011-08-14
Anybody got any idea? Please please help&#65281;

---

### Post by biyan on 2011-08-15
Suddenly works fine. Thank you for helping.

---

