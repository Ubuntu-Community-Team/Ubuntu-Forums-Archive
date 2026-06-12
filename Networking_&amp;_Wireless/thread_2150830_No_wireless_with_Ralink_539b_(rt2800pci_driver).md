---
title: "No wireless with Ralink 539b (rt2800pci driver)"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by sky5564 on 2013-06-02
So i have been trying to get this card to work with no luck.

I installed the backports module:

```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```

Then lspci shows:

```
skilo@HP-2000-Notebook-PC:~$ lspci -vv -s 01:00.0
01:00.0 Network controller: Ralink corp. Device 539b
	Subsystem: Hewlett-Packard Company Device 18ed
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 7
	Region 0: Memory at 52500000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: rt2800pci
```

iwconfig then shows:

```
skilo@HP-2000-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

And then finally modprobe rt2800pci:

```
skilo@HP-2000-Notebook-PC:~$ sudo modprobe rt2800pci
[sudo] password for skilo:
WARNING: Error inserting cfg80211 (/lib/modules/3.2.0-44-generic/updates/cw-3.6/cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-44-generic/updates/cw-3.6/mac80211.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/3.2.0-44-generic/updates/cw-3.6/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/3.2.0-44-generic/updates/cw-3.6/rt2x00pci.ko): Invalid module format
WARNING: Error inserting crc_ccitt (/lib/modules/3.2.0-44-generic/kernel/lib/crc-ccitt.ko): Invalid module format
WARNING: Error inserting rt2800lib (/lib/modules/3.2.0-44-generic/updates/cw-3.6/rt2800lib.ko): Invalid module format
FATAL: Error inserting rt2800pci (/lib/modules/3.2.0-44-generic/updates/cw-3.6/rt2800pci.ko): Invalid module format 
```

---

### Post by sky5564 on 2013-06-05
Bump.

---

### Post by sky5564 on 2013-06-05
Well i just tried this same step again on a different laptop with the the same card and now everything is working.

I just did:

```
sudo modprobe rt2800pci
```

Then rebooted and everything seems to be working, I rebooted twice already and everything seems to be fine.

Gonna mark this one as solved.

---

