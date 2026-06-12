---
title: "r8168 on Ubuntu 11.10 Kernel 3.x.x, part 2"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by wtruong on 2012-01-07
On Unbuntu 11.10, 3.0.0-14-generic:

[http://ubuntuforums.org/showthread.php?t=1861865](http://ubuntuforums.org/showthread.php?t=1861865)

I've followed the steps above to change my kernel module to load r8168 instead of r8169. However, I'm still getting dropped connectivity on the ethernet connection.

Network-Manager also keeps complaining with popups with "Wired network\n Connection Established" and "Wired network\n Disconnected".

I checked the syslog and it doesn't report eth0 going down or up, so I assume it stays up. 

I am sharing my wifi connection on my computer to computers with this ethernet card attached to a switch. On the other computer, icmp_seq is inconsistent when I ping a website and sometimes gets dropped:

64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=5 ttl=50 time=29.4 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=9 ttl=50 time=23.0 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=12 ttl=50 time=36.7 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=13 ttl=50 time=23.7 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=16 ttl=50 time=22.3 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=17 ttl=50 time=19.5 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=20 ttl=50 time=23.9 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=21 ttl=50 time=21.4 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=24 ttl=50 time=53.5 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=28 ttl=50 time=34.1 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=32 ttl=50 time=23.5 ms
From 10.42.43.1 icmp_seq=33 Destination Port Unreachable
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=35 ttl=50 time=26.2 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=39 ttl=50 time=23.9 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=43 ttl=50 time=99.5 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=47 ttl=50 time=31.1 ms

Anyone experiencing this issue?

lspci details:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 41
	I/O ports at de00 [size=256]
	Memory at fdaff000 (64-bit, prefetchable) [size=4K]
	Memory at fdae0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at fda00000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 12-34-56-78-12-34-56-78
	Kernel driver in use: r8168
	Kernel modules: r8168

---

### Post by wtruong on 2012-01-08
bump

---

