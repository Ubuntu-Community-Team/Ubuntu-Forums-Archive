---
title: "poor sound &amp; volume Ubuntu 9.04"
date: 2009-04-29
forum: Multimedia Software
---

### Post by Rodd on 2009-04-29
I have upgraded to ubuntu 9.04
but have lost sound quality and have hardly any volume.
and have tried most of the no sound threads but nothing has worked
My sound chip is on the mobo using the SIS964 southbridge chipset which is compliant with the AC'97 v2.3 Codec 
I have run 
rod@rod-desktop:~$ lsmod | grep snd

snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm

and a lot of the scripts in the no sound threads sadly no changes 
I have tried the diffrent sound drives in the sound volume preferances ie pulse , Alas, OSS, Realtek ALC655..... and no joy
The sad part is the sound works perfectly in winXP partition using the lastest Realtek drivers and I don't want to return to using winXP 
So can anyone help

thanks 
Rodd

---

### Post by Kizsde on 2009-04-29
Hi!

I'm a newbie myself and maybe you already have done this, but I experienced some sound quality loss in Ubuntu, when I installed it first. My problem was that there was some noise disturbance/crackling when playing songs. What I found that I had to lower the PCM slider in the sound settings (Advanced option I think). After that it was a bit quieter, so I raised that master volume up and from then on it was fine. Maybe this helps!

---

### Post by abloss01 on 2009-05-10
Hi,

I face similar problem with my installation of 9.04.  The sound works perfectly fine - nice and clear in the (dual boot) Vista installation on the same machine - yet in 9.04, it is barely audible. In my 9.04, from max setting, turning the volume 2 notches down is equivalent to shutting the sound off completely.

---

### Post by abloss01 on 2009-05-10
I tried alsamixer as per the advice in this post [http://www.linuxquestions.org/questions/ubuntu-63/volume-control-doesnt-work-721615/](http://www.linuxquestions.org/questions/ubuntu-63/volume-control-doesnt-work-721615/).

Since I was using headphone, I turned the alsamixer headphone volume to max.  What's more interesting was that somehow with alsamixer, I was able to turn the master volume to a much higher level than previously.  The bottom line was this did seem to fix my problem.

Hope this helps !

---

