---
title: "Cannot Get Kismet Working"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by Meads on 2009-06-06
I have an atheros 5007 chipset, i followed [http://inportb.com/2008/07/27/madwifi-support-for-ar5007-ar2425-with-injection-aircrack/](http://inportb.com/2008/07/27/madwifi-support-for-ar5007-ar2425-with-injection-aircrack/) and everything went fine until i come to using kismet which gives me the error below.

```
ian@ian-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'source=madwifi' in source 'source=madwifi,wifi0,default'
Done.

```
I have tried all variants of the 'madwifi' source inclusing madwifi_ag etc and they all produce the same result.
heres lspci -vv
```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at 54100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci

```

When i run airmon it shows my chipset on wifi0 using the madwifi-ng driver so i cannot understand why it is not working with kismet.

Any ideas?

Thank You.

---

### Post by Meads on 2009-06-07
Anyone?

---

