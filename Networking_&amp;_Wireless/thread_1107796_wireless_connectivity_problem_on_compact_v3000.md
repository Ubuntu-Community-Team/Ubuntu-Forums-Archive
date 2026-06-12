---
title: "wireless connectivity problem on compact v3000"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by jonglabu on 2009-03-27
Hi all..
I cannot get thru internet using wireless connection has i already tried everything..your kindly assistant/expertise is badly needed..tq

daniel@ubuntu:~$ sudo lshw -C network 
[sudo] password for daniel: 
  *-network               
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network 
       description: Ethernet interface 
       product: PRO/100 VE Network Connection 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:08:08.0 
       logical name: eth0 
       version: 02 
       serial: 00:16:d3:93:6c:3a 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=203.121.104.243 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 82:dc:6b:91:91:eb 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
daniel@ubuntu:~$ lspci -vv 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx- 
	Latency: 0 
	Capabilities: <access denied> 
	Kernel driver in use: agpgart-intel 
	Kernel modules: intel-agp 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin A routed to IRQ 16 
	Region 0: Memory at d4200000 (32-bit, non-prefetchable) [size=512K] 
	Region 1: I/O ports at 1800 [size=8] 
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M] 
	Region 3: Memory at d4300000 (32-bit, non-prefetchable) [size=256K] 
	Capabilities: <access denied> 
	Kernel modules: intelfb 

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Region 0: Memory at d4280000 (32-bit, non-prefetchable) [size=512K] 
	Capabilities: <access denied> 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Interrupt: pin A routed to IRQ 22 
	Region 0: Memory at d4340000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: HDA Intel 
	Kernel modules: snd-hda-intel 

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0 
	I/O behind bridge: 00002000-00002fff 
	Memory behind bridge: d2000000-d3ffffff 
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff 
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR- 
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B- 
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR- 
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B- 
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
	Memory behind bridge: d4000000-d40fffff 
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR- 
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B- 
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin A routed to IRQ 23 
	Region 4: I/O ports at 1820 [size=32] 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin B routed to IRQ 19 
	Region 4: I/O ports at 1840 [size=32] 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin C routed to IRQ 21 
	Region 4: I/O ports at 1860 [size=32] 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin D routed to IRQ 16 
	Region 4: I/O ports at 1880 [size=32] 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin A routed to IRQ 23 
	Region 0: Memory at d4544000 (32-bit, non-prefetchable) [size=1K] 
	Capabilities: <access denied> 
	Kernel driver in use: ehci_hcd 
	Kernel modules: ehci-hcd 

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01) 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64 
	I/O behind bridge: 00003000-00003fff 
	Memory behind bridge: d4100000-d41fffff 
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR- 
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B- 
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
	Capabilities: <access denied> 

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Capabilities: <access denied> 
	Kernel modules: iTCO_wdt, intel-rng 

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP]) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin A routed to IRQ 18 
	Region 0: I/O ports at 01f0 [size=8] 
	Region 1: I/O ports at 03f4 [size=1] 
	Region 2: I/O ports at 0170 [size=8] 
	Region 3: I/O ports at 0374 [size=1] 
	Region 4: I/O ports at 1810 [size=16] 
	Kernel driver in use: ata_piix 
	Kernel modules: ata_piix 
 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO]) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0 
	Interrupt: pin B routed to IRQ 20 
	Region 0: I/O ports at 18d0 [size=8] 
	Region 1: I/O ports at 18c4 [size=4] 
	Region 2: I/O ports at 18c8 [size=8] 
	Region 3: I/O ports at 18c0 [size=4] 
	Region 4: I/O ports at 18b0 [size=16] 
	Region 5: Memory at d4544400 (32-bit, non-prefetchable) [size=1K] 
	Capabilities: <access denied> 
	Kernel driver in use: ata_piix 
	Kernel modules: ata_piix 

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Interrupt: pin B routed to IRQ 20 
	Region 4: I/O ports at 18e0 [size=32] 
	Kernel driver in use: i801_smbus 
	Kernel modules: i2c-i801 

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
	Subsystem: Hewlett-Packard Company Device 1364 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Interrupt: pin A routed to IRQ 19 
	Region 0: Memory at d4000000 (32-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: b43-pci-bridge 
	Kernel modules: wl, ssb 

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 64 bytes 
	Interrupt: pin A routed to IRQ 20 
	Region 0: Memory at d4100000 (32-bit, non-prefetchable) [size=4K] 
	Region 1: I/O ports at 3000 [size=64] 
	Capabilities: <access denied> 
	Kernel driver in use: e100 
	Kernel modules: e100 

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 32 (500ns min, 1000ns max) 
	Interrupt: pin A routed to IRQ 16 
	Region 0: Memory at d4101000 (32-bit, non-prefetchable) [size=2K] 
	Capabilities: <access denied> 
	Kernel driver in use: ohci1394 
	Kernel modules: ohci1394 

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 32 
	Interrupt: pin B routed to IRQ 18 
	Region 0: Memory at d4101800 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 
	Kernel driver in use: sdhci-pci 
	Kernel modules: sdhci-pci 

08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Interrupt: pin B routed to IRQ 11 
	Region 0: Memory at d4101c00 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05) 
	Subsystem: Hewlett-Packard Company Device 30b2 
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Interrupt: pin B routed to IRQ 11 
	Region 0: Memory at d4102000 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

daniel@ubuntu:~$ uname -a 
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux 
daniel@ubuntu:~$ lsb_release -d 
Description:	Ubuntu 8.10 
daniel@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:93:6c:3a  
          inet addr:203.121.104.243  Bcast:203.121.104.255  Mask:255.255.255.224 
          inet6 addr: fe80::216:d3ff:fe93:6c3a/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:4974 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4135 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5694653 (5.6 MB)  TX bytes:519936 (519.9 KB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B) 

pan0      Link encap:Ethernet  HWaddr 82:dc:6b:91:91:eb  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

daniel@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

daniel@ubuntu:~$ daniel@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:93:6c:3a  
          inet addr:203.121.104.243  Bcast:203.121.104.255  Mask:255.255.255.224 
          inet6 addr: fe80::216:d3ff:fe93:6c3a/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5159 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4214 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5743788 (5.7 MB)  TX bytes:537374 (537.3 KB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B) 




daniel@ubuntu:~$ sudo modprobe b43 
WARNING: /etc/modprobe.d/wlAnd line 3: ignoring bad line starting with 'modprobe'

---

### Post by GeeZor on 2009-03-27
What does your /etc/nework/interfaces file look like?
Does i contain an entry for your:
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)  ??? (not sure what logical name you should look for though)

You might consider installing wpa_supplicant also (and read that manual to get it working. )

Mine looks like this:
------
iface ath0 inet static
address 192.168.2.xxx
netmask 255.255.255.0
wireless-essid gbb
gateway 192.168.2.xxx
pre-up wpa_supplicant -B -Dwext -iath0 -c/etc/wpa_supplicant.conf
#pre-up wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
iwconfig ath0 rate 48M


Hope this helps..

---

### Post by jonglabu on 2009-03-29
sorry bro for late reply...

actually my wireless is working fine after i run this cmmand below..

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart

but after i restart back i have to input those command again to activate the wireless..so i just put another command ..

echo wl|sudo tee -a /etc/modules
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wlAnd that should allow it to work when the system restarts


and the problem arise..

my wireless is not working and when i put those command..

sudo moprobe -r b43 b44 ssb wl

WARNING: /etc/modprobe.d/wlAnd line 3: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/wlAnd line 3: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/wlAnd line 3: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/wlAnd line 3: ignoring bad line starting with 'modprobe

---

