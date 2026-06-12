---
title: "Change amarok2 output device"
date: 2009-05-11
forum: Multimedia Software
---

### Post by g0ng on 2009-05-11
Hello,

I have installed ubuntu 9.04 and I use OSS for audio since soundblaster X-Fi isn't recognized by alsa.
/dev/dsp is linked to /dev/oss/oss_sbxfi0/pcm0 and I have sound with vlc and mplayer but not with amarok. OSS recognizes the two soundcard (my on board soundcard and the X-Fi) and creates two devices: /dev/oss/oss_sbxfi0/pcm0 and /dev/oss/oss_hdaudio0/pcm0

Previously with 8.04 (older version of amarok) you could alter in the options the output device. But not with this one. Is there a way to change this? I read somewhere about .xine/config.

I put 

```
# audio driver to use
# { auto  null  pulseaudio  alsa  oss  jack  file  none }, default: 0
audio.driver:oss 

# device used for pulseaudio
# string, default: 
audio.pulseaudio_device:/dev/oss/oss_sbxfi0/pcm0
```


but nothing happened. Any other solution?

thanks

---

