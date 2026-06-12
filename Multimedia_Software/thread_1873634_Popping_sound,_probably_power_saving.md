---
title: "Popping sound, probably power saving?"
date: 2011-11-01
forum: Multimedia Software
---

### Post by The last Bert on 2011-11-01
Hi,

I am getting a popping sound from my speakers just before audio is played, and again about 5 seconds after audio stops. Reading around, this seems to be power saving related (i.e. the noise is due to the audio amp being switched on and off). Is there an easy way to disable audio power saving? There was no power save option set in alsa-base.conf, so I added ```
options snd_hda_intel power_save=0
```just to be expilicit, but it had no effect.

lspci | grep Audio gives:
```
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
```

and  cat /proc/asound/cards gives:
```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6480000 irq 21
```

so I thought that power save option should work. 

I am running Kubuntu 11.10, not sure if Pulse makes things different, a lot of what I've read is quite dated.

Any help greatly appreciated.

TLB

---

