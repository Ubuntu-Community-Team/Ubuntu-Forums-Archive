---
title: "Post Update Sound Issue"
date: 2010-08-09
forum: Multimedia Software
---

### Post by rchille on 2010-08-09
Good evening all,

I have a MiniITX box that I use for a media server attached to my TV. Everything seemed to be OK until today when my sound stopped working. It seemed to happen after that update/upgrade I did when I got home, but I can't confirm this is the trouble as I didn't do anything that would've played sound before the update

Here is a link the the alsa-info.sh file:
[http://www.alsa-project.org/db/?f=cb665a5d33d1296bb1909abd6bbc76869cb9a6af](http://www.alsa-project.org/db/?f=cb665a5d33d1296bb1909abd6bbc76869cb9a6af)

A little more background:
Running a Zotac ION MiniITX:
[http://www.zotacusa.com/zotac-ionitx-g-e-synergy-atom-n330-1-6ghz-dual-core-mini-itx-intel-motherboard.html](http://www.zotacusa.com/zotac-ionitx-g-e-synergy-atom-n330-1-6ghz-dual-core-mini-itx-intel-motherboard.html)

and have the audio pushed through the HDMI to my TV.

Anything else needed to help trouble-shoot?
Thanks in advance!

---

### Post by lidex on 2010-08-09
Try updating your alsa install. Use the alsa-upgrade link in my sig.

---

### Post by rchille on 2010-08-10
Thanks for the reply lidex!

I have got the patch installed:
```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 10 2010 for kernel 2.6.32-24-generic-pae (SMP).

```

and aplay is still showing my device:
```
 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

speaker-test doesn't seem to be happy:  
```

speaker-test 1.0.23

Playback device is plughw:2,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Playback open error: -2,No such file or directory

```

I'm still having the trouble that my alsamixer is only showing two options: PCM and S/PDIF. Neither are muted.

The Mixer app shows me only PCM (under Playback) and IEC958 (under Switches). I do not see any other controls to activate.

Updated alsa-info.sh: [http://www.alsa-project.org/db/?f=172a5a7873d2f96920f1818c41c6fceced202394](http://www.alsa-project.org/db/?f=172a5a7873d2f96920f1818c41c6fceced202394)

What can I try next?
Thanks!

---

### Post by rchille on 2010-08-11
Nothing a re-install couldn't fix :)

I got pretty far down the rabbit before I gave-up and tried the Windows solution (aka: re-install). Happily, this was the frontend of the media center that I had just setup a week ago so it didn't take very long! 

Thanks again for the help!:)

---

### Post by lidex on 2010-08-14
Please mark thread solved and have fun!

---

