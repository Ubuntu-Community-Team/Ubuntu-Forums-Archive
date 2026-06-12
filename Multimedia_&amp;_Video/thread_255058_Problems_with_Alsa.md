---
title: "Problems with Alsa"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by Mithrilhall on 2006-09-10
I'm trying to run alsamixer from the command line and I keep getting the following error message:

> 
doom@Innorruk:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
doom@Innorruk:~$                              


It was working the other day and I don't think I changed anything. I might have applied some updates but I can't remember for sure.

The odd thing is sound is still working for some things. I'm listening to MP3s via Amarok but the audio in streaming video in Firefox isn't working. I don't think any of my system sounds are working.

I can play DVDs via Kaffeine and get sound as well.


Any suggestions on what I can do to fix this? It's driving me nuts.

---

### Post by shat on 2006-09-10
I'm having a [similar problem]("http://ubuntuforums.org/showthread.php?t=254238"), I wonder what would happen if you tried 
```
alsamixer -c 0
```

---

### Post by Mithrilhall on 2006-09-10
I get:

> 
doom@Innorruk:/usr/bin$ alsamixer -c 0
wrong -c argument '0'

doom@Innorruk:/usr/bin$            


But if I run
> 
alsamixer -c 1


it works.

Now, how come certain programs and the OS can't play sounds? Amarok works fine but other things don't.

---

### Post by Mithrilhall on 2006-09-11
Is there a way I can trick linux to think alsamixer -c 1 is alsamixer -c 0?

---

### Post by Mithrilhall on 2006-09-13
Ok..I'm still having the same issue here. I can't seem to figure this out. Any suggestions would be helpful.

> 
eric@Innorruk:~$ lsmod|grep snd
snd_intel8x0           33692  2
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm


---

### Post by Mithrilhall on 2006-09-13
Well I finally got it working again.

I changed this line in /etc/modprobe.d/alsa-base

> 
options snd-via82xx-modem index=-2


to

> 
options snd-via82xx-modem index=0


---

### Post by Mithrilhall on 2006-09-13
Well..I'm not sure it worked actually. I have sound in Firefox now but I can't start alsa-utils from Sound System.

---

