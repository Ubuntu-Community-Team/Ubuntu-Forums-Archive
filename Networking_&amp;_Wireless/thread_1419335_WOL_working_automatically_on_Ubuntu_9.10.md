---
title: "WOL working automatically on Ubuntu 9.10"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by vinicius.vbf on 2010-03-01
Hi there!

I was running Ubuntu 9.04 on my box (Tyan Tiger i7501R (S2735)) and the WOL scripts that uses the ethtool ([http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)) were working perfectly. But since I've made a fresh installation of the Ubuntu 9.10, my WOL is working automagically. I mean, don't even have the ethtool installed in my box, but everything works like a charm.

I'm using the e1000 network driver and my uname -a says:

Linux ubuntu 2.6.31-19-generic-pae #56-Ubuntu SMP Thu Jan 28 02:29:51 UTC 2010 i686 GNU/Linux

and the lspci shows the following about my network device:

4:01.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
	Subsystem: Intel Corporation Device 1011
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 48
	Memory at fe9c0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at a400 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e1000
	Kernel modules: e1000

Does anyone knows what is happening? Is it possible that the driver itself is setting the correct flags to the network device?

Not knowing how this "feature" is being activated is driving me crazy.

Thanks!

---

