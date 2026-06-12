---
title: "Intel Pro MT 1000 network card not recognised"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by kerm1t on 2010-04-21
Hi all,

Firstly, apologies if this should be in the Hardware forum instead.

I'm having trouble getting Jaunty to recognise one of my network cards, an Intel MT 1000 Dual Port.

The machine has an on-board network card too, and during installation Ubuntu detected both. It asked me which to use by default, I chose the on-board one.

But now that installation is complete, and I'm logged in, there's no sign of the Intel card: I've tried dmesg, lspci and lshw - they just report the on-board card. Since the installer was able to find it, I'm confident it's not faulty hardware.

I'm guessing e1000 or eepro would be the correct driver, and i've tried modprobing these. 

Any help please?

---

