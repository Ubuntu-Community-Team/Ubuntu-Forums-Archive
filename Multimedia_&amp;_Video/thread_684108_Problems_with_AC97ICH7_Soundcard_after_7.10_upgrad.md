---
title: "Problems with AC97/ICH7 Soundcard after 7.10 upgrade"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by elijahwrx on 2008-01-31
For whatever reason, my soundcard decided to stop being recognized after my upgrade to 7.10.  I haven't really worried about it until now because I haven't been using the box much.  That has recently changed, and after working through the comprehensive sound problems guide, I'm at a loss.

Here's the entry in an lspci -v:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 0606
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at d2100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```

Listing of currently loaded modules:

```
Module                  Size  Used by
snd_ac97_codec        101028  0 
snd_pcm_oss            52096  0 
snd_mixer_oss          17280  1 snd_pcm_oss
snd_pcm                85768  2 snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_seq_dummy           3972  0 
snd_seq_oss            34816  0 
snd_seq_midi            9856  0 
snd_rawmidi            26368  1 snd_seq_midi
snd_seq_midi_event      7680  2 snd_seq_oss,snd_seq_midi
snd_seq                57328  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24708  2 snd_pcm,snd_seq
snd_seq_device          8844  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    61708  13 snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
ac97_bus                2432  1 snd_ac97_codec

```

And finally, the aplay output:

aplay: device_list:204: no soundcards found...

I've tried uninstalling/reinstalling the drivers per the guide, as well as building things from scratch.  Nothing is working.

Any suggestions?

Thanks in advance for any help!

-Eli

---

