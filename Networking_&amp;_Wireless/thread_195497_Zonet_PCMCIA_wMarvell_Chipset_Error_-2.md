---
title: "Zonet PCMCIA w/Marvell Chipset: Error -2?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by newuserAK on 2006-06-12
I am pretty new to ubuntu (got breezy about a month ago, downloaded kubuntu 6.06 when it came out).  I am running it on a 4 year old toshiba satellite 1105 notebook, and my problem deals with installing a PCMCIA wifi card.

I bought a zonet card from newegg at the recomendation of somebody on the ubuntu IRC, and sure enough, there is a driver built-in to the kernel for the marvell 8k chipset.  When i run "tail -f /var/log/messages" and plug in the card, i get this message:

Jun 12 17:26:11 mary-laptop kernel: [4296662.269000] pccard: CardBus card inserted into slot 1
Jun 12 17:26:11 mary-laptop kernel: [4296662.269000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
Jun 12 17:26:11 mary-laptop kernel: [4296662.269000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Jun 12 17:26:12 mary-laptop kernel: [4296663.284000] ACPI: PCI interrupt for device 0000:07:00.0 disabled
Jun 12 17:26:12 mary-laptop kernel: [4296663.284000] mrv8k: probe of 0000:07:00.0 failed with error -2


i am not particularly experienced with the inner workings of the kernel, but from what i can tell, it sees the card, has the router (mrv8k), tries to activate it, and somehow fails.  Am i misunderstanding this message and/or is there some way to fix this?  Thanks for any help.

---

