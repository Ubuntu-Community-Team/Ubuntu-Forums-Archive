---
title: "dwl-650 rev.P"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by fgs on 2006-06-23
I need help. Have searched and searched and can't figure out how to get this card to work with laptop. Can't find chipset on d-link dwl-650 card and if I knew I still would not know what to do. Brand new to Ubuntu, used a few dos commands 25 or so years ago. Maybe I just need to buy a different card but don't even know how to do that. Frustrated in San Antonio, but like Ubuntu so far. Internet access is with d-link card and cat 5 cable, no problem just plug card in and out and it works perfect.
 
*-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:14100000-14100fff irq:9
           *-network
                description: DWL-650 Wireless PC Card RevP
                product: ISL37101P-10
                vendor: D-Link
                physical id: 0
                version: A3
                slot: Socket 0
fgs@fgs-laptop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

---

### Post by tturrisi on 2006-06-23
That card has an Intersil Prism3 chipset & *should*  work because the kernel has support for prism devices...however from what I have read so far it appears that card is tough to get working.  Better off going out & grabbing a dlink 630 or 650 (30-40 bucks), they have the atheros chipset & work almost flawlessly out of the box using madwifi drivers which come w/ ubuntu.

---

