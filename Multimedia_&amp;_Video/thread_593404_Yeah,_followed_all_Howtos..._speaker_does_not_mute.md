---
title: "Yeah, followed all Howtos... speaker does not mute when headphone jack plugged in"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by wnmnkh on 2007-10-27
Yes, infamous Sony Vaio one. (FZ series)

In fact there was no sound from headphone jacks for a while until I eventually set my model as vaio (see Hdaintel howto.)

Then now my headphone jack works, but speaker does not mute at all.

my 'lsmod | grep snd'

```
 
snd_hda_intel         262552  1 
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35328  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

```

chip is STAC9872.

btw, I actually got two cards instead of one. but it seems only sigmatel one is working. Maybe this is the problem.

the result of ' head -n 1 /proc/asound/card0/codec*'
```

==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9872AK

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06


```

---

