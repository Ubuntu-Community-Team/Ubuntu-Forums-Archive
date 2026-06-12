---
title: "Timing issue during bootup?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by daz0001 on 2009-02-24
I have a GF7025-M2 motherboard with on-board ethernet:

```

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 2507
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 215
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d800 [size=8]
	Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
	Memory at fe029000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping

```

Now, I have a problem where the link light doesn't come on, and I get the kernel message:
```
[   32.400111] eth0: no link during initialization.
```
and ethtool will report that there is no link detected.

Now, if I've discovered that if I plug the cable in at some point during the boot process (rather than having it plugged in before I switch on), then the link light will come on, and I get the following in my kernel log:
```
 [   32.250901] eth0: link up.
```
and ethtool will report that the link is up. 
I can then connect to the internet. 

Any ideas why this is happening?

---

### Post by daz0001 on 2009-02-25
I think it might be related to this: [https://bugs.launchpad.net/ubuntu/+bug/272059]("https://bugs.launchpad.net/ubuntu/+bug/272059") 

I upgraded from ubuntu 8.04 to 8.10 and the issue seems to have been resolved?

---

