---
title: "BlackMagic Decklink SDI to display desktop?"
date: 2012-04-28
forum: Multimedia Software
---

### Post by mnelson01 on 2012-04-28
I have an interesting problem I hope someone here might be able to help  me with.  I have a standard Intel box running Ubuntu 11.10.  It contains  an nVidia GeForce 7300 LE card and a Blackmagic Design DeckLink SDI  card (for professional video monitoring situations).

What I need to figure out how to do is have the standard Ubuntu desktop mirrored on both cards.  

Nvidia Geforce 7300 LE
ID 0
Bus: pci@0000:01:00.0

03:00.0 multimedia video controller: Blackmagic Design Device a11b

drivers currently in use: 
xorg:nvidia_173
kmod:blackmagic

I'm a novice at Linux hardware hacking, so please be gentle.

---

### Post by mnelson01 on 2012-04-28
Still working on this issue, and I'm fairly certain I need the correct xorg.conf entries to make it work.  The SDI card is to carry both a video and audio signal.  Here is some more information that I believe is relevant:

result of "sudo lshw -C video"
> *-display
    description: VGA compatible controller
    product: G72 [geforce 7300 LE]
    vendor: nVidia Corporation
    physical id: 0
    bus info: pci@0000:01:00.0
    version: a1
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
    configuration: driver=nvidia latency=0
    resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:de000000-deffffff memory:dfe00000-dfe1ffffresult of "sudo lshw -C multimedia"
> *-multimedia
    description: Audio device
    product: 82801H (ICH8 Family) HD Audio Controller
    vendor: Intel Corporation
    physical id: 1b
    bus info: pci@0000:00:1b.0
    version: 02
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: driver=HDA Intel latency=0
    resources: irq:44 memory:dffdc000-dffdffff
*-multimedia
    description: Multimedia video controller
    product: Blackmagic Design
    vendor: Blackmagic Design
    physical id: 0
    bus info: pci@0000:03:00.0
    version: 00
    width: 64 bits
    clock: 33 MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: driver=blackmagic_driver latency=0
    resources: irq:16 memory:dcd00000-dcdfffff memory:dce00000-dcefffff 

---

### Post by mnelson01 on 2012-04-29
I'm still chasing down this rabbit hole.  Is it possible there are things I need to change in grub to make the devices/drivers start correctly?

---

### Post by mnelson01 on 2012-05-02
Upgraded to 12.04 and actually using the nouveau driver instead of the nVidia.  that's acting better than before.  But I still can't come up with the right combination to put the desktop video and audio out the Multimedia card.  the resources and descriptions from lshw are the same as before.

---

### Post by dreh on 2012-06-02
You found a solution for the decklink card ? I'm interested in pbuying one.

---

