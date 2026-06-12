---
title: "Slow upload speeds over LAN"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by isecore on 2010-01-10
I'm trying to figure out why I'm getting slow upload rates when copying stuff to other devices on my LAN.

I've got a 100mbps LAN setup at home, yet I never get more than about 5.5 megabytes/second when uploading stuff to other computers. Why is this? It seems rather slow in my opinion. Should be around 10-11 megabytes per second instead. When downloading things (i.e. copying from other machines to this machine) it goes fast, 11-12 megabytes per second. All other machines have various 100mbit-capable NICs.

Tried searching forums and googling, but to no avail.

Running Ubuntu 9.10 Karmic AMD64 on a Phenom 9500 with 4 gigs of RAM. NIC is some onboard realtek thing, lspci -v reports it as

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at ce00 [size=256]
	Memory at fdbff000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at fda00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169
```

---

