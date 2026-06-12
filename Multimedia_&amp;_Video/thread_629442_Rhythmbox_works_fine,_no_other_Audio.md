---
title: "Rhythmbox works fine, no other Audio"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by Don1500 on 2007-12-02
My sound problems are driving me crazy! I set up Gusty and at one point had all sound, except Rhythembox. Tried so many things I lost track of the original setup. Now I finally have Rhythmbox working good but I don't have any computer generated sounds, And I can't get sound from the internet (Youtube, Internet radio, etc.). Since it was working at some point in the past (I was able to listen to Inet Radio and heard the logon sounds), and since Rhythmbox and Movie Player are working, I know it's a settings thing, but I'll be darned if I can find it. 

Can anyone out there help me with my brain freeze?:confused:

:guitar:

Just thought of something, I have to try downloading a video clip and playing it with xgine. (I will bet that works)

 lsmod | grep snd

```
snd_cmipci             38688  2 
snd_mpu401             10152  0 
gameport               16776  2 snd_cmipci,analog
snd_opl3_lib           12160  1 snd_cmipci
snd_hwdep              10628  1 snd_opl3_lib
snd_mpu401_uart         9984  2 snd_cmipci,snd_mpu401
snd_rawmidi            26112  1 snd_mpu401_uart
snd_seq_device          9740  2 snd_opl3_lib,snd_rawmidi
snd_intel8x0           35484  3 
snd_ac97_codec        101924  1 snd_intel8x0
ac97_bus                3456  1 snd_ac97_codec
snd_pcm                80644  5 snd_cmipci,snd_intel8x0,snd_ac97_codec
snd_timer              24580  3 snd_opl3_lib,snd_pcm
snd                    56708  18 snd_cmipci,snd_mpu401,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_intel8x0,snd_pcm

```

---

### Post by Don1500 on 2007-12-02
bump.....anyone?

Oh, Nevermind, I solved it myself by reinstalling everything.

---

