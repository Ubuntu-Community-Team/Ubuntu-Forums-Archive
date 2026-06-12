---
title: "Intel HDA ICH8 Drivers for Alsa"
date: 2009-06-25
forum: Multimedia Software
---

### Post by Solar Zenith on 2009-06-25
I recently installed ubuntu ( on a dell vostro 2510 laptop partitioned with Windows, and since that time, I have not been able to get any sound when in ubuntu (9.04 Jaunty Jackalope).  After going through the troubleshooting tutorial at: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting), I'm fairly sure but not positive that ALSA does not support my sound card.  Here is the card information:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02b5
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I also looked on the [Alsa]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel") site and ICH8 isn't included as a supported chipset on any of the intel sound cards, so essentially my question is, is there anything i can do about this?

---

