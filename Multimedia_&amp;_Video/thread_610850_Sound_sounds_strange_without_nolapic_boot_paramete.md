---
title: "Sound sounds strange without nolapic boot parameter in Gutsy."
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by skovenborg on 2007-11-12
Hi and sorry for the nondescriptive title.

Normally I boot Gutsy with the noapic nolapic irqpoll parameters but since nolapic causes the whole system to run extremly slow and freeze I decided to remove it. But then the sound started acting very weird.
When I play music it sounds like an old record that's stuck in the same place (other than its actually do play the whole song - the output just doesn't make sense). It's very hard to explain but lets just say it sound strange for now.

I'm sorry I can't give any other information right know because I don't really know where to look.

I'm running Kubuntu 7,10 Gutsy Gibbon with all the latest updates.
The soundcard is a VIA VT8233 AC97.
I attached the output from lspci -vvnn
Here's also a snippet from the lsmod output:
```

snd_via82xx            29336  1
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
via_ircc               27668  0
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
analog                 13344  0
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0
gameport               16776  2 snd_via82xx,analog
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
i2c_viapro             10004  0
serio_raw               8068  0
psmouse                39952  0
nvidia               4716468  22
snd                    54660  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```

---

### Post by RussNelson on 2008-04-24
What you're seeing is the DMA controller asserting an interrupt saying "I need more data", the interrupt being serviced late, and the DMA buffer being replayed.

---

