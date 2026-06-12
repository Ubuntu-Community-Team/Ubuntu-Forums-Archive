---
title: "3c59x not working in dapper with Asus K7M board"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by vazzeroni on 2006-06-20
Hi guys,
I recently upgraded a bunch of Athlon 550's from warty to dapper, after upgrading their RAM from 128MB to 512MB each. They run it quite well except that the 3c59x module doesn't work in 2.6.15-x. It works fine with the warty kernel (2.6.10). It's one of the stranger things I've ever seen... I get the following in the kernel messages, like I would expect:

Jun 20 18:21:49 localhost kernel: [  251.014123] PCI: Found IRQ 5 for
device 0000:00:0e.0
Jun 20 18:21:49 localhost kernel: [  251.014922] 3c59x: Donald Becker
and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
Jun 20 18:21:49 localhost kernel: [  251.015626] 0000:00:0e.0: 3Com PCI
3c905B Cyclone 100baseTx at e0a44f80. Vers LK1.1.19

The card is indeed at IRQ5, however, when I check /proc/interrupts, it doesn't show up, and "ifconfig eth0" gets me "no such device" or something similar. I tried booting with pci=routeirq as well as acpi=off, but it didn't help. I also tried upgrading the BIOS, which didn't help either. In addition, I tried making the card move IRQ's by shutting off certain ones in the BIOS, and trying things like changing the "ACPI aware OS" and "PnP aware OS" settings in BIOS, all to no avail. The oddest thing of all is that one of these machines, identical to the rest of them, works fine, and the kernel messages look similar... here's the kernel messages for the one that works:

[17179598.652000] **** SET: Misaligned resource pointer: da897b22 Type 07 Len 0
[17179598.652000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179598.652000] PCI: setting IRQ 10 as level-triggered
[17179598.652000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179598.652000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179598.652000] 0000:00:0e.0: 3Com PCI 3c905B Cyclone 100baseTx at e099cf80. Vers LK1.1.19

Does anybody have any clues? If not, I think I'll submit a kernel bug report.

-Josiah

---

### Post by vazzeroni on 2006-06-20
More info... the adaptor that's working works in all of the computers, so there's something different about it, though I don't know what. lspci -v says the EXACT same thing about both of them:

0000:00:0e.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (r ev 30)
        Subsystem: 3Com Corporation 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at c400 [size=128]
        Memory at efffff80 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at effc0000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 1

Again, if I swap back to an older kernel, they both work fine.

Here's a clue:  I get:
ACPI: PCI Interrupt for device 0000:00:0e.0 disabled

in the kernel messages when the card doesn't work. What would cause ACPI to disable the interrupt? Why, then, does turning acpi off at boot-time not fix it?

---

### Post by vazzeroni on 2006-06-20
More clues... it does it with other cards as well... an ne2k-pci that I've got will do a similar thing: it'll initialize correctly, say what IRQ it's at, and then not show up in /proc/interrupts nor work when I say "ifconfig eth0" even though it said "eth0: RTL8029" etc in the kernel messages, and the same thing happens if I try a 3c590 I've got as well... initializes fine, says it's there, lists the IRQ and the ioport and everything, then doesn't show up and doesn't work - acts like the module was never inserted at all.... I think this is a kernel bug.

---

### Post by vazzeroni on 2006-06-20
Similar things happen with an ne2k-pci and a 3c590 I've got... modprobe looks fine, it says eth0: and the irq and the iobase and everything, with no error messages after that, and then just doesn't work - doesn't show up in /proc/interrupts (though, oddly enough, they do show up in /proc/ioports) and doesn't work when I try to use ifconfig... I think this is a kernel bug.

---

### Post by vazzeroni on 2006-06-21
I have reported this as a bug: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50597](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50597)

...but I shouldn't have, and will delete the bug. Boy, do I feel dumb. /etc/iftab was the problem - I had imaged the machines all to each other, and the MAC of the one card that worked was in /etc/iftab of all of them. Breezy, apparently, doesn't actually care about this file. Sigh. Live and learn. (I'd never heard of /etc/iftab before... huh)

---

