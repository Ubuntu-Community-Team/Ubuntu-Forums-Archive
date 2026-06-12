---
title: "Very slow local network transfer speeds"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by mellery on 2012-01-08
When transferring files between my two computeres over wireless it starts out transferring at 1.5mbs, but then quickly drops to 150kbps.  I have an inspiron n5010

Here is my lspci output, do I have the right drivers installed?

```

12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Dell XPS 8300
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbc00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: brcmsmac
	Kernel modules: bcma, brcmsmac

13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Dell Device 0447
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at e000 [size=256]
	Memory at d0b10000 (64-bit, prefetchable) [size=4K]
	Memory at d0b00000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fb200000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by praseodym on 2012-01-08
Hi,

please show
```
lsmod
```
Did you install the Broadcom-STA driver? If yes, blacklist the modules **brcmsmac**, **bcma**, and **brcm80211** and reboot. If not, blacklist them, too, and install it. Also reboot after that

---

