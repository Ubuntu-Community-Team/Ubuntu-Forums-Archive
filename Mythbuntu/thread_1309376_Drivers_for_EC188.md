---
title: "Drivers for EC188?"
date: 2009-11-01
forum: Mythbuntu
---

### Post by mushroomdude on 2009-11-01
Hello,

I recently bought a cheap PCI DVB-T -tuner for a multimedia PC. Apparently it doesnt work (in Linux) as Mythbuntu doesnt even recognize it.

The card has an (E3C) EC188 -chip and lspci gives the following line for the card:
04:05.5 Multimedia video controller: Device 1a2d:1768

I did some googling and found nothing. 

I know that Antti Palosaari has made drivers for EC168 (the USB version). Would it be hard for someone to make drivers to EC188 using the EC168 drivers as a base? I have absolute no knowledge on Linux drivers :/ .

Here is some information about the EC168 drivers: [https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942](https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942)

I can provide more information about the card if wanted.

---

### Post by Eldis on 2009-12-29
Just bought one of these also plugged in and it's as I feared. Not recognized by mythbuntu 9.10 and even worse this is the only thread I've found about the device.

lspci -v

```
05:02.0 Multimedia video controller: Device 1a2d:1768
        Subsystem: Device 1801:0101
        Flags: bus master, slow devsel, latency 64, IRQ 14
        Memory at feaff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [78] Power Management version 3
```

Any help would be appreciated. I'll keep it for a while and return it in a week or so if I can't find any hope for getting it working.

---

### Post by rafael_alcantara_perez on 2010-02-19
I also bought that cheap PCI DVB-T tuner (because of being able to convert it to a low profile card). The card is a LifeView LV32T. Are there any advances on its support in the kernel?

Does anybody have technical information about that card, or at least about the EC188 chip? Maybe some people with more programming skills can use that to make a driver for the card.

---

