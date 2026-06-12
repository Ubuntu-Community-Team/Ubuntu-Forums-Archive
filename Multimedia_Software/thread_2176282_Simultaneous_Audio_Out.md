---
title: "Simultaneous Audio Out"
date: 2013-09-23
forum: Multimedia Software
---

### Post by gus_zernial on 2013-09-23
I have an AMD system with Sabertooth 990FX motherboard, running Kubuntu 12.04 and KDE 4.11.1. Chipset is AMD990FX/SB950, and audio spec is Realtek ALC892 8-channel Hi Def audio. I have audio outputs connected to the analog out ports, and digital coax out to a mini-card connected to  the SPDIF-Out connector on the motherboard. Output of lshw for multimedia is below.

Audio configuration is thru System Settings -> Multimedia -> Audio and Video Settings  and accordingly thru Phonon multimedia framework. I can get audio out either thru Analog Stereo jacks or Digital Coax (designated Digital Stereo IEC958) jack, but I can't get output thru both simultaneously, and I can't find anything in Audio and Video Settings to do so. It must be possible, as this is a Windows/Linux dual-boot system, and I get simultaneous audio output with Windows.

Can someone tell me how to configure my Kubuntu system for simultaneous audio output?

Thx, Gus

*-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fe600000-fe603fff

---

