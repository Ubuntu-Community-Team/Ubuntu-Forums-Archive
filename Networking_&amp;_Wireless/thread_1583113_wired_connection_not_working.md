---
title: "wired connection not working"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by cportiz on 2010-09-27
Hello everyone,
I have recently installed ubuntu 10.04 LTS on a gateway netbook lt303u.  My wireless works perfectly, but for some reason, connecting directly to the ethernet port does not (it doesn't even light up when connected to the laptop).
I have tested the cable on another computer to confirm the internet is working. I have checked that my MAC address is allowed on the network.  I tried disconnecting from all wireless networks.
Here is the output from lspci -v relevant to ethernet and wireless.

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 028c
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at a000 [size=256]
	Memory at cfdef000 (64-bit, prefetchable) [size=4K]
	Memory at cfdf0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at cfd00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e016
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

Also, if I go to system/preferences/network connections, there is indeed a connection "Auto eth0" that says to connect automatically and has the correct MAC address.

I have no idea what to do next.
Please help!
Thanks,
Carlos
p.s. apologies if this has been dealt with already - please point me to it because I couldn't find it

---

### Post by grahammechanical on 2010-09-27
Some further information would be useful. Try opening a terminal. Applications>Accessories>Terminal and putting in the code ```
nm-tool
```. See if the listing includes Device eth0. Is it listed as connected?

Regards.

---

