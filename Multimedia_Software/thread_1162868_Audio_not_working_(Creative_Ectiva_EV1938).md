---
title: "Audio not working (Creative Ectiva EV1938)"
date: 2009-05-18
forum: Multimedia Software
---

### Post by r0ck80y on 2009-05-18
Hi,

So theres this HP Pavilion 6100 desktop pc that has the "Creative Labs Ectiva EV1938" audio controller according to lspci but i cant hear any audio (on Ubuntu 9.04). A bit of googling through older posts shows its a complicated problem. Is anyone able to run any audio on this hardware? Heres a pic of alsamixer ui display on the pc: [http://i40.tinypic.com/2w7jqu1.jpg](http://i40.tinypic.com/2w7jqu1.jpg)

**lsmod**:
```
binfmt_misc            16776  1 
ppdev                  15620  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
snd_ens1371            30496  5 
gameport               19340  1 snd_ens1371
snd_ac97_codec        112292  1 snd_ens1371
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
psmouse                61972  0 
serio_raw              13316  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  19 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
sc92031                22532  0 
snd_page_alloc         16904  1 snd_pcm
pcspkr                 10496  0 
k8temp                 12416  0 
i2c_nforce2            14980  0 
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
:
:
```

TIA :|

---

