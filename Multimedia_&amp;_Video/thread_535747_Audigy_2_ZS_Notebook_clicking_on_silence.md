---
title: "Audigy 2 ZS Notebook clicking on silence"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by agashlin on 2007-08-26
I'm running Feisty and have an Audigy 2 ZS Notebook sound card to replace the built in one (which I've disabled via /etc/modprobe.d/blacklist), the laptop itself is an Acer TravelMate 2480.
The problem is that whenever sound playback begins or ends there is an audible pop in the headphones.  This gets particularly irritating with qsynth, as it happens whenever the audio falls to silence, but it happens with any audio format in any audio player I've tried, as well.  The built in card didn't have this issue (it had a different fun issue with the headphones not working most of the time, but that is a different topic...)

Hope that I might get some advice here, I'll try poking at Creative as well.

---

### Post by agashlin on 2007-08-30
I was able to avoid the clicking by enabling "Tone" in alsamixer.  This makes the bass and treble sliders take effect as well, so I set those both to 50 so as not to use them.

---

