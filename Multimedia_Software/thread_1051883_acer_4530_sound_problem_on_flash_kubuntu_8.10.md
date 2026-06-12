---
title: "acer 4530 sound problem on flash kubuntu 8.10"
date: 2009-01-27
forum: Multimedia Software
---

### Post by nikolaiortiz on 2009-01-27
Hi all..
i get this acer aspire 4530 and install kubuntu 8.10 all works fine.. but the sound doesn't work for flash
i try some things posted but i dont know if i dont make well..
please some help..
```
lsmod |grep snd
snd_hda_intel         381488  2
snd_pcm_oss            46848  0
snd_mixer_oss          22784  3 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0
snd_seq_oss            38528  0
snd_seq_midi           14336  0
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  3 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
```

---

### Post by Linuxdork on 2009-01-27
I think this may be the problem: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) Let us know how it works.

---

### Post by nikolaiortiz on 2009-01-27
Ok i will try again.. but i made it before, maybe i made something  wrong 
i will try very carefully.

---

### Post by nikolaiortiz on 2009-01-27
ok all seem to be good  for now..!!!
all works fine!!
thanx a lot 
Linuxdork

---

### Post by Linuxdork on 2009-01-27
No problem man.

---

### Post by nikolaiortiz on 2009-04-15
i back again..

jejeje
well..
all thing looks fine.. but suddenly i want to use my headphones and 
the thing doesn't work :(

any ideas?
i try this
but nothing happend

/etc/modprobe.d/alsa-base

```
options snd-hda-intel model=acer

```

---

