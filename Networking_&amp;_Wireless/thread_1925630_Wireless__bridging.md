---
title: "Wireless / bridging"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by Ariana Grande on 2012-02-14
Hey guys, I am having a slight problem with my Ubuntu / bridging. Originally my Dell 910 (using right now to type this) was on XP. It blue screened so I made the switch over to Ubuntu (10.10). At first, I could not use the wireless, so I had to plug an ethernet cable in and use "Additional Drivers" to get my wireless to work. Now, I have ran into another problem. I am trying to bridge my connection but am unsuccessful.

My setup looks something like this at the moment. 
PC (Windows 7) == Ethernet cable ==> Laptop (Ubuntu) == Wireless ==> Router

I am trying to supply internet connectivity to the Windows 7 PC, which will otherwise have no internet access. 

I am able to connect to the internet on my laptop, but bridging is a whole different story. I am trying to bridge with 'Firestarter'. When I originally started trying to bridge, I had 3 options. br0 (Unknown Device), eth0, and eth1. The problem is, my only internet inputs on this PC are wireless, and one Ethernet port. So it SHOULD look like wlan0 & eth0. Now, after a computer reset br0 mysteriously disappeared. Now I am left with eth0, and eth1. Eth0 is absolutely nothing because when I use it, I get an error saying it's 'not ready for use' or something along those lines. I see Eth1 is getting incoming / outgoing traffic. So that's either my ethernet to my PC, or my wireless to my router. Now my problem is, how do I get my wireless card to be wlan0, and my ethernet port to be eth0 so I can successfully bridge my connection?

My wireless card has the Broadcom STA Wireless driver for the 43xx series installed. Which is what gives me internet access, but wlan0 does not appear under Terminal 'Ifconfig' nor under 'Firestarter'. Which leads me to believe its active, but somehow hidden. Could anyone shed me some light on how I may go about fixing my problem?

- Thanks!

EDIT: I got more information on the Ethernet port and the wireless card for anyone trying to help me. c:

```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Broadcom Corporation Device 04b5
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at 2000 [size=256]
	Memory at f0610000 (64-bit, prefetchable) [size=4K]
	Memory at f0600000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f0620000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by Sudoku11 on 2012-02-15
If you are having trouble with your wireless card, you may want to consider reinstalling the wireless driver.  Have you tried installing ndiswrapper?

---

### Post by Cheesehead on 2012-02-15
Network Manager has a "share this connection" feature that creates a bridge for you, so mucking about with trying to create a bridge manually seems unneccessary.

Network Manager --> Edit Conenctions --> Wireless --> Edit --> IPv4 Settings --> Method

But your question: 
1) Check the MAC addresses in /etc/udev/rules.d/*-persistent-net.rules
That file ensures your device gets mapped to the same interface every time. If you have a 'ghost' eth*, it's usually because of that file.

2) A real bridge is represented a separate interface (normally, br0). Generally, a bridge should be brought up/down each time any component interface (eth0, wlan0) is brought up/down. That's not automatic - normally it's done by a bunch of scripting in /etc/network/interfaces...which, of course, then prevents Network Manager from doing the job of autodetection and autoconfiguration that you originally wanted it to do.

The 'brctl' command is your friend to create/add/monitor/delete/destroy a bridge.

---

