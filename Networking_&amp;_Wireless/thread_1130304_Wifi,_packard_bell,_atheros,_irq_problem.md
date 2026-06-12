---
title: "Wifi, packard bell, atheros, irq problem"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by mark.roeling on 2009-04-19
Hi

dmesg log:
[   11.355863] ath_hal: module license 'Proprietary' taints kernel.
[   11.357857] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.375313] wlan: 0.9.4
[   11.387267] ath_pci: 0.9.4
[   11.387337] ath_pci 0000:00:06.0: enabling device (0000 -> 0002)
[   11.387348] ath_pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   11.387436] wifi%d: request_irq failed

The kernel switch mentioned is one of many I've tried, but without success. The installed windows xp however has no problem detecting and using wireless networking.

lspci -v:
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7084
	Flags: medium devsel
	Memory at 20000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci, ath5k

So the adapter can be detected.

I've tried several things: updated madwifi, ndiswrapper, even with newest windows drivers, but no luck yet.

---

