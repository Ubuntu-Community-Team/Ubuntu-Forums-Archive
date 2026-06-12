---
title: "Unstable connection on 11.04"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by Bardobrave on 2011-07-15
Hi.

I've bought a new computer and I've installed ubuntu 11.04 x64 in one partition to abandon windows in a step by step basis.

However, after installation network connections seems unstable, usually I lose connection after few minutes of surfing or downloading anything. All in the network configuration seems ok, and when I lose connection simply by disabling and reenabling it it comes back again. 

I've tried to specify manually the network parameters instead of using an automatic configuration, but nothing changed at all.

I'm quite new to linux and don't have much idea about for where to start searching for a solution.

In the windows partition the network connection is perfectly stable and shows no problem at all.

Any ideas or sugerences?
Thank you.

---

### Post by ratcheer on 2011-07-15
My new computer did that, too. After a lot of searching, I discovered that Ubuntu had loaded the wrong driver for my NIC.

Please open a Terminal and run "sudo lspci -v". Post the output into a reply. That will tell us your NIC model and what kernel driver is being loaded.

Tim

---

### Post by Bardobrave on 2011-07-19
Hi, sorry for the lapse in answering, I've been away from the computer a couple of days.

This is the Ethernet controller exit for the pci listing command. Certainly the behaviour points to some type of driver problem. Maybe I should seek for a newer or more suitable version of network driver.

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 41
	I/O ports at de00 [size=256]
	Memory at fbdff000 (64-bit, prefetchable) [size=4K]
	Memory at fbdf8000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

Any suggerences?

---

### Post by jmoorse on 2011-07-19
Please search the forums next time before posting.  This exact same issue was addressed less than 24h ago:

[http://ubuntuforums.org/showthread.php?t=1806348](http://ubuntuforums.org/showthread.php?t=1806348)

The resolution was:

[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by Bardobrave on 2011-07-19
Well... to be fair I've posted this three days ago :P

---

### Post by jmoorse on 2011-07-19
> **Bardobrave said:**
> Well... to be fair I've posted this three days ago :P

Agreed.  Please search though.  "Let us help you...help us!"

---

### Post by Bardobrave on 2011-07-19
Totally agree.

I've followed your link and problem seems to be solved. Thanks a lot.

---

