---
title: "MPD controlling system volume"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Aikon- on 2009-09-24
I have just noticed the following behaviour between MPD and my system volume: changing the MPD volume changes the system volume!

I was listening to a particularly long song, but wanted to stop and watch a TV episode instead. Since I don't like cutting off songs, I carefully faded out the music using the volume slider in Sonata, my MPD client of choice. When I went to watch the episode, I had no sound. It took me about 10 minutes to figure out that changing the sound in Sonata was changing my entire system volume.

Some more experimentation using Pitchfork (a web client for MPD) shows that it isn't just Sonata, but MPD itself that is affecting the system volume.

I have been using MPD for two years now, and I have never noticed this behaviour before.. If anyone has any ideas how to make the MPD volume separate from the system volume, I would be very grateful!

Cheers,
-Aikon

---

### Post by Nonno Bassotto on 2009-09-24
The last paragraph of [this]("http://mpd.wikia.com/wiki/PulseAudio") may be of help.

---

### Post by Aikon- on 2009-09-24
Wunderbar, thanks for the pointer, works great =) (except that MPD is having to do software mixing, but that should just be a stopgap until Karmic, which hopefully has 0.15.*).

Aikon-

---

