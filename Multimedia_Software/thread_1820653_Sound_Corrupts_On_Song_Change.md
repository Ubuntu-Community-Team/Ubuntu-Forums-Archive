---
title: "Sound Corrupts On Song Change"
date: 2011-08-07
forum: Multimedia Software
---

### Post by cerberos on 2011-08-07
After a fresh boot the first few songs I play with Banshee or Rhythmbox (only used for testing if Banshee was the issue) the songs start to be played badly distored. Like the sound is only being played in very short bursts with gaps between them. 

If I restart Banshee the music will usually resuming playing fine for a couple of songs and then the issue repeats. If system load is high the number of songs before the issue appears decreases (as low as 0).

I've attached the output of the alsa-info.sh as I see 90+% of audio issue threads ask for that file in the first reply :)

---

### Post by cerberos on 2011-08-09
Does anyone have any pointers on where I should be looking?

---

### Post by cerberos on 2011-08-11
Apparently restarting the Alsa system solves it for quiet a while, I guess that's the best solution I'm going to get.

---

