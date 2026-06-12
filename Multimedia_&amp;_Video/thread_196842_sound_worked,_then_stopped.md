---
title: "sound worked, then stopped"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by dasratsel on 2006-06-14
howdy,
i just did a fresh install of dapper yesterday, and after the install i was configuring thigs to the way i like them, and stumbled into the system sounds, and things worked as i expected... then today, i installed xmms and xine, only to find that my sound no longer works. not even the system sounds work, which baffles me.
here's "lspci | grep Multimedia":
```
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

```
and here's "lsmod | grep snd":
```
snd_cs46xx             85576  1
gameport               15496  2 snd_cs46xx
snd_rawmidi            25504  1 snd_cs46xx
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         92704  1 snd_cs46xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs46xx,snd_pcm

```

i'm using a thinkpad T22 laptop.
things seem in order, mixer levels seem ok, is there something i'm overlooking?

thanks
~Xavier

---

### Post by dasratsel on 2006-06-14
in alsamixer apparently i needed to turn up DAC .... which leads to my question:
what's DAC?

---

### Post by neo_reloaded on 2006-06-14
DAC Stands for Digital To Analog Converter  - self explanatory. But I just wonder, I didnt have to get into all that stuff to hear sounds! Well I have a t42p laptop- but the sound card's gonna be same.

---

### Post by dasratsel on 2006-06-16
yea, best i c'n imagine, one of the packages i installed must've changed my DAC mixer value... go figure.

i have one more question about the thinkpad though...
when i boot, the thinkpad volume buttons only work some of the time... sometimes running "sudo thinkpad-keys" works in bringing it back, sometimes not

this isn't a big problem, my sound is fine and the volume buttons work, only thing is it doesn't always link the volume buttons to the mixer. anyone else ever have this problem?

thanks
~Xavier

---

