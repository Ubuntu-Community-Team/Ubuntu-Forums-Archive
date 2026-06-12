---
title: "Need help setting up alsa"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by Xecuter on 2007-06-11
I'm trying to set up alsa so that I can use my Echo Mia Midi sound card, but I need some help. 

I've been following [this guide.]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Mia-midi.&chip=Motorola+56361&module=mia")

But now when I restarted I had no sound, so I tryed installing the alsa packages from Synaptic, but I still have no sound.

1. What do I have to do to get sound back?

2. What do I need to do to make my Mia card work? I have to start all over again, so please help me from there. What to do?

---

### Post by Xecuter on 2007-06-12
Bump. At least help me get some sound!

lshw says:
> *-multimedia:1 UNCLAIMED
            description: Multimedia audio controller
            product: VT8233/A/8235/8237 AC97 Audio Controller
            vendor: VIA Technologies, Inc.
            physical id: 11.5
            bus info: pci@00:11.5
            version: 60
            width: 32 bits
            clock: 33MHz
            capabilities: cap_list
            configuration: latency=0
            resources: ioport:e000-e0ff irq:11

I've tried to reinstall alsa-base, alsa-utils and alsa-oss through Synaptic, but with no luck.

---

