---
title: "Dapper cardbus not supported"
date: 2006-03-17
forum: Networking &amp; Wireless
---

### Post by hapee on 2006-03-17
The hardware forum didn't answer so I try again here because I need some help on this.

I installed dapper on my laptop (a topline amicus) and have problems installing my wifi card (which was working on breezy without problem).

I tried with ndiswrapper and with several bootoptions but dmesg keeps on saying :

cs: pcmcia_socket0: cardbus are not supported

is this Dapper or the kernel?

lspci says:

0000:00:0a.0 Cardbus bridge: 02 Micro, Ind 0Z6812 Cardbus Controller (rev 05)

nsdiswrapper -l says:

installed ndis drivers:
rt2500 driver present

So I am stuck, any suggestion?

Thanks,

Hapee

---

### Post by hapee on 2006-03-17
well thanks for your help, because I got no answer so I kept on looking myself, as I have done before, I checked the dmesg again and it brought me to this:

Yenta no PCI IRQ cardbus support disabled for this socket

And that lead me some additional boot options in the menu.lst of grub, I am booting now with:

acpi=on acpi=force lapic pci=usepirqmask pci=biosirq

and my card is detected and after filling in the right parameters I have a wireless connection again.

Thanks but no thanks.

---

