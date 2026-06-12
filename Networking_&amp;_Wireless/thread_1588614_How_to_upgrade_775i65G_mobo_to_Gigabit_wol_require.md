---
title: "How to upgrade 775i65G mobo to Gigabit? wol required!"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by frafu on 2010-10-05
Hi, 

I have a server with a 775i65G motherboard running Ubuntu Lucid sever edition. It is currently connected to the network by using the onboard fast ethernet interface. 

I would like to upgrade the server to Gigabit, but am not sure how to proceed, because I have to keep the wol working. 

If I insert an Intel PWLA8391GT card into it and disable to onboard LAN in the BIOS, will wol continue to work? Moreover, do I have to connect some cable from a header on the card to a header of the motherboard for the wol to work? (Please, when answering, take also the motherboard into account.) 

Thanks in advance for any help.

Francesco

PS: Do not hesitate to also suggest an different procedure or NIC if appropriate.

---

### Post by FullMetalManiac on 2010-10-05
Ummm, what's "wol"?

---

### Post by frafu on 2010-10-05
> **FullMetalManiac said:**
> Ummm, what's "wol"?

wol: wake-on-lan

It allows to boot the server by sending it a command from another computer connected to the network.

---

### Post by frafu on 2010-12-15
Hello, 

For those that might be interested: 

I installed an INTEL PRO/1000 GT Ethernet PCI Adapter in the computer and by using the BIOS, I disabled the ethernet port that is integrated on the motherboard. There were no wires necessary between the ethernet adapter and the motherboard; I only had to put the adapter into a pci slot. 

The board is supported by Ubuntu lucid out of the box and wol is also working. 

Cheers, 

Francesco.

---

### Post by mjitkop on 2011-01-20
Thank you for this thread. I was just looking at this gigabit card on Newegg and was wondering if it would work with Ubuntu. That answers my question. :popcorn:

---

### Post by mjitkop on 2011-01-20
*** Deleted *** (duplicate)

---

### Post by frafu on 2011-01-20
I am glad that I could help.  :-)

---

