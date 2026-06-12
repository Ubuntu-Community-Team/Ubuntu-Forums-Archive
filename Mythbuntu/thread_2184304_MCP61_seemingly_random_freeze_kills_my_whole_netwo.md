---
title: "MCP61: seemingly random freeze kills my whole network"
date: 2013-10-28
forum: Mythbuntu
---

### Post by d2a on 2013-10-28
I've recently moved my whole setup onto new (to me) hardware

Mobo: Asus M2N-MX
Processor: AMD Athlon™64 X2 5400+ 2.8GHZ SOCKET AM2 CPU (BRISBANE CORE)
Memory: 2x 1GB DDR2 PC2-6400 800MHz
Graphics: nVidia GeForce 8400GS 256MB
Nova-t 500 DVB-T dual tuner
Wired gigabit ethernet (to megabit router)

00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 43
	Memory at dbefd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c480 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

Mythbuntu 12.04 64bit 0.26 install ran beautifully and all hardware is up and working well in general. However:

over the course of perhaps 24-72 hours the system will freeze completely. display is active but frozen, time within theme no longer updates, mouse and keyboard input not recognised. more confusingly, not only does network go down, so machine cannot be pinged and ssh is unavailable, but the freeze also effects other devices on the network, so that network connectivity is lost for my other machines. Disconnecting network cable brings other machines' connectivity back up and all is well once myth machine is hard reset, until the next freeze.

since the freeze appears to be instant, i can't find anything written to the logs to help diagnose the problem. i tried remote logging, but again, once the network dies, nothing gets through.

any suggestions for further diagnosis gratefully received...

---

### Post by newlinux on 2013-10-29
sounds like a potentially a hardware issue. Which logs where you looking at? You should note the times of the freezes and look in your logs at what is going on at timestamps leading up to the freeze. Start with syslog. If nothing shows up you may just need to comb through your logs and see if you see any red flags in general. Tracking freezes down often takes a series of steps (isolating it as a hardware or software problem, then tracking down the hardware or software offender).
Are all the machines connected to the same switch?

---

### Post by d2a on 2013-10-29
i've checked most logs - myth specific, syslog etc. no one thing is consistently happening at the point of freeze, and nothing is exactly at the time of the freeze. i suspect a misbehaving NIC. i've disabled the onboard NIC and added a temporary wifi adapter, so that i can discount it as a cause. so far so good - although the network is not entirely stable, at least it hasn't frozen or killed the network. if this keeps up i'm tempted to just buy a pci nic and bypass the issue...

simplified diagram below (--- = ethernet ))) = wifi):

mythbox ---- switch/modem ---- wireless AP ))) laptop

after freeze wireless AP still connected to laptop but unable to connect to switch/modem. nic lights flashing on mythbox after freeze

---

