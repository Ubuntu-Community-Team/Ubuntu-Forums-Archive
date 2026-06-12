---
title: "No sound after recent updates 12.10"
date: 2013-02-20
forum: Multimedia Software
---

### Post by mckaymotoworks on 2013-02-20
I have a pretty bread and butter install of 12.10, I've some how lost sound with the recent updates or it's possible it could be after I installed QTractor last night. 

I went through the usual Terminal verification of the sound card on my Dell N5010:
[B]00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Dell Device 0447
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at fbd00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel[/B]

I do remember after the QTractor install, it did ask me about the audio I believe related to JACK. Forgive me, I've been away from Linux for a bit, so still working my head back around it.

I also attached a screenshot of the Sound menu, seems I remember another option related to the onboard Intel card?

---

### Post by mckaymotoworks on 2013-02-20
Odd, I shut the computer all the way down, removed battery and sound now works again.
Previously I just restarted, I guess something was hung during the update and not releasing the appropriate software components to communicate with the hardware.

---

