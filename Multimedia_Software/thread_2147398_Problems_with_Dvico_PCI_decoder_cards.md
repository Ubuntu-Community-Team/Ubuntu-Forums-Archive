---
title: "Problems with Dvico PCI decoder cards"
date: 2013-05-21
forum: Multimedia Software
---

### Post by lannetlinux on 2013-05-21
I was previously running Mythbuntu with the Ubuntu level 11.10 and a 3.0.? kernel (I think - could be 3.2.?).

My original DVB-T decoder card is DViCO FusionHDTV DVB-T DualDigital4 PCI (which has an IR socket just below the antenna socket.)

Now, that worked fine and I was able to use both USB chips on the card.

Necessity demanded that I replace the base computer (failing mobo) so I ordered a new 'puter (without disks) and also an additional decoder card as the new mobo had a spare PCIe x1 slot - DViCO Fusion Dual Express 2 HDTV Tuner PCI-E.  Using the disks out of the old 'puter I was able to get the system running and the original card worked fine, but the new tuner card wouldn't present the extra USB devices; the cx23885 PCI chip was found but the DiBComm decoders were missing as USB devices.

A bit of googling indicated that the newness of this card had been a problem back a couple of years, and as 11.10 was out of support I decided to progressively upgrade to 13.04 hoping that the lack of drivers had been resolved in the 3.8.0 kernel.

Not so, in fact the problem has worsened.  The old card is recognised and lsusb shows 2 Dvico USB devices, but now the primary device (frontend0) is not working and the logs are being flooded with "dvb-usb: bulk message failed: -110 (1/0)" about every 2 seconds.  Also, still, the situation has not changed about the new tuner card, lspci shows it to be present - "02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)", but still no USB devices.

In short, I am now down from 2 decoder channels to just 1 instead of lifting to 4 as I wanted.


HELPPPPPPPPPPPPPPPP...

---

