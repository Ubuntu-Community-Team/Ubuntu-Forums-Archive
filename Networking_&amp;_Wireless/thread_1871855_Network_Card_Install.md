---
title: "Network Card Install"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by kinadian on 2011-10-29
I just a new server for a client.  It's a CybertronPC with an Intel onboard network card.  It has an Intel DH67BL Media servers motherboard.

I downloaded and installed Ubuntu 10.04 LTS.  Everything is great except that the installer couldn't install the network card.

I did some searching around to try and find out why but I'm not having much luck.

I ran lspci -vnn and searched through the output to find this:

00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1503] (rev 05)
Subsystem: Intel Corporation Device [8086:2002]
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at fe500000 (32-bit, non-prefetchable) [size=128K]
Memory at fe528000 (32-bit, nonprefetchable) [size=4K]
I/O ports at f080 [size=32]
Capabilities: <access denied>

I also ran sudo cat /var/log/dmesg | grep -i eth but that didn't produce any output.

Running ifconfig only gives me the loopback interface.

Any ideas as to how I can proceed from here to install the network card?

Thanks.

---

