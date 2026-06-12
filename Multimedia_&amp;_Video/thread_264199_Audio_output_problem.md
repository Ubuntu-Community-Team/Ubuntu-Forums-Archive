---
title: "Audio output problem"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by ke20 on 2006-09-24
Hello,
I'm a french Ubuntu user  and I have a problem with my audio output.
My computer is an Asus A6VC, the soundcard is an Intel HDA.
I followed the tuto to install the driver and it works but only when I have nothing plugged in the audio (jack) output. I can just hear the music with my laptop speakers which only one works.
the result of aplay -l is (sorry it's in french):
```
ke20@ubuntu:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC880 Analog [ALC880 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 2 : ALC880 Digital [ALC880 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0   
```


and for lsmod | grep :
```
ke20@ubuntu:~$ lsmod|grep snd
snd_hda_intel          20468  2
snd_hda_codec         166096  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

```

Does anybody know what is the problemps:soory for my bad english

---

