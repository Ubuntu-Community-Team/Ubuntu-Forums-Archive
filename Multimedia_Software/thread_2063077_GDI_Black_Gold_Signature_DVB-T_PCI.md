---
title: "GDI Black Gold Signature DVB-T PCI"
date: 2012-09-26
forum: Multimedia Software
---

### Post by schneil on 2012-09-26
Hi all

I've just acquired an old BlackGold signature card.
I've put it in my ubuntu box and I can't get it to work.

There was a message in dmesg about setting the card type manually (see below), so I have manually set it to 2 (GDI /black gold)
There sees to be no more errors on reboot, but I have no DVB device.

Is this card not ubuntu compatible?

(old dmesg output, before I set card type manually)



1.935571] cx88[0]: Your board isn't known (yet) to the driver.  You can
[    1.935573] cx88[0]: try to pick one of the existing card configs via
[    1.935574] cx88[0]: card=<n> insmod option.  Updating to the latest
[    1.935575] cx88[0]: version might help as well.
[    1.936574] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[    1.936890] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[    1.937089] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[    1.937328] cx88[0]:    card=2 -> GDI Black Gold

---

### Post by schneil on 2012-09-26
lspci

05:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

dmesg

[   22.823816] cx88[0]: GDI: tuner=unknown
[   22.826075] cx88[0]/0: found at 0000:05:02.0, rev: 5, irq: 18, latency: 64, mmio: 0xfc000000
[   22.826273] cx88[0]/0: registered device video0 [v4l2]
[   22.826335] cx88[0]/0: registered device vbi0

---

