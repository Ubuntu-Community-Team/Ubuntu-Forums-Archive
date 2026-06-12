---
title: "problem playing short wav files"
date: 2008-11-16
forum: Multimedia Software
---

### Post by searland on 2008-11-16
When I try playing short wav files either using aplay or mplayer, it always seems that the first half (maybe the first half second) won't be played. It also happens in Thunderbird when I set an email notification sound. The sound is cut off and I can hear only a small part of or even none of it.

I use Ubuntu 7.10 and have a integrated Realtek ALC888 sound card. Today, I want to update my sound card driver program. But I could not load snd_hda_intel module after I compiled the alsa driver. So I installed linux-backports-modules to make my sound card work. Now the version of the alsa driver is 1.0.16

Everything seems good: I can play mp3 using Listen, and I can play videos using mplayer. The only problem is playing wav files. Any ideas? Thanks in advance.

searland

PS. I searched the Internet, but I found few people having the same problem. One guy said it might be the problem of alsa 1.0.16. If I use aplay -B 1 wavfile, I can get correct output sound.

---

