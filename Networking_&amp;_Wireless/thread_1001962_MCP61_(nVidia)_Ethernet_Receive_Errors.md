---
title: "MCP61 (nVidia) Ethernet Receive Errors"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by mikecrowe on 2008-12-04
Hi folks,

I can't tell if this just happened or what, but suddenly I have 1 machine that is dog slow from the network.  In researching, I found that the ethernet is having lots of errors:

> ifconfig:
RX packets:1532532 errors:258062 dropped:0 overruns:0 frame:177885


Running:> Ubuntu 7.10
Linux hpserver 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

dmesg | grep eth0 gives:> [   30.907001] eth0: forcedeth.c: subsystem: 0103c:2a58 bound to 0000:00:07.0
[   44.673752] bridge-eth0: enabling the bridge
[   44.673870] bridge-eth0: up
[   44.673968] bridge-eth0: already up
[   44.673971] bridge-eth0: attached
[   45.324489] eth0: no IPv6 routers present
[   49.310214] device eth0 entered promiscuous mode
[   49.310221] audit(1228254050.021:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   49.310223] bridge-eth0: enabled promiscuous mode


lspci:> 00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 2a58
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

If I do an iperf test, I get these results:
> [  3]  0.0-10.0 sec  16.2 MBytes  13.6 Mbits/sec

A machine right beside it gives:> [  3]  0.0-10.0 sec    101 MBytes  84.4 Mbits/sec

I've searched ad-nauseum here, internet, nvidia, etc, but can't figure out where to turn.  Can anybody point me to my next step?

---

### Post by IQRules on 2008-12-04
Try 'sudo modprobe forcedeth' and check with 'sudo dmesg'

---

