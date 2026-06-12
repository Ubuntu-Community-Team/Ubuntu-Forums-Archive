---
title: "sound oddness, skype works, system events not"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by daczo on 2006-10-22
Hi

I have a strange issue on one of mine ubuntu boxes. 
The login chime, notification sounds and other sounds are not working, but I can speak using Skype... (if only I notice that someone is calling, as there is no notification) 

I did some checking, all seams ok, except for "lsof /dev/dsp" returning nothing.
 
$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: V8233A [VIA 8233A], urz&#261;dzenie 0: VIA 8233A [VIA 8233A]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
$ lsof /dev/dsp
$ lsmod | grep snd
snd_rtctimer            3340  0 
snd_seq_dummy           3844  0 
snd_seq_oss            33536  0 
snd_seq_midi            9376  0 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtc                    13492  1 snd_rtctimer
snd_mpu401              6728  0 
snd_via82xx            28824  3 
gameport               15496  2 analog,snd_via82xx
snd_ac97_codec         93216  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  3 snd_pcm_oss
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  3 snd_rtctimer,snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  2 snd_mpu401,snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  14 snd_seq_oss,snd_seq,snd_mpu401,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  3 snd


I enabled all in alsamixer and stored it (alsactl store).

Does anyone have any clue what might be wrong ?
Marcin

---

