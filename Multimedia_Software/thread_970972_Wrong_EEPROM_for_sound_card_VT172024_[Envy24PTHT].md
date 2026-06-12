---
title: "Wrong EEPROM for sound card VT1720/24 [Envy24PT/HT]"
date: 2008-11-04
forum: Multimedia Software
---

### Post by ericml on 2008-11-04
I recently installed Ibex and everything has been going great but I can't get any sound. After searching for some time I think I have found the solution [here]("http://www.lbtechservices.com/blog/2005/04/09/sn25p-ice1724/"). So I was wondering if there is some way to rebuild just that module and get it to work or do I need to compile a custom kernel?

---

### Post by cariboo on 2008-11-04
That is a 3 year old solution things have changed quite a bit since 2005. Could you paste the output of:

```
sudo lshw -C multmedia
```

in your next post. The above command must be done in a Applications-->Accessories-->Terminal.

Jim

---

### Post by ericml on 2008-11-04
ok

```
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
```

---

### Post by cabez0n on 2009-12-18
Mine says:

  *-multimedia            
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 1
       bus info: pci@0000:0a:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1724 latency=32
       resources: irq:16 ioport:4080(size=32) ioport:4000(size=128)

---

