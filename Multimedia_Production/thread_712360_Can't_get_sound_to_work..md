---
title: "Can't get sound to work."
date: 2008-03-01
forum: Multimedia Production
---

### Post by Morph-------------- on 2008-03-01
I've been using ubuntu for quite a while now but all of a sudden (i think) the sound doesn't work anymore. I haven't yet found a solution and i need help!
What i can say is that in the upper right corner a icon is showing that sound doesn't work, when i double click it i get a message with: ```
No volume control GStreamer plugins and/or devices found.
```

lspci -v gives me:
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

aplay gives me:
```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:550: audio open error: No such device

```

Thanks in advance =)

---

