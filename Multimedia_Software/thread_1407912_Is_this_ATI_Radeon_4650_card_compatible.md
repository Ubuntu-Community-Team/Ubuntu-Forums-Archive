---
title: "Is this ATI Radeon 4650 card compatible?"
date: 2010-02-15
forum: Multimedia Software
---

### Post by m3rc on 2010-02-15
I'm looking to buy a new video card. I checked the compatibility with Karmic 9.10 here [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti) and it looks compatible software-wise. Reading up on video cards, I'm confused with PCI Express vs. AGP. 

Is this card compatible with my system?

Here's the relevant info from lshw:

```

*-display UNCLAIMED
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0
          resources: memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable)

```Here's the specs on the [Radeon 4650:]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814131180")

Model                 Brand       POWERCOLOR                 
Model       AX4650 512MD2-LHV2 
                Form Factor       Low Profile Ready                 Low Profile 
                Interface       PCI Express 2.0 x16 
Chipset Manufacturer       ATI                 GPU       Radeon HD 4650                 
Core Clock       600MHz 
                Stream Processors       320 Stream Processing Units                 Memory                 Effective 
Memory Clock       800MHz                 
Memory Size       512MB 
                Memory Interface       64-bit                 
Memory Type       DDR2                 3D API                 
DirectX 10.1                 
Ports                 HDMI       1 x HDMI                 D-SUB       1 x D-SUB                 DVI       1 x DVI                 General                 RAMDAC       400 MHz                 
Max Resolution       2560 x 1600 
                CrossFireX Support       Yes                 Cooler       With Fan                 Dual-Link 
DVI Supported       Yes 
                HDCP Ready       Yes

---

### Post by Yellow Pasque on 2010-02-15
Yeah, it's compatible. nforce 410/430 boards are pci-e, so you don't have to worry about AGP.

---

### Post by m3rc on 2010-02-15
Great, thanks! I read up on AGP a little more and it sounds like it's an older technology anyway. Most motherboards after 2006 use PCI-E.

---

