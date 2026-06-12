---
title: "Kubuntu 12.10 no DHCP on Intel 82566DM-2 eth. card (HP dc7800)"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by TK999 on 2013-03-12
Hello everyone,

I have problems establishing a DHCP wired connection using a HP dc7800 Convertible Minitower and Kubuntu 12.10 (kernel 3.5.0-25).

I tried using a live Arch Linux system with dhcpcd, Fedora 18 with GNOME 3.6, Fedora 18 KDE Spin and Kubuntu 12.10; fetching addresses via DHCP*—*including forcing a static DHCP server with dhcp -S*—*results in a timeout (in KDE and GNOME, stuck at "setting network address"). Attempting to set the network properties statically using iproute2 also does not work. dmesg does not output any errors related to my Ethernet device (eth0) or its e1000e driver. The network card itself was fully functional under Linux Mint 13 MATE*—*using the same e1000e driver*—*and Windows 7 also works with it flawlessly. The network cable, wall socket and network topology are also functioning, as an Arch laptop connected to the same socket is able to connect without problems. Googling the Ethernet device's name for related errors brings up no useful hits.

Are there any other tests or software I should try to run before renouncing this as hopeless? Thanks in advance. Command output is below:
Here is lspci -vv:
```

00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Device 2818
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin B routed to IRQ 42
        Region 0: Memory at f0180000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at f01a5000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 1100 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0100c  Data: 41a9
        Capabilities: [e0] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: e1000e
        Kernel modules: e1000e


```
sudo lshw for the motherboard:
```
  *-core
       description: Motherboard
       product: 0AACh
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC7487GC7
```

---

