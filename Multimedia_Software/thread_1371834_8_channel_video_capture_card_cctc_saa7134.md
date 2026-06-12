---
title: "8 channel video capture card cctc saa7134"
date: 2010-01-03
forum: Multimedia Software
---

### Post by rompstar on 2010-01-03
I bought a 8 channel video cctv capture card, it is a PCI card.  when I type: sudo lshw, here are all the channels that I see.  It seems to be using the saa7134 driver.  I have cameras hooked up to /dev/video0 and 1, but I see no video.

I tried different software and I tried to setup zoneminder, which I did, but no video shows up.  Anyone know how to fix this ?

Running Ubuntu 8.10 


   *-multimedia:0
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: 8
                   bus info: pci@0000:06:08.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:16 memory:f8500000-f85003ff
              *-multimedia:1
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: 9
                   bus info: pci@0000:06:09.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:18 memory:f8500400-f85007ff
              *-multimedia:2
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: a
                   bus info: pci@0000:06:0a.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:21 memory:f8500800-f8500bff
              *-multimedia:3
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: b
                   bus info: pci@0000:06:0b.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:22 memory:f8500c00-f8500fff
              *-multimedia:4
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: c
                   bus info: pci@0000:06:0c.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:16 memory:f8501000-f85013ff
              *-multimedia:5
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: d
                   bus info: pci@0000:06:0d.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:18 memory:f8501400-f85017ff
              *-multimedia:6
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: e
                   bus info: pci@0000:06:0e.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:21 memory:f8501800-f8501bff
              *-multimedia:7
                   description: Multimedia controller
                   product: SAA7130 Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: f
                   bus info: pci@0000:06:0f.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=66 maxlatency=38 mingnt=15
                   resources: irq:22 memory:f8501c00-f8501fff

---

