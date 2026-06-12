---
title: "wifi is shown connected but no access-ubuntu 11.04 and mint 11"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by kashan on 2011-07-26
hi all...
When i logon to ubuntu or manually try to connect my wifi, popup appeares that you are connected to "bilal Javed" (my network ssid) but nothing 
opend when i try to open any website. i just installed linux ubuntu-11.04. my browser is firefox. Before this i have mint 11, i faced same problem on that,it is also a factor to change my OS. I have dual boot machine linux/W7. The same wifi perfectly connects on windows 7 without any problem.. here are some diagnosic results
```
kashan@linuxmint ~ $ ndiswrapper -l
kashan@linuxmint ~ $ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11abg  ESSID:"bilal javed"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 74:EA:3A:B9:93:EE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0
 
kashan@linuxmint ~ $ lspci-vvnn
lspci-vvnn: command not found
 
kashan@linuxmint ~ $ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
 Subsystem: Lenovo T61 [17aa:20b3]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
 Latency: 0
 Capabilities: <access denied>
 Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c) (prog-if 00 [VGA controller])
 Subsystem: Lenovo T61 [17aa:20b5]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 46
 Region 0: Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
 Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
 Region 4: I/O ports at 1800 [size=8]
 Expansion ROM at <unassigned> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: i915
 Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
 Subsystem: Lenovo T61 [17aa:20b5]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Region 0: Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
 Capabilities: <access denied>
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
 Subsystem: Lenovo ThinkPad T61 [17aa:20b9]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 45
 Region 0: Memory at fe000000 (32-bit, non-prefetchable) [size=128K]
 Region 1: Memory at fe025000 (32-bit, non-prefetchable) [size=4K]
 Region 2: I/O ports at 1840 [size=32]
 Capabilities: <access denied>
 Kernel driver in use: e1000e
 Kernel modules: e1000e
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) (prog-if 00 [UHCI])
 Subsystem: Lenovo ThinkPad T61 [17aa:20aa]
 Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 20
 Region 4: I/O ports at 1860 [size=32]
 Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) (prog-if 00 [UHCI])
 Subsystem: Lenovo ThinkPad T60 [17aa:20aa]
 Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin B routed to IRQ 21
 Region 4: I/O ports at 1880 [size=32]
 Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20 [EHCI])
 Subsystem: Lenovo ThinkPad T61 [17aa:20ab]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin C routed to IRQ 22
 Region 0: Memory at fe226400 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
 Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
 Subsystem: Lenovo ThinkPad T61 [17aa:20ac]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Interrupt: pin B routed to IRQ 47
 Region 0: Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: HDA Intel
 Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) (prog-if 00 [Normal decode])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
 I/O behind bridge: 00002000-00002fff
 Memory behind bridge: fc000000-fdffffff
 Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
 BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
  PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) (prog-if 00 [Normal decode])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
 I/O behind bridge: 00003000-00003fff
 Memory behind bridge: dc000000-df3fffff
 Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
 BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
  PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03) (prog-if 00 [Normal decode])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
 I/O behind bridge: 00004000-00004fff
 Memory behind bridge: d8000000-d9ffffff
 Prefetchable memory behind bridge: 00000000dfb00000-00000000dfbfffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
 BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
  PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) (prog-if 00 [Normal decode])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
 I/O behind bridge: 00005000-00005fff
 Memory behind bridge: d4000000-d5ffffff
 Prefetchable memory behind bridge: 00000000df800000-00000000df8fffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
 BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
  PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) (prog-if 00 [Normal decode])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
 I/O behind bridge: 00006000-00006fff
 Memory behind bridge: d0000000-d1ffffff
 Prefetchable memory behind bridge: 00000000df500000-00000000df5fffff
 Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
 BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
  PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) (prog-if 00 [UHCI])
 Subsystem: Lenovo ThinkPad T61 [17aa:20aa]
 Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 16
 Region 4: I/O ports at 18a0 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) (prog-if 00 [UHCI])
 Subsystem: Lenovo ThinkPad T61 [17aa:20aa]
 Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin B routed to IRQ 17
 Region 4: I/O ports at 18c0 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) (prog-if 00 [UHCI])
 Subsystem: Lenovo ThinkPad T61 [17aa:20aa]
 Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin C routed to IRQ 18
 Region 4: I/O ports at 18e0 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20 [EHCI])
 Subsystem: Lenovo ThinkPad T61 [17aa:20ab]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin D routed to IRQ 19
 Region 0: Memory at fe226800 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
 Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01 [Subtractive decode])
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
 I/O behind bridge: 00007000-0000afff
 Memory behind bridge: f8300000-fbffffff
 Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
 Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
 BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
  PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
 Capabilities: <access denied>
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
 Subsystem: Lenovo T61 [17aa:20b6]
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Capabilities: <access denied>
 Kernel modules: iTCO_wdt
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03) (prog-if 80 [Master])
 Subsystem: Lenovo Device [17aa:20a8]
 Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin B routed to IRQ 16
 Region 0: I/O ports at 01f0 [size=8]
 Region 1: I/O ports at 03f4 [size=1]
 Region 2: I/O ports at 0170 [size=8]
 Region 3: I/O ports at 0374 [size=1]
 Region 4: I/O ports at 1c30 [size=16]
 Region 5: I/O ports at 1c20 [size=16]
 Capabilities: <access denied>
 Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
 Subsystem: Lenovo ThinkPad T61 [17aa:20a9]
 Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Interrupt: pin A routed to IRQ 11
 Region 0: Memory at fe226c00 (32-bit, non-prefetchable) [size=256]
 Region 4: I/O ports at 1c40 [size=32]
 Kernel modules: i2c-i801
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
 Subsystem: Intel Corporation ThinkPad R60e/X60s [8086:1011]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Interrupt: pin A routed to IRQ 48
 Region 0: Memory at df3ff000 (32-bit, non-prefetchable) [size=4K]
 Capabilities: <access denied>
 Kernel driver in use: iwl3945
 Kernel modules: iwl3945
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
 Subsystem: Lenovo Device [17aa:20c6]
 Physical Slot: 1
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 168
 Interrupt: pin A routed to IRQ 16
 Region 0: Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
 Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
 Memory window 0: f4000000-f7fff000 (prefetchable)
 Memory window 1: 80000000-83fff000
 I/O window 0: 00007000-000070ff
 I/O window 1: 00007400-000074ff
 BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
 16-bit legacy interface ports at 0001
 Kernel driver in use: yenta_cardbus
 Kernel modules: yenta_socket
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04) (prog-if 10 [OHCI])
 Subsystem: Lenovo Device [17aa:20c7]
 Physical Slot: 1
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 64 (500ns min, 1000ns max)
 Interrupt: pin B routed to IRQ 17
 Region 0: Memory at f8301000 (32-bit, non-prefetchable) [size=2K]
 Capabilities: <access denied>
 Kernel driver in use: firewire_ohci
 Kernel modules: firewire-ohci
 

```
 
anybody help please... it is really freaking me up.
 
oh.. and i have lenovo t61 (may be it is adding something in trouble)
-regards

---

### Post by Peter09 on 2011-07-26
an you also supply the output of:
 
```
 
nm-tool

```
 
and
 
```
 
route

```

---

### Post by kashan on 2011-07-26
sure, here it is n sorry for late reply
```
kashan@ubuntu:~$ nm-tool 
 
NetworkManager Tool 
 
State: connected 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            e1000e 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1E:37:8E:B2:56 
 
  Capabilities: 
    Carrier Detect:  yes 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0  [Auto bilal javed] -------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            iwl3945 
  State:             connected 
  Default:           yes 
  HW Address:        00:1C:BF:BD:41:60 
 
  Capabilities: 
    Speed:           54 Mb/s 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points (* = current AP) 
    witribe_wifi:    Infra, AC:81:12:63:23:D2, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 
    *bilal javed:    Infra, 74:EA:3A:B9:93:EE, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2 
    Qurban_wireless: Infra, 00:26:82:AE:72:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2 
    PTCL-BB:         Infra, F4:3E:61:9D:5E:7E, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA 
 
  IPv4 Settings: 
    Address:         192.168.1.3 
    Prefix:          24 (255.255.255.0) 
    Gateway:         192.168.1.1 
 
    DNS:             192.168.1.1 
 

```

and

```
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0 
link-local      *               255.255.0.0     U     1000   0        0 wlan0 
default         login.router    0.0.0.0         UG    0      0        0 wlan0 
 

```

hoping it will help!!!!!!!1

---

### Post by Peter09 on 2011-07-26
Go to the network manager icon and click on it to get the menu. select edit connections. Select the wireless tab and delete your wireless access point.

Exit, and then select the network-manager icon and click on your access point - it should connect. Apart from your passphrase you should not need to enter anything else.

Looking at the route information - it seems a bit strange, so clearing the data in network-manager may help.

---

### Post by kashan on 2011-07-27
sir i did it many many times but nothing happens. But after your suggestion, i tried it once more but it followed same track as expected. please suggest something or i have to go back on windows considering linux as a nightmare.
oha... one more thing, sometimes it accesses the internet for a minutes or two but it is very rare.
-regards

---

