---
title: "Hiss/Static"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by kayn_lyght on 2007-04-24
Hello, I'm having audio problems consisting of hissing/static coming from the speakers.  I know it has to do with Ubuntu but can only isolate to the audio device drivers.  I can play music just fine but the hiss/static still persist throughout.  I am unsure what I need to do.  Any & all detailed instructions will be greatly appreciated.

PS
When I lshw this is the information I received.

 *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:80000000-80003fff irq:19

---

### Post by Steve H on 2007-04-25
This might sound a bit stupid, but have you tried turning down some of the volume levels in the ALSA mixer?

Sometimes, I have found that having the PCM or WAVE levels too high on the mixer can cause hissing on my speakers. To get to the ALSA mixer just double click on the speaker icon on your taskbar, that should  bring up the mixer for you.

Worth a try. Hope it helps.

---

### Post by kayn_lyght on 2007-04-28
Hello Steve & thanks for the reply.  To answer you're question, yes I've adjusted the volume controls & it does negate the audible hiss/static at the halfway point.  However some of the audio files I have require high volume thus comes in the problem.  I'm looking to find a way to rid the problem completely not just mitigate it.  I'm still tussling with said issue & if it proves to be unsolvable then I'll have to live with a constant lowered volume.  Again I thank you for replying Steve & if you have any other ideas in addition to the great one you gave I'd be very appreciative to seeing them.

---

