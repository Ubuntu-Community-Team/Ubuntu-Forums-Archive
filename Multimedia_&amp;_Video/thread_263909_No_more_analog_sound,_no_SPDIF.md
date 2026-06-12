---
title: "No more analog sound, no SPDIF"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by jonnythan on 2006-09-23
I have a GeForce 6100 board with builtin analog and optical audio.

I'm trying to set the box up as a DVD player and LAMP server. I installed LAMP server, then xubuntu-dektop, then used EasyUbuntu to install the DVD codecs and so forth. I then installed gxine.

Well, I got DVDs to play on gxine, but audio only came out of the analog port. I changed the preferences to "Pass Through," but no audio came out of the optical port.

I changed it back to "Stereo 2.0" and now I can't get audio out of anything no matter what I try.

1) How do I troubleshoot this problem?

2) How do I get Dolby Digital out of this system??

---

### Post by jonnythan on 2006-09-23
I got analog audio back by putting the volume icon on the taskbar and turning IEC958 Piayback AC97 halfway up (turning this halfway up seems to enable PCM audio - halfway up is on, anything below is off - it doesn't adjust volume).

Anyway, I still can't get anything at all out of the optical port. Everything is hooked up correctly. The receiver end of the cable is lit.

I'm very frustrated. Please help!

---

### Post by jonnythan on 2006-09-25
Someone please help, I'm going nuts over this :(

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
/# lsmod | grep snd
snd_intel8x0           35804  2
snd_ac97_codec         99296  1 snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
snd_pcm                96772  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  1 snd_pcm
snd                    60068  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11040  1 snd
snd_page_alloc         11592  2 snd_intel8x0,snd_pcm
```

I have no asound.conf. What else can I do?

---

### Post by jonnythan on 2006-09-25
Help? Anyone? Please?

---

