---
title: "[SOLVED] Alsa has stopped working."
date: 2008-08-22
forum: Multimedia Software
---

### Post by Prefix100 on 2008-08-22
I have a HDA-Intel sound card, yesterday Alsa was working perfectly, after a restart this morning, it isn't.

**Note:** I'm not using pulseaudio, just ALSA.

When I goto system>preferences>sound and have alsa selected and test the sound I get the following error.

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

However if I select my card directly and test the sound it works fine. Now this is all well and good until I go to use an application that tries to use ALSA, Quake4 for instance, or indeed firefox, I get no sound.

I'm not really sure what commands to show you guys for alsa problems so you'll have to ask me for outputs.

aplay
```

jonny@jonny-desktop:~$ aplay
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such file or directory

```

aplay -l
```

jonny@jonny-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

alsamixer
```
jonny@jonny-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

Thanks,
Prefix

EDIT: I'm going away for the weekend, so I guess this topic is just going to sink to the 10th page, but if you could help me out, I'd greatly appreciate it.

---

### Post by Prefix100 on 2008-08-25
Solved, after a restart and removing webcam it worked.

---

