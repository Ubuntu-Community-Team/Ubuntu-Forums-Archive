---
title: "MPD can't open alsa device"
date: 2008-11-28
forum: Multimedia Software
---

### Post by mts280 on 2008-11-28
Hi,

mpd can't open my soundcard when using plughw. This is my config:

```

audio_output {
        type                    "alsa"
        name                    "Juli"
        device                  "plughw:0,0"     # optional

#        format                  "44100:16:2" # optional
}

```

when trying to play, i get:

```

ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
Nov 28 17:50 : Error opening alsa device "plughw:0,0": No such file or directory

```

other applications work perfectly when using plughw:0,0. I'm using a ESI Juli@ sound card.

Thanks for any hints,
mts280

---

