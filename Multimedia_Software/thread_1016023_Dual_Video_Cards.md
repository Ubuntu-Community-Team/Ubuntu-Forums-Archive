---
title: "Dual Video Cards"
date: 2008-12-19
forum: Multimedia Software
---

### Post by jebathan on 2008-12-19
I just upgraded to Ubuntu 8.10 and I want to get dual monitors working with two different video cards. I've seen the tutorials on how to do this with dual head video cards, but not so much info on dual video cards.

Once I installed the PCI card it decided to only use that one, not the AGP card. When I run lshw -c display I get.
*-display UNCLAIMED
    description: VGA compatible controller
    product: Radeon RV200 QW [Radeon 7500]
    vendor: ATI Technologies Inc
    physical id: 0
    bus info: pci@0000:01:00.0
    version: 00
    width: 32 bits
    clock: 66MHz
    capabilities: cap_list
    configuration: latency=64 mingnt=8
*-display
    description: VGA compatible controller
    product: ViRGE/DX or /GX
    vendor: S3 Inc.
    physical id: 9
    bus info: pci@0000:02:09.0
    version: 01
    width: 32 bits
    clock: 33MHz
    configuration: driver=s3fb latency=64 maxlatency=255 mingnt=4 module=s3fb

Any sort of help would be very appreciated.

---

