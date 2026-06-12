---
title: "Wireless Network - 'disconnected' on ubuntu 9.10"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by mjsilverstri on 2010-04-15
Hi,

I am running ubuntu 9.10 on my HP Pavilion dv7 laptop, which has a intell 802.11n wireless card.

When I click the Network notification icon, it said 'Wireless Network-disconnected'.

I have tried 
sudo apt-get install linux-backports-modules-karmic-generic
sudo rmmod -f iwlagn
sudo modprobe iwlagn

But it still said 'disconnected'.
Please help me with this.

> 
$ dmesg | grep iwl
[   16.551480] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   16.551483] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   16.551592] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.551620] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.551687] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[   16.585169] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.585263] iwlagn 0000:02:00.0: irq 36 for MSI/MSI-X
[   16.622497] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.273847] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   19.322557] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   19.322562] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   19.325263] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   19.325268] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   19.327622] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   19.327626] iwlagn 0000:02:00.0: Could not read microcode: -2
[   21.715374] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   21.717767] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   21.717773] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   21.720549] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   21.720555] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   21.723212] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   21.723217] iwlagn 0000:02:00.0: Could not read microcode: -2




> 
02:00.0 Network controller: Intel Corporation Device 4239 (rev 35)
Subsystem: Intel Corporation Device 1311
Flags: bus master, fast devsel, latency 0, IRQ 36
Memory at da100000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlagn
Kernel modules: iwlagn


---

