---
title: "Help me get sound to work on my hp laptop"
date: 2009-11-09
forum: Multimedia Software
---

### Post by yellowstoned on 2009-11-09
Hey guys, struggling to get sound to work, walked trough the sticky and it did not work for me, I must be missing a step along the way somewhere
Linux detects the soundcard but it will not run and my mixer says 'dummy output'

when i type lspci-l I get among many other things the following

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Hewlett-Packard Company Device 30bf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

Anyone offer any advice on what to do next?

---

### Post by Ulysses361 on 2009-11-10
Please send us the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of laptop you are using.

---

### Post by Jyothi Sangam on 2009-11-10
Could you Take the sound System Testing?
 System->Adminitstration->System Testing->AudioTesting.


> **yellowstoned said:**
> Hey guys, struggling to get sound to work, walked trough the sticky and it did not work for me, I must be missing a step along the way somewhere
Linux detects the[CENTER][/CENTER] soundcard but it will not run and my mixer says 'dummy output'

when i type lspci-l I get among many other things the following

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Hewlett-Packard Company Device 30bf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

Anyone offer any advice on what to do next?

---

### Post by markbuntu on 2009-11-10
These problems can be very hardware specific so solutions can also be very hardware specific as you will see of you follow this link where a lot of laptops are listed including many hps:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

