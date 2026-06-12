---
title: "No sound, Ubuntu 7.10"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Fiskejohn on 2007-10-27
Hi,

I have just installed Ubuntu 7.10 and every thing works great except sound. There's just no sound at all...

Here is output of lsmod | grep snd:
snd_rtctimer            4384  0 
snd_intel8x0           34972  2 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  1 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

Also I am not able to change volume settings in Totem: [http://img220.imageshack.us/img220/9287/soundjp0.png](http://img220.imageshack.us/img220/9287/soundjp0.png)

Best regards
Fiskejohn AKA Anton

---

### Post by Fiskejohn on 2007-10-27
Problem solved. :)

---

### Post by adamorjames on 2007-10-27
> **Fiskejohn said:**
> Problem solved. :)

Would you mind explaining your solution for others to see? Also, add to the title of this thread, "[SOLVED]".

---

