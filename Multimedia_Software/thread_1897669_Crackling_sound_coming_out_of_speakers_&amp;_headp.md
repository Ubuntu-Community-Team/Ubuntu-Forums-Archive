---
title: "Crackling sound coming out of speakers &amp; headphones"
date: 2011-12-19
forum: Multimedia Software
---

### Post by NiteiaTt on 2011-12-19
I need help with a little problem I'm experiencing with mi Ubuntu Maverick installation.
I'm going through a little problem with my audio card. Every time I use the speakers or headphones (watching videos, listening to music) there's a annoying crackling-like sound coming out.
And it gets interesting. I use Blender a lot, and when I render, the music that's currently playing gets "fast-forwarded (if that even exists [English is not my native language])", and the crackling continues.

With my previous installation, Ubuntu Lucid, that didn't happen.

Please, I need help.
I can't work without music.

My system:
Processor: AMD A8-3510MX APU (Quad -> 1.8)
Graphics Card: ATI Radeon 6620G 
OS: Ubuntu Maverick Meerkat, Kernel 2.6.35-31-generic
Audio card: uuuh... I got confused, so I'm pasting an output from the terminal:
> francisco@francisco-305V4A-305V5A:~$ sudo lshw -C multimedia
[sudo] password for francisco: 
  *-multimedia:0          
       description: Audio device
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:feb44000-feb47fff
  *-multimedia:1
       description: Audio device
       product: Hudson Azalia Controller
       vendor: Advanced Micro Devices [AMD]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32
       resources: irq:16 memory:feb40000-feb43fff
I don't know if that's helpful somehow :S

Any help is truly appreciated.

---

### Post by MoreOrLess on 2011-12-20
Please post alsa info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by NiteiaTt on 2011-12-20
> **MoreOrLess said:**
> Please post alsa info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=5c770940fdd5995d1a94a412a0b858f509e1fad7](http://www.alsa-project.org/db/?f=5c770940fdd5995d1a94a412a0b858f509e1fad7)

thanks =D

---

