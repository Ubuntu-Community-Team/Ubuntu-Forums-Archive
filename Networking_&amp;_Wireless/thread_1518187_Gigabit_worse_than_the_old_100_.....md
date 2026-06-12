---
title: "Gigabit worse than the old 100 ...."
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by Nokao on 2010-06-26
Hi ... 

I have bought a new ethernet gigabit switch, and with Windows everything is fine.
With Ubuntu 10.0.4 I move data slower than with a 100Mb (something like 100 Kb/s).

But what is strange that when I plugged the switch with Ubuntu OS open, everything was fine and fast.

The problems appeared AFTER a reboot, so I suppose that:

When the system starts, it loads a 1000 mb/s driver that is not working.
But if it loads a 100 mb/s driver, everything is fine.

So I'm asking you how to force my Ubuntu OS to use my new gigabit switch as a normal 100 mb/s switch.

My motherboard however is this:
[http://www.ciao.it/ASUS_M2NPV_MX__656544#productdetail](http://www.ciao.it/ASUS_M2NPV_MX__656544#productdetail)

---

### Post by jonobr on 2010-06-26
what type ethernet card do you have?

---

### Post by Nokao on 2010-06-29
nVidia nForce chipset ...

---

### Post by Nokao on 2010-06-29
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 816a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

---

### Post by Nokao on 2010-06-29
I found this bug:
[http://www.gossamer-threads.com/lists/linux/kernel/878643](http://www.gossamer-threads.com/lists/linux/kernel/878643)

Should I remove MSI ?
Or is it possible to just force the use of another driver?

---

