---
title: "fresh install, no sound"
date: 2009-11-19
forum: Multimedia Software
---

### Post by SeriousName on 2009-11-19
I'm having the problem described in the title; Kubuntu 9.10, I'm not getting sound, except that when audio should be playing and I turn up the speakers very high, I can hear a bit of a crackling. I've tried changing the multimedia settings to no avail. I've tried installing the pulseaudio-utils package, which hasn't helped. Here's the audio devices that show up using lspci -v:

```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Subsystem: Giga-byte Technology Device a102                
Flags: bus master, slow devsel, latency 32, IRQ 16         
Memory at fe024000 (64-bit, non-prefetchable) [size=16K]   
Capabilities: <access denied>                              
Kernel driver in use: HDA Intel                            
Kernel modules: snd-hda-intel

Audio device: ATI Technologies Inc Device 970f
Subsystem: Giga-byte Technology Device 960f
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
```

What else can I try? I'm at a loss. Thanks in advance.

---

### Post by Ulysses361 on 2009-11-20
Please send us the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc that you are using.

---

### Post by SeriousName on 2009-11-20
EDIT: Arrgh, just found that in gnome-alsamixer PCM was turned all the way down. Nevermind, it works now. #-o

Thanks anyways.

---

