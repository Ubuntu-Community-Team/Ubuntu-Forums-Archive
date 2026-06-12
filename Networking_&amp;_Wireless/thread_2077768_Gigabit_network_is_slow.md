---
title: "Gigabit network is slow"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by ericus on 2012-10-29
Hi all.
I have a problem with my gigabit-LAN. The setup looks like this:
Internet - ClearOS Firewall - Gigabit-switch - clients.

**Computer #1 (desktop):**
3.4 GHz quadcore, 4GB RAM, onboard LAN (gigabit).
Primary OS: Ubuntu 12.04
Secondary OS: Windows 7

**Computer #2 (Windows 2008r2 Server):**
3.5 GHz quadcore, 16GB RAM, onboard LAN (gigabit).

The problem is that I can not achive full speed with Ubuntu > Win Server. Maximum speed that I've seen while transfering files is ~25-26MB/s, while** Win7 > Win server gives me around 90-110MB/s. So, there's no hardware problem.**

From Win Server > Ubuntu desktop the speed is about ~35MB/s.

I have tried with another NIC from Intel (PCI-E gigabit), and got the same poor performance. So what could be the problem here? I've installed the latest drivers for my onboard NIC, without any changes...

Some outputs:
ethtool eth0:
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
```

sudo lcpci -v:
```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
	Flags: bus master, fast devsel, latency 0, IRQ 49
	I/O ports at e800 [size=256]
	Memory at fafff000 (64-bit, prefetchable) [size=4K]
	Memory at faff8000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number *************
	Kernel driver in use: r8168
	Kernel modules: r8168

```

What could be the problem?

---

### Post by Sergius14 on 2012-10-29
35MB/s is a very decent disk writing speed.

Gigabit LAN exceeds any disk read/write speed by far at any home pc.

The most that you can expect is about 200/250 mbps.

Regarding you 110 MB/s, i think that in fact they are 110 mbps, since no single/regular hard drive can write at that speed.


You can really test the network speed using iperf.


But you need several switches/parameters to make a good test. There are many guides out there. You Google them.


Moving files at gigabit ethernet is limited by hard disk speeds.

---

### Post by ericus on 2012-10-29
> **Sergius14 said:**
> 35MB/s is a very decent disk writing speed.

Gigabit LAN exceeds any disk read/write speed by far at any home pc.

The most that you can expect is about 200/250 mbps.

Regarding you 110 MB/s, i think that in fact they are 110 mbps, since no single/regular hard drive can write at that speed.


You can really test the network speed using iperf.


But you need several switches/parameters to make a good test. There are many guides out there. You Google them.


Moving files at gigabit ethernet is limited by hard disk speeds.
No, the write speed is not the issue. It really runs at 90-110MB/s under Win7 > Win2k8 Server. But on the same machine, but with Ubuntu, only around 25-26MB/s. And yes, MB/s, not Mb/s.

iperf:
```
iperf -c 192.168.111.245
------------------------------------------------------------
Client connecting to 192.168.111.245, TCP port 5001
TCP window size: 96.7 KByte (default)
------------------------------------------------------------
[  3] local 192.168.111.2 port 52009 connected with 192.168.111.245 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.10 GBytes   941 Mbits/sec
```

Disk write speed:
```
dd if=/dev/zero of=/tmp/output bs=8k count=100k; rm -f /tmp/output
102400+0 records in
102400+0 records out
838860800 bytes (839 MB) copied, 9.27572 s, 90.4 MB/s

```

---

### Post by ericus on 2012-10-31
I tried using NFS instead, and the speed is about 60MB/s. So there's something with samba file sharing.

---

