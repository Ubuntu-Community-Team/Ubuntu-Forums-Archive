---
title: "ALSA software mixer pwnt"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Weird Al on 2007-10-22
On Edgy it used to be that an application using the sound card would block it for ALSA, and thus I could only have one going at once.

Google Fu found this page [http://www.thepenguin.org.uk/alsa/](http://www.thepenguin.org.uk/alsa/) and I copypasta'd directly and it worked after restarting ALSA.

Now, with Gutsy, it doesn't. Wine outputs errors:

```
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
```

And if I'm running wine I can't use mplayer, as an example.

```
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
```

My asound.conf is as in the above link. Also:

```
al@llathrael:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1370/1 [ES1370 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1370/2 [ES1370 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any more info needed just holler.

So, what's changed in ALSA, and what do I need to change to keep up with it?

---

