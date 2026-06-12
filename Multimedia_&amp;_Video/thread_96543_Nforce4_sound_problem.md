---
title: "Nforce4 sound problem"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by Can0n on 2005-11-29
Hello

I have recently installed Ubuntu after a short flashback to XP and now I dont get the surround to work. I use Ubuntu 5.10 with a Shuttle SN25P. I have installed the drivers från NVidia but dont know if they are active because when I do a "modprobe nvsound" and then tries to change the volume in nvmixer I get "Volume set failed" and in the console it says "Nvsound: Unable to open the Mixer" when I open nvmixer. 
The speakers works fine in Windows.

When I type speaker-test -c 6 I get alot of these messages:
```

Buffer size range from 8 to 10920
Period size range from 4 to 5460
Periods = 4
Buffer time size 2525
To choose buffer_size = 10920
To choose period_size = 2730
was set period_size = 2732
was set buffer_size = 10920
Unable to set sw params for playback: Invalid argument
Setting of swparams failed: Invalid argument
Rate set to 48000Hz (requested 48000Hz)

```

lsmod | grep snd shows:
```

snd_ice1724            60964  1
snd_ice17xx_ak4xxx      4224  1 snd_ice1724
snd_ac97_codec         72188  1 snd_ice1724
snd_ak4114              8576  1 snd_ice1724
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_ak4xxx_adda         6144  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_mpu401_uart         6784  1 snd_ice1724
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  13 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4xxx_adda,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  2 nvsound,snd

```

I have asked around on IRC and search alot of forums but noone seems to know what I can do to try and fix it so Im asking you guys =)

//Johan

---

### Post by Can0n on 2005-11-30
Someone ?

---

