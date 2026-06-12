---
title: "[SOLVED] audio problem on laptop"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by orrie on 2007-12-06
Laptop: Asus A3HF

When I'm trying to play some music on the laptop after a fresh Gutsy-install, the speakers are just playing some weird sounds.

I have checked the `alsamixer`, and there are only "accessable" choose in the fields "PCM","Line","CD","Mic".

But, I think it was a little bit weird that I couldn't turn up or at all change the volume at the "Front".
I guess that the "Front" is the speaker?

Realtek ALC660.

---

### Post by orrie on 2007-12-06
Problem fixed using [this guide](https://help.ubuntu.com/community/HdaIntelSoundHowto) :)

Just setting the option snd-hda-intel model to asus.

Won't work with the selection 3stack-660.

---

