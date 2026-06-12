---
title: "Wireless Card No Longer Working on Dell Inspiron Laptop"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by kidcharles on 2009-01-14
Hi all, I've had a pre-installled Ubuntu Dell Inspiron laptop for a little over a year. The wireless worked fine until recently, but now my wireless card does not show up under the "Connections" tab in "Network Settings". The card does show up under 'lspci':

```

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

It also shows up in the output from 'lshw -C network':
```

  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:ecfff000-ecffffff irq:16

```

I'm running 7.04, but I tried doing a LiveCD session with an 8.04 disk and it didn't show up under the "Connections" tab in that either. Could it be a hardware problem even though it shows up under lspci and lshw? Any thoughts? Thanks.

---

### Post by utnubuuser on 2009-01-15
Hi -- Is it enabled in under System>>Administration>>Hardware Drivers?

---

### Post by kidcharles on 2009-01-15
> **utnubuuser said:**
> Hi -- Is it enabled in under System>>Administration>>Hardware Drivers?

Thanks for responding. If you mean "System>>Administration>>Restricted Drivers Manager", yes it is. I'm using 7.04, maybe there is an option now for "Hardware Drivers" instead? It was enabled before and after the wireless stopped working.

---

