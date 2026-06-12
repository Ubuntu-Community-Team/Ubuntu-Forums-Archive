---
title: "Sound suddenly stops on streaming video/flash playback on MPlayer"
date: 2010-08-05
forum: Multimedia Software
---

### Post by Juzo on 2010-08-05
Hello friends, 
I'd recently installed Xubuntu Lucid Lynx 10.04 on my desktop PC (yes i replaced windows XP totally :)), and run into serious problem as any streaming video or flash (on youtube) stopped playing after couple of minutes and never returned. Only when I restart firefox it plays again couple of minutes and then stops again.
I'm using MPlayer with gecko-mediaplayer plugin for mozilla browsers.
My system is:
CPU P4;
Motherboard: ASUS P4P800-e;
Chipset: Intel 865PE;
Soundcard: Onboard ALC850

ALSA recognizes me as:
0 [ICH5 ]: ICH4 - Intel ICH5
Intel ICH5 with ALC850 at irq 17

My sound driver used by ALSA is snd-intel8x0

What I did:
- Followed all the instructions on "comprehensie sound guide" etc...
- Tried run snd-intel8x0 with any available options as "ac97_quirk(-1 - 6), buggy_irq etc...)
- Tried dmix 

At the end of the days of searching and trying sound plays several minutes and dead again. 
Please help me with that, I really have no idea, except gonig back to windows, and I don't want to do it.

---

