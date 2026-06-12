---
title: "lspci says wireless controller disabled"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by james.wilde on 2010-01-03
Thought I posted this message about an hour ago, but can't find it in the forum.

I am installing 9.10 on an old Dell laptop.  This machine has the built-in Dell wireless controller and a pcmcia d-link DWL-650+ card.  The built-in controller has poor reception, so I prefer to use the d-link.  This machine also runs XP where the d-link works fine.

On installation of Ubuntu 9.10 the opsys has not picked up the d-link card.  This is what I get from lspci -v:

01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
	Subsystem: Dell Device 0003
	Flags: bus master, fast devsel, latency 32, IRQ 5
	Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
	Subsystem: D-Link System Inc Device 3b00
	Flags: medium devsel, IRQ 11
	I/O ports at e000 [disabled] [size=32]
	Memory at 28010000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Memory at 28000000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 2

As one can see, the card is visible to the system but is disabled.  dmesg gives no mention of acx, texas or d-link.  Is there any way I can enable the card before I start trying to make it work? I assume I have to enable it before I try to make it work.

Incidentally, the network device can't be seen under Devices in Network Tools.  On the other hand, the built-in controller is there twice, once as Wireless Interface (wlan0) and once as Unknown interface (wmaster0).  Can't get either of them to work.

TIA

//James

---

### Post by gordintoronto on 2010-01-03
Did you find this web site:
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) 

The card automatically powers down to a "doze" mode.  Perhaps that is why it's disabled.

The manufacturer's web site is:
[http://www.dlink.ca/products/?pid=DWL-650%2b](http://www.dlink.ca/products/?pid=DWL-650%2b)

---

