---
title: "Stuck on 8.04 because of IRQ issues on 10.04"
date: 2013-02-27
forum: Mythbuntu
---

### Post by tabnett on 2013-02-27
Hi,

I'm running Mythbuntu 8.04 (mythtv 0.21) on an AM2 motherboard (ASUS M2NPV-MX). Mythbuntu 8.04 runs very reliably on this hardware, although I have to use 'noapic nolapic' boot parameters to prevent occasional boot hangs.

I have 10.04 on another partition because I've been trying to upgrade for years, but 10.04 on the same hardware gives me 'IRQ 5 nobody cared'. I use noapic nolapic as with 8.04. It's always IRQ 5 which seems to be video and ata. I've tried a few irq/pci boot parameters with no luck. Every few boots I get 'IRQ 5 nobody cared' and the system grinds almost to a halt.

Has anyone got any suggestions for ways to diagnose/fix this? Am I ever likely to get 10.04 or later running, or have I got to give up and get new hardware?

Thanks,
Tom

N.B. boot options tried (all with noapic nolapic):
pci=routeirq
pci=nomsi
pci=noacpi
irqpoll

---

