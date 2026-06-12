---
title: "Sound test works...no sound ouptut"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by johannix on 2008-02-25
I have SB Audigy 24 bit audio card and have it working in the sound test with ALSA although when I try to play music with amarok i dont hear anything. Thats the case with everything except for the sound test.

I've already tried messing with the settings in alsamixer.

Other steps already taken:
```
$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0413] at 0xbce0 irq 16
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 16
```

```
$ lsmod | grep snd
snd_hda_intel         263712  0 
snd_ca0106             34720  3 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_ac97_codec        100644  1 snd_ca0106
snd_seq_dummy           4740  0 
snd_pcm                80388  5 snd_hda_intel,snd_ca0106,snd_pcm_oss,snd_ac97_codec
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_ca0106,snd_pcm_oss,snd_mixer_oss,snd_ac97_codec,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac97_bus                3200  1 snd_ac97_codec
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_hda_intel,snd_ca0106,snd_pcm
```

```
$ sudo asoundconf list
Names of available sound cards:
CA0106
Intel
```

```
$ sudo asoundconf set-default-card CA0106
```

---

### Post by terry_gardener on 2008-02-25
i had a similar problem when i installed the oss driver for the x-fi card. when i ran osstest i got sound but when i started mp3 players no sound. 

I fixed this by disabling the soundcard in the bios system.

---

### Post by johannix on 2008-02-29
I tried disabling the system sound and nothing changed.

Keep in mind that the sound works in the sound test just not in any applications.

---

### Post by johannix on 2008-03-02
Still have this problem.

Is there anyway to clear all my changes and have Ubuntu "figure out" my sound settings as if this were a new system?

---

