---
title: "Wireless Driver for ubuntu 12.10 on Dell inspiron 5520"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by xxsmarty on 2012-10-28
I have installed ubuntu 12.10 on my dell inspiron 5520 laptop.
I have tried many methods but I can't get the wireless working.

I have :
```


$lspci -vvv

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
Subsystem: Dell Device 056a
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
Latency: 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
I/O behind bridge: 00003000-00003fff
Memory behind bridge: c0000000-c0ffffff
Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Subsystem: Dell Device 056a
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 45
Region 0: Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
Region 2: Memory at b0000000 (64-bit, prefetchable) [size=256M]
Region 4: I/O ports at 4000 [size=64]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
Subsystem: Dell Device 056a
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 42
Region 0: Memory at c1600000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
Subsystem: Dell Device 056a
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 44
Region 0: Memory at c1614000 (64-bit, non-prefetchable) [size=16]
Capabilities: <access denied>
Kernel driver in use: mei
Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
Subsystem: Dell Device 056a
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 16
Region 0: Memory at c1619000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
Subsystem: Dell Device 056a
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 46
Region 0: Memory at c1610000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
I/O behind bridge: 00002000-00002fff
Memory behind bridge: fff00000-000fffff
Prefetchable memory behind bridge: 00000000c1400000-00000000c14fffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
I/O behind bridge: 0000f000-00000fff
Memory behind bridge: c1500000-c15fffff
Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
Subsystem: Dell Device 056a
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin A routed to IRQ 23
Region 0: Memory at c1618000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
Subsystem: Dell Device 056a
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Capabilities: <access denied>
Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
Subsystem: Dell Device 056a
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin B routed to IRQ 41
Region 0: I/O ports at 4088 [size=8]
Region 1: I/O ports at 4094 [size=4]
Region 2: I/O ports at 4080 [size=8]
Region 3: I/O ports at 4090 [size=4]
Region 4: I/O ports at 4060 [size=32]
Region 5: Memory at c1617000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
Subsystem: Dell Device 056a
Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Interrupt: pin C routed to IRQ 10
Region 0: Memory at c1615000 (64-bit, non-prefetchable) [size=256]
Region 4: I/O ports at 4040 [size=32]
Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series] (prog-if 00 [VGA controller])
Subsystem: Dell Device 056a
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 47
Region 0: Memory at a0000000 (64-bit, prefetchable) [size=256M]
Region 2: Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
Region 4: I/O ports at 3000 [size=256]
Expansion ROM at c0020000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: fglrx_pci
Kernel modules: fglrx, radeon

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
Subsystem: Dell Device 056a
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 43
Region 0: I/O ports at 2000 [size=256]
Region 2: Memory at c1404000 (64-bit, prefetchable) [size=4K]
Region 4: Memory at c1400000 (64-bit, prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169

08:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
Subsystem: Dell Device 0016
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 11
Region 0: Memory at c1500000 (64-bit, non-prefetchable) [size=32K]
Capabilities: <access denied>


```

```

$sudo lshw -c network
 [sudo] password for arun: 
  *-network               
   description: Ethernet interface
   product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:07:00.0
   logical name: eth0
   version: 05
   serial: d4:be:d9:2d:d3:86
   size: 100Mbit/s
   capacity: 100Mbit/s
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=90.0.2.135 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
   resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
 *-network UNCLAIMED
   description: Network controller
   product: Broadcom Corporation
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:08:00.0
   version: 01
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list
   configuration: latency=0
   resources: memory:c1500000-c1507fff

```
I have tried on many sites but can't get wireless working.
Please Help.
I have BCM43142 802.11b/g/n (rev01) wireless card

---

### Post by Abhinav Kumar on 2012-10-28
May be there is no wireless driver in your system.
just grab a LAN wire and use a wired connection to connect to the internet.
I assume system connects to the wired network and there is no proxy.

However, if there is a proxy, enter desired proxy settings by typing  Network Proxy on the dashboard. Now the username and password need to be given
For this, type in the terminal 
sudo gedit /etc/apt/apt.conf
and after giving the password follow the following format in apt.conf file
Acquire  http:: proxy "http://username: password@ur_PROXY"
Acquire  http:: proxy "ftp://username: password@ur_PROXY"
Acquire  https:: proxy "https://username: password@ur_PROXY"
save it and now you should see your computer can connect to the wired connection
through the proxy.:)

Now, type additional drivers on the dashboard.
Ubuntu should automatically select the driver for you. just install and restart may be required after the install.

---

### Post by lawadm1 on 2013-01-11
I know this is a little late, but I had the same issue.  Here's what I had to do to get it working on my Dell 5520:

1) Install Ubuntu 12.04 64 bit
2) apt-get install dkms
3) Download the deb package: [http://wielki.tk/vostro/debs/wlan_amd64.deb](http://wielki.tk/vostro/debs/wlan_amd64.deb)
4) sudo dpkg -i wlan_amd64.deb[]("http://wielki.tk/vostro/debs/wlan_amd64.deb")

I could not get wireless to work with 12.04 32 bit, and I couldn't even get 12.10 to install.  It would freeze up on the trigger portion.

Jeff

---

### Post by Hadaka on 2013-01-11
Hi, here is a how to link..

[http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)

* for 64 bit ONLY*

check for 32 or 64 bit
```
arch 
```

---

