---
title: "Alsa and Delta 44"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by fourbissime on 2006-12-18
Hi there.

I'm strugling here with a soundcard problem. I've got the onboard chip (the via82xx thing) and an M-audio Delta 44 PCI.

I solved my first problem, which was having the Delta-44 used as the primary soundcard. I got it solved by using /etc/asound.conf

But now this is set, I just can't get any sound. I checked in alsamixer to see if everything is unmuted and it seems alright. As i didn't have any clear error messages from gstreamer, i tried in mplayer and here is what i've got :

```
alsa-init: using device default
alsa-init: format s16le are not supported by hardware, trying default
alsa-init: unable to set format: Invalid argument
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
```

I'm really lost here (and a bit pissed off i must admit)

What is even worse is that i had sound when I booted from the liveCD ! ] (*,)

EDIT : being curious, i've just rebooted on the live CD and i've got sound. In fact, my Delta-44 soundcard even appears as the FIRST soundcard when I do aplay -l

(okay, okay, breathe ... and more importantly, don't panic)

---

### Post by fourbissime on 2006-12-19
okay, I found the answer. All I had to do was to add a new file /etc/modprobe.d/sound containing

```
alias snd-card-0 snd-ice1712
alias snd-card-1 snd-via82xx

options snd-ice1712 index=0
options snd-via82xx index=1
```

---

