---
title: "Front right channel is crackling over spdif"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by peterdm on 2008-02-22
Whenever I play PCM audio over spdif, the right channel crackles. Especially speach etc. are noticeably affected. I have an on-board intel audio chipset:

```

root@cheetah:~# aplay -L
default:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

All this on an up-to-date gutsy.
This problem is driving me nuts. Here is what I've learned so far:

1) Digital pcm audio sources other than my pc sound fine (consumer dvd player, minidisc, dvd)
2) Output via headphones (non-digital mini-jack on my pc's front) sounds fine
3) Dolby Digital and DTS hardware pass-through sound fine as well (tested with mplayer)
4) Playing a cd through a consumer cd player sounds fine, through the same digital spdif input connector on my amp. When playing the same cd from the pc, it crackles
5) It seems to affect only the right channel, and only when playing PCM over spdif

Anybody has any ideas on this one?


Peter

---

### Post by peterdm on 2008-02-22
Some more digging into the issue, I've found out that I have a particular model of sound card:
Codec: Analog Devices AD1988B

Desperate as I was, I came across the following howto and followed its advice:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I downloaded, recompiled and installed alsa 1.0.16...
Then I figured out the module parameters for my "Analog Devices AD1988B" type of sound card in /etc/modprobe.d/alsa-base...

```

# Try to fix crackling front right speaker in 2-ch pcm spdif playback
options snd-hda-intel model=6stack-dig

```

And miraculously, the pcm sound works great now!
No crackling whatsoever!

I'm suspecting the module option had more to do with it than the new driver version.

Then the downside: hwdts and hwac3 are now broken.

```
mplayer: relocation error: mplayer: symbol snd_config_search_alias_hooks, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

```

After this I can't even type anything in the terminal window anymore. Grrrr! It's always something, isn't it...

---

### Post by mala88 on 2008-04-27
I have the same issue with the hwac3 output and am getting the same error from mplayer.

Were you able to fin a solution to this?

---

