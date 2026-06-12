---
title: "Low speaker output Haswell-ULT HD / 8 Series HD / PCH92HD91BXX"
date: 2015-04-26
forum: Multimedia Software
---

### Post by Krillo on 2015-04-26
Hi all

This laptop (HP Spectre 13 x2) of course came pre-installed with windows. After installing Ubuntu the output of the speakers are noticably quieter. Yesterday I happened to plug in my headphones and found that level to be a lot hotter. All sliders are at 100% in the Pulse audio controlpanel. If cranked up more, I just get distortion. So something is off, and there seems to be no way of adjusting it.
Iz bug, no? :-k

```
               
    description: Notebook
    product: HP Spectre 13 x2 PC (F9E35EA#UUW)
    vendor: Hewlett-Packard

        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:77 memory:b2510000-b2513fff


        *-multimedia:1
             description: Audio device
             product: 8 Series HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:62 memory:b2514000-b2517fff
```

---

### Post by Krillo on 2015-04-29
Not anyone with similar chipsets / probelm?

---

### Post by Rob Sayer on 2015-04-29
Pulseaudio is actually a layer on top of alsa.  Try alsamixer.  Here's a guide:

[https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)

---

### Post by Krillo on 2015-04-29
Thanks for the answer! The two controls that affect the speakers in alsamixer are "PCM" and "Master", in the Pulse audiomixer they are the same slider. If having both windows open you can see that the one slider named "Speakers" is affected by both the controls in alsamixer.

If speaking in general audio terms, there seems to be lacking a control for "the poweramp". Maybe I'm hallucinating, but I can't remeber audio being this low before. I could measure the actual SPL, installing windows and repeating the process but actually I'm reluctant to do that :-/

*Edit:*
I'm downloading some windows 7 live CD now. I didn't know it existed :o

---

