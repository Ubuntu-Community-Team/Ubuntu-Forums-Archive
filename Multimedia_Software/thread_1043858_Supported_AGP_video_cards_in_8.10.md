---
title: "Supported AGP video cards in 8.10"
date: 2009-01-18
forum: Multimedia Software
---

### Post by awg1011 on 2009-01-18
After upgrading to Xununtu 8.10, my PCI FX 5200 video card will only work in low graphics mode and I haven't been able to get any nvidia drivers to work. After searching the forums here and trying several things posted here I came across a few posts saying that Nvidia doesn't support the FX 5200 in Ubuntu 8.10. So now I guess I'm looking for a new vid card, gives me a chance to go from PCI to AGP.;) 

What AGP cards or chipsets are well supported under 8.10? Nvidia or ATI, which is better supported? 

Basic specs:
ASUS P4S800D-X socket 478 MB
2.5 Ghz P4 (no HT)
1GB DDR RAM
PNY GeForce FX 5200 PCI 256MB RAM

BTW, I don't need anything fancy

---

### Post by RJARRRPCGP on 2009-01-18
The FX5200 should be fine. Anything >GeForce 4 Ti should be supported.

---

### Post by awg1011 on 2009-01-21
> **RJARRRPCGP said:**
> The FX5200 should be fine. Anything >GeForce 4 Ti should be supported.

As I mentioned before, while searching the forums trying to find a fix for my video, I had seen several posts that said the FX 5200 was no longer supported but after your reply I thought I would give it another shot. This time I did a fresh install of Xubuntu 8.10 then installed the video driver with no problems. 

When I first went to 8.10, I had used the update manager in 8.04, video was working fine until the update.

Thanks RJARRRPCGP

---

### Post by HunterK on 2009-01-21
I can vouch for my GeForce 6800GT.  It works fine in 8.10, even with the new 180 drivers.

---

### Post by sandy8925 on 2009-01-21
PCI to AGP ? wow. I'm trying to go from AGP to PCI...-E

---

### Post by sandy8925 on 2009-01-21
I have a 6600 GT AGP card which works fine on 8.10 without any problems. I'm using driver version 177.

---

### Post by awg1011 on 2009-01-21
> **sandy8925 said:**
> PCI to AGP ? wow. I'm trying to go from AGP to PCI...-E

I know, I know. I do have another box with 4 pci-e slots (SLI ready), dual core 64 bit AMD, and oodles of RAM, running XP. I wouldn't mind replacing my Linux motherboard with something similar but I need to spend my money on other things at the moment. So I'm stuck with pci video for now....Maybe I'll come across a cheap used AGP card.

---

### Post by awg1011 on 2009-01-21
> **HunterK said:**
> I can vouch for my GeForce 6800GT.  It works fine in 8.10, even with the new 180 drivers.

The FX 5200's latest driver is 173, the 177 and 180 drivers don't list FX 5200.

I don't understand why it would work fine in 8.04 then not work after updating to 8.10, but works fine after a fresh 8.10 install..... I'm not going to loose sleep over it, it's working now.

---

### Post by Shazaam on 2009-01-21
I have two AGP cards that work with 8.10= a PNY GeForce 6600GT and a BFG 7800GS.

---

### Post by ppc_guy on 2009-01-21
open a term, or ctrl to whatever virt you want to use.

sudo su
apt-get install nvidia-settings

Run that from the command line, tweak to tell you like it, save it and there you are.

Nathan
--------------------------------------------------------------
When you are Sierra-Oscar-Lima. I am Hotel-Tango-Hotel.
--------------------------------------------------------------

---

