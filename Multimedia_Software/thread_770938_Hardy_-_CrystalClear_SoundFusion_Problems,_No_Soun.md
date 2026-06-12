---
title: "Hardy - CrystalClear SoundFusion Problems, No Sound"
date: 2008-04-27
forum: Multimedia Software
---

### Post by fwre01 on 2008-04-27
So, i decided to put Hardy on my unkles (rather dated) PC. most things came up fine, except the sound. its a pretty old onboard sound card. if i do a sudo lshw i see this
```
*-multimedia UNCLAIMED
                description: Multimedia audio controller
                product: CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]
                vendor: Cirrus Logic
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=56 maxlatency=24 mingnt=4
```

So, i found out the kernel should be using this module snd-cs46xx. so i figured it just wasn't loading the driver, (...or just didnt have the driver)

when i do an lsmod | grep snd-cs46xx i see this 

```
snd_cs46xx             86748  1 
gameport               16008  1 snd_cs46xx
snd_ac97_codec        101028  1 snd_cs46xx
snd_pcm                78596  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            25760  2 snd_cs46xx,snd_seq_midi
snd                    56996  11 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

...which i assume means it has loaded that module?

so...how do i tell the sound card to use that driver? iv found another post on the forums where a guy posted this output, he looks asthough he has the same card, and IS using that driver.

```
*-multimedia
                description: Multimedia audio controller
                product: CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]
                vendor: Cirrus Logic
                physical id: 7
                bus info: pci@02:07.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Sound Fusion CS46xx latency=64 maxlatency=24 mingnt=4
                resources: iomemory:fe2ff000-fe2fffff iomemory:fe100000-fe1fffff irq:19
```

so all i think i need to do is to get that driver loaded properly? any thoughts?

Any help would be great, if you need any more info just say! Thanks

---

