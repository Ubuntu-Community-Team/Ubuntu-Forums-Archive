---
title: "padsp -  SNDDMA_Init: Sorry, but your soundcard doesn't support trigger or mmap"
date: 2010-08-21
forum: Multimedia Software
---

### Post by interzoneuk on 2010-08-21
Hi.

I am trying to get round the age old issue of multiple sound outputs when using an OSS app.

I though padsp would do it.

But when I try to use it (on this example with digital paint 2)

morgan@morgan-desktop:~/games/paintball2$ padsp ./paintball2 
> 
Paintball 2 -- Version 2.0
execing configs/config.cfg
Console initialized.

------- sound initialization -------
LoadLibrary("./snd_oss.so")
SNDDMA_Init: Sorry, but your soundcard doesn't support trigger or mmap. (00005100)

- I get no sound...

Is it a hardware thing - i.e my soundcard lacks something?  (I know it lacks the ability to record its own output without snd-aloop)

Here is my soundcard info:-


> morgan@morgan-desktop:~/games/paintball2$ sudo lshw  -class sound
  *-multimedia            
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: 6.1
       bus info: pci@0000:00:06.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fc100000-fc103fff


Anyone know if I can do something in order to get it to work ?

---

