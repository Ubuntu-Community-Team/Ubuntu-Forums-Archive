---
title: "Realtek r8168 high packet loss"
date: 2013-02-28
forum: Networking &amp; Wireless
---

### Post by OregonTrail on 2013-02-28
I had my connection drop intermittently with an r8168 based NIC (about 1 minute dropout every 1 minute).

It seemed as thought my problem was having the r8169 kernel module loaded as others have experienced.

I followed the instructions in [this blog post]("http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/"), and installed the 8.035.00 drivers found on[ this page]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false").

It looks like I have the r8168 module loading, however the network dropouts still occur.

This is an issue as I'm trying to set this machine up as a webserver.

Any ideas?

dmesg | grep r8:

```

[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021f200000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.859374] r8168 Gigabit Ethernet driver 8.031.00-NAPI loaded
[    0.859478] r8168 0000:04:00.0: irq 45 for MSI/MSI-X
[    1.023716] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.023719] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[    8.845298] r8168: eth1: link down
[   11.575182] r8168: eth1: link up
[   11.844758] r8168: eth1: link up

```

lspci -vv:

```

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 45
    Region 0: I/O ports at d000 [size=256]
    Region 2: Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8168
    Kernel modules: r8168, r8169

```

ping google.com:
```

64 bytes from iad23s05-in-f5.1e100.net (74.125.228.5): icmp_req=24 ttl=57 time=6.30 ms
64 bytes from iad23s05-in-f5.1e100.net (74.125.228.5): icmp_req=25 ttl=57 time=6.25 ms
64 bytes from iad23s05-in-f5.1e100.net (74.125.228.5): icmp_req=26 ttl=57 time=6.18 ms
64 bytes from iad23s05-in-f5.1e100.net (74.125.228.5): icmp_req=27 ttl=57 time=6.26 ms
64 bytes from iad23s05-in-f5.1e100.net (74.125.228.5): icmp_req=28 ttl=57 time=6.24 ms
64 bytes from iad23s05-in-f5.1e100.net (74.125.228.5): icmp_req=29 ttl=57 time=6.25 ms
^C
--- google.com ping statistics ---
55 packets transmitted, 29 received, **47% packet loss**, time 54043ms
rtt min/avg/max/mdev = 6.182/6.242/6.302/0.061 ms

```

---

