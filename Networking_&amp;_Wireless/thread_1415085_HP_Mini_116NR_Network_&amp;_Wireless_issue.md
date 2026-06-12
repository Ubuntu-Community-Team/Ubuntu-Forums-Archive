---
title: "HP Mini 116NR Network &amp; Wireless issue"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by Redterp on 2010-02-24
Hello,

I'm getting my feet wet with UNR 9.10 on my "new" refurbished HP Mini and the install went fine off of a bootable USB flash drive that I created. 

However, I am having trouble getting the network connections to work.

I tried following Cpbl posting on his blog on how to get the wireless working but it requires installing "bcmwl-kernel-source". Unfortunately it does not exist and I do not have a connection to downalod it from any of the software sources.

(Ref: [http://cpbl.wordpress.com/2010/01/07/gnulinux-on-hp-mini-1116nr/](http://cpbl.wordpress.com/2010/01/07/gnulinux-on-hp-mini-1116nr/))

Based on Sabas310's posting on HPmini board, I ran "lspci -vv" and got the following info out:

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
    Subsystem: Hewlett-Packard Company Device 361a
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at e000 [size=256]
    Capabilities: <access denied>
    Kernel modules: sky2


For what it's worth, the wireless device info:

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1507
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

I would really appreciate it if you can shed some light on what might be the root cause here. 

**New to Ubuntu. Have a history of working with linux environments once installed for sys admin work but not troubleshooting like this.

---

