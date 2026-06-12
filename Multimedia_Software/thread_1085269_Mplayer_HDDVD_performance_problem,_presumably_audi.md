---
title: "Mplayer HDDVD performance problem, presumably audio"
date: 2009-03-02
forum: Multimedia Software
---

### Post by Cracauer on 2009-03-02
Playing HD-DVDs in mplayer (cvs version). Everything works fine, except that I get jerky playback.

It is much better (as in watchable versus unwatchable) when I only use 2 audio channels as opposed to 6.  CPU usage is 61% with 2 channels and 66% with 6 channels, and that is just one core, the other one is idle.  So I think I'm not out of CPU here, and even if I use 2 channel output it still reads a 5.1 stream and merges it.

So I figure my problem is in actual output of the audio stream to the soundcard.

I have HDA Intel sound, onboard on a D975XBX ("BadAxe1")
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01).  Driver is ALSA in 2.6.26.3.

Is there anything that I can do to ease the load? Something like changing to mmap, or not use ALSA or something else?

I would prefer to avoid putting in a better PCI card, but out of curiosity, would that help? Does Linux have some kind of actual acceleration such as sending the original compressed EAC3 stream? I can't imagine that format is supported, even if the capability exists.

---

