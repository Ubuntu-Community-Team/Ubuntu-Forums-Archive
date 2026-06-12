---
title: "pulseaudio sound broken - all devices are gone (10.4)"
date: 2010-10-13
forum: Multimedia Software
---

### Post by flavourmetz on 2010-10-13
Hi everybody,

for some unknown reason my formerly perfectly well sound setup stopped working all of a sudden in Ubuntu 10.4. I can't reproduce what led to this unfortunate event.

I have a Creative X-Fi (Gamer) soundcard running with pulseaudio. When I look at the sound preferences, I see that there are no devices listed. Applications like rhythmbox just freeze on loading. 

Doing a```
lspci | grep audio 
``` I get ```
05:09.0 Multimedia audio controller: Creative Labs SB X-Fi 
```

Also, the driver module seems to be loaded:
```
lsmod | grep xfi
snd_ctxfi             100843  0 
snd_pcm                87882  3 snd_usb_audio,snd_ctxfi,snd_pcm_oss
snd                    71187  11 snd_usb_audio,snd_hwdep,snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          8500  2 snd_ctxfi,snd_pcm
```


Does anybody know how to fix this? Many thanks in advance!

---

### Post by przemek35 on 2010-10-18
> **flavourmetz said:**
> Hi everybody,
 
for some unknown reason my formerly perfectly well sound setup stopped working all of a sudden in Ubuntu 10.4. I can't reproduce what led to this unfortunate event.
 
I have a Creative X-Fi (Gamer) soundcard running with pulseaudio. When I look at the sound preferences, I see that there are no devices listed. Applications like rhythmbox just freeze on loading. 
 
Doing a```
lspci | grep audio 
``` I get ```
05:09.0 Multimedia audio controller: Creative Labs SB X-Fi 
```
 
Also, the driver module seems to be loaded:
```
lsmod | grep xfi
snd_ctxfi             100843  0 
snd_pcm                87882  3 snd_usb_audio,snd_ctxfi,snd_pcm_oss
snd                    71187  11 snd_usb_audio,snd_hwdep,snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          8500  2 snd_ctxfi,snd_pcm
```
 
 
Does anybody know how to fix this? Many thanks in advance!
 
try to remove pulseaudio and instal alsa instead

---

