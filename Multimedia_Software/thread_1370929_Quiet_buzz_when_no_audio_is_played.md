---
title: "Quiet buzz when no audio is played"
date: 2010-01-02
forum: Multimedia Software
---

### Post by sharq1 on 2010-01-02
Hi,
when i watch some movies or listen to music, then everything is ok, when there is no sounds (for example between tracks), then there are no sounds. But when i don't listen to anything, then after about 10 seconds i can hear buzz (until i play some audio again), which can be quite annoying when amplified.

This is the output of lshw
> *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:20 memory:f8400000-f8403fff


---

### Post by HappyFeet on 2010-01-02
Is your computer located near a source of interference such as large speakers, or electrical appliance? Your power supply could also be the reason.

---

### Post by sharq1 on 2010-01-03
There are large speakers 3 meters away, there is also amplifier half meter away. But it didn't happen in Jaunty, only in Karmic.

---

### Post by sharq1 on 2010-01-04
You were right, my power supply is the reason. If i plug it off then it's ok. But why does this sound come after about 10 seconds, and it is ok, when some sound is beeing played?

---

