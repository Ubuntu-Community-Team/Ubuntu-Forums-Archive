---
title: "Try a new wifi driver?"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by bonfire89 on 2012-01-18
Hey all,

I have a Dell Latitude E6410, I think this is my wifi card. It says ethernet but I guess it is combined on one module? I didn't see one for wireless

```
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
	Subsystem: Dell Device 040a
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at d6900000 (32-bit, non-prefetchable) [size=128K]
	Memory at d6980000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 7040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

```

I have been having troubles with wifi at school particularly after upgrading to 11.10. I tested with another Ubuntu 11.10 laptop and wifi worked perfectly. The wifi on this Dell works perfectly on wireless networks other than the one at school. The problem is that it takes a long time to associate with the network, long as in, hours at times, but, I have seen it connect before. Is it possible that I could try some other driver? Or something like that?

---

### Post by inobe on 2012-01-18
bonfire, have a look here to troubleshoot the issues.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

a side note, clearing previous "past" connections may also help.

---

