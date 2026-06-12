---
title: "Lost audio"
date: 2011-07-25
forum: Multimedia Software
---

### Post by williepabon on 2011-07-25
After the installation of a new video card (NVIDIA GeForce GT240), the  system failed to detect the sound card (Creative Audigy card). The  hardware doesn't show on the Sound preferences. This was working  perfectly before I substituted the old video card that failed. What do I  have to do for Ubuntu to recognize the card again? Thanks for the help. Following the hardware info I get from the system.

I ran lshw and for the Audigy card I get:
   *-multimedia UNCLAIMED
                   description: Multimedia audio controller
                   product: SB Audigy
                   vendor: Creative Labs
                   physical id: d
                   bus info: pci@0000:03:0d.0
                   version: 04
                   width: 32 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list
                   configuration: latency=64 maxlatency=20 mingnt=2
                   resources: ioport:dc80(size=64)
              *-input
                   description: Input device controller
                   product: SB Audigy Game Port
                   vendor: Creative Labs
                   physical id: d.1
                   bus info: pci@0000:03:0d.1
                   version: 04
                   width: 32 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list
                   configuration: driver=Emu10k1_gameport latency=64
                   resources: irq:0 ioport:dc78(size=8)
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: SB Audigy FireWire Port
                   vendor: Creative Labs
                   physical id: d.2
                   bus info: pci@0000:03:0d.2
                   version: 04
                   width: 32 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list
                   configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                   resources: irq:50 memory:dfecb800-dfecbfff memory:dfecc000-dfecffff
 Also found that the video card installed had audio capabilities or something!
            *-display
                description: VGA compatible controller
                product: GT215 [GeForce GT 240]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:d0000000-d1ffffff(prefetchable) ioport:cc80(size=128) memory:dfc00000-dfc7ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:dfbfc000-dfbfffff
 But it doesn't show as part of the hardware on the sound preferences dialog.
Hope this additional information help to solve this problem. Thanks.
wp

---

### Post by williepabon on 2011-07-26
Hi!
The workaround suggested by Anish Asoka on alsa-driver bug report #662299 solved my problem. Go to: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662299](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662299)
 for details. Thanks.
wp

---

### Post by williepabon on 2011-07-26
I take it back! the workaround above only worked once on my machine. The  next time I did boot up the audio was gone again. Tried to repeat the  steps, but they don't work now. Pleeeaase help!
wp

---

### Post by lkjoel on 2011-07-26
Try Sound Troubleshooting in my signature.

---

