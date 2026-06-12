---
title: "CMUS error on 12.04 server"
date: 2012-08-04
forum: Multimedia Software
---

### Post by mcc28x on 2012-08-04
Hi,

I have a Server install of 12.04 and wanted to play some music from the command line so I installed CMUS.

When I try to play a track I get: 'Error: opening audio device: No such device'

The output of lspci -v | grep -A7 -i "audio" is:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

--
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV670/680 HDMI Audio [Radeon HD 3690/3800 Series]
        Subsystem: Giga-byte Technology Device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f5010000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel
```

Could anyone help me troubleshoot this please?

Thanks

Mark

---

