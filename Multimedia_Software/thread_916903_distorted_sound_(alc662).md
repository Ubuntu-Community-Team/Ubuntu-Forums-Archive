---
title: "distorted sound (alc662)"
date: 2008-09-11
forum: Multimedia Software
---

### Post by jyaan on 2008-09-11
I am running Hardy 8.04 (fully updated). My motherboard is Biostar GF8100 M2+ SE with Realtek ALC622 (HDA NVidia) onboard sound.

Sound is **perfectly** fine in flash, but in java, videos and music the sound randomly gets 'scratchy'. It indeed appears totally random, although at times it will subside for a matter of (a) second(s); yet mostly the scratching accompanies nearly every sound.

I've added the following to /etc/modprobe.d/options:
```
options snd-hda-intel model=3stack-6ch-dig
``` 

Under System > Pref > Sound I've set all to ALSA. Changing these doesn't appear to help regardless. 

I've tried removing pulseaudio; however, that was to no effect.

Changing the volume settings does not appear to make any difference. The distortion is present with both headphones and speakers. Putting the sliders past half results in completely inaudible sound, which was not the case on my old pc (using the same old speakers). I am not using spdif. 

Any ideas?

---

### Post by jyaan on 2008-09-11
Has anyone heard anything about this issue with this chipset? I noticed the sound is also stuttering in music playback. I have tried several players; amarok, mplayer, vlc, etc - yet they all have the same static-plagued audio. 

I can't understand why flash has perfect audio, yet everything else is horrible, to the point where music and video has no potential of being enjoyable. :mad:

I'm still searching through the forums but not finding any solutions. I've tried various options for my /etc/modeprobe.d/alsa-base, all with the same results.

Is there really no solution and I should buy a new sound card? It seems there are people that have Realtek alc662 operating without problems. How??? :(

---

### Post by jyaan on 2008-09-12
I've just found out that mute does not work for any channels except for PCM.

---

### Post by jyaan on 2008-09-12
Switching the settings in System > Pref > Sound to OSS has solved the sound problem for java. It's still occurring in video/music playback, however. :(

---

### Post by jyaan on 2008-09-12
Well, sound is usable now that I've edited the mplayer and vlc (vlc is better than before but not really usable..) config files to use OSS, and changed amarok settings to use it as well. But is there any way to make ALSA operate correctly (I'd really like ALSA support...) ? Hopefully this should help narrow down the problem now that *something* has been shown to work. Thanks (if anyone is listening out there!:lolflag:).

---

### Post by jyaan on 2008-09-12
Well, it looks like that was a fluke. It seems like nobody cares anyways so I'll just buy SB Audigy SE later on if I can't figure it out myself.

---

### Post by nooooobi on 2008-12-25
i had the same problem with the same board, but today i managed to solve the problem. 

for me it worked like this:

at first i installed and configured medibuntu following the instructions. 
then i tried .ogg files and it worked perfectly with totem.
then i tried .mp3 files, but totem told me to download and install the right codecs, i did so as suggested by the system, and everything works fine now. (i forgot the name of the codecs, but there were 2 of them, the name was something with G).

---

