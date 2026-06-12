---
title: "&quot;Create new wireless network&quot; not working"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by Xavier Oddmon on 2010-08-25
I have recently moved into a dorm, which does not have wifi. There is an ethernet port, which my laptop is connected to, and I'd like to make a wifi network for my phone to connect to (since I don't have an unlimited data plan.) I have tried making a new network with network-manager, but it is not visible on my phone. When I try to connect manually on my phone, it says that there are no networks by the name I specified. My laptop is an iBuyPower LX750 (I believe an MSI ex700?) The phone is a palm pre plus, but other computers (running windows 7) don't see my new network either. My hardware is as follows:
```
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at f88fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 4327
	Flags: bus master, fast devsel, latency 0, IRQ 30
	I/O ports at c800 [size=256]
	Memory at f89ff000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at d0c00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169
```
I do have dnsmasq-base installed, but I don't believe that would make a difference in finding the network, only connecting to the internet through it.

---

### Post by easytiger on 2010-10-14
For what its worth i have the exact same issue. It used to work but i think something has broken in an update.

Using a 
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300

---

### Post by soreau on 2011-09-15
I have the same issue here using atheros chipset. I can at least get it to broadcast using hostapd but still can't connect.

---

### Post by nothingspecial on 2011-09-15
Please create your own thread on the subject.

Closed.

---

