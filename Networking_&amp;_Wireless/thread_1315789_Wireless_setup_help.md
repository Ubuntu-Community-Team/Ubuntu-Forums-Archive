---
title: "Wireless setup help"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by alms66 on 2009-11-05
I just bought a new laptop (Toshiba Satellite P505-S8980) which you can see here:
[Toshiba Laptop]("http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=452687")
I installed Ubuntu 9.10 and now I'd like to get the wireless working.  Is the Ubuntu ndiswrapper doc the best way to get it up and running?

---

### Post by Iowan on 2009-11-05
Apparently, a lot of cards that required **ndiswrapper** now have drivers "built in". What chipset does your new Toshiba use?

---

### Post by alms66 on 2009-11-05
Well, I just plugged in a cable and still nothing.  I have no wired or wireless network connections.

lspci gives me:

```

07:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```

I should also mention I'm running 64-bit...

---

### Post by Iowan on 2009-11-05
Guess I should mention that I'm not (yet) running Karmic,,,
Although it should be similar to **lspci**, what are results of **lshw -C network**?

---

### Post by alms66 on 2009-11-05
```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list
       configuration: latency=0
       resources: memory:b6000000-b603ffff ioport:2000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b6100000-b6103fff

```

---

### Post by alms66 on 2009-11-06
I tried to come back last night and add this little tid-bit, but had trouble with the forum not loading...

Anyhow, so the 'Unclaimed' part means that there no linux driver for these two devices.  I've downloaded the windows drivers and put them on the laptop to proceed with ndiswrapper.  Is there a how-to on using that which might be considered the "standard" or will any old one do?

This would seem to be the "standard", correct?

That will, hopefully, fix the wireless.  Is there anything I can do about the wired device?

---

