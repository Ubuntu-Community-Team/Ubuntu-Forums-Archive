---
title: "Change audio device for flash player"
date: 2011-11-09
forum: Multimedia Software
---

### Post by i.sinister on 2011-11-09
Hi everybody,

I have problem trying to make flash player use HDMI connection. With Vlc player I can play video with sound via Hdmi, so in general Hdmi works just fine.

I'm using Xubuntu 11.10, Firefox 7.0 with  Shockwave Flash 11.0 r1 plugin. I dont use PulseAudio, OSS, ESD or anything else - just Alsa (1.0.24) is installed. There are 2 sound devices on my motherboard:
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
koruyucu@evren:~$ 

```But whenever clip/movie is opened in the flashplayer first device is used. Is there a way to change device used by flash player. It would be better if it could be done without restarting computer =)

Thank you

---

### Post by i.sinister on 2011-11-12
Any ideas?

---

### Post by MoreOrLess on 2011-11-12
Flash player always uses the "default" ALSA device, so you would need a .asoundrc file with something like:

```
pcm.onboard {
type hw
card 0
device 0
}
pcm.hdmi {
type hw
card 1
device 3
}
pcm.flash {
type plug
slave.pcm "hdmi"
}
pcm.!default {
type plug
slave.pcm "flash"
}
```

---

### Post by Toz on 2011-11-12
Or you could install pavucontrol (Pulseaudio Volume Control), startup the flash video and select the output device from the Playback tab.

---

### Post by MoreOrLess on 2011-11-12
> **Toz said:**
> Or you could install pavucontrol (Pulseaudio Volume Control), startup the flash video and select the output device from the Playback tab.

That might work if OP was running pulse..

---

### Post by i.sinister on 2011-11-19
Thank you for reply. Unfortunately config you sent did no work. After reading alsas wiki I managed to make it works with following config:
> pcm.!default {
    type hw
    card 1
    device 3
}
ctl.!default {
    type hw
    card 1
    device 3
}
(I got cardID by running > cat /proc/asound/cards and deviceID by running> aplay -L)
Then I restarted alsa:> sudo /sbin/alsa force-reload and then sound started to work in FF. There is one problem though - only one application can send sound via hdmi - e.g if FF is opened and uses hdmi then VLC can not use it. Can it be solved?

For now  I will prepare 2 configs and a script that will replace that config and restart alsa when I'll need sound via hdmi from FF.

---

