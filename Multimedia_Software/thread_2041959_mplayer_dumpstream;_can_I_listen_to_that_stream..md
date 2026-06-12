---
title: "mplayer dumpstream; can I listen to that stream."
date: 2012-08-13
forum: Multimedia Software
---

### Post by ajgreeny on 2012-08-13
I use ```
/usr/bin/mplayer -cache 2048 -playlist http://bbc.co.uk/radio/listen/live/r3.asx -vc null -vo null -ao pcm:fast:waveheader:file=/home/andrew/Radio/$(date +%F_%H-%M)-BBCR3.wav
``` to record broadcast concerts on BBC Radio 3. 

Can I listen in to that stream at the same time by using a localhost address as I can with streamripper ```
gnome-mplayer http://localhost:8000
``` to avoid two concurrent streams of the same thing

I can not find the mplayer localhost port to use, so any help would be very welcome.

---

### Post by ads52 on 2012-08-13
I am probably missing your point completely but can you not simply open another MPlayer process and listen to the */home/andrew/Radio/$(date +%F_%H-%M)-BBCR3.wav* file as it is downloading?

I am curious to know also if the option *-bandwidth 1000000* makes downloading the stream itself any easier...

---

### Post by ajgreeny on 2012-08-14
> **ads52 said:**
> I am probably missing your point completely but can you not simply open another MPlayer process and listen to the */home/andrew/Radio/$(date +%F_%H-%M)-BBCR3.wav* file as it is downloading?

I am curious to know also if the option *-bandwidth 1000000* makes downloading the stream itself any easier...
Yes, I can open the .wav file with a media player, but for some reason it will not play the whole of the file as it grows; only the amount that was downloaded at the time I start playing it.  Maybe that can be changed in some way, but I am not sure.

I can also run gnome-mplayer or anything else to listen to streasm and listen live to the same broadcast, but this was really a question about if it is possible just to listen in to the mplayer stream that is already streaming.  It is not really a bandwidth problem, or anything like that, but simply that I can listen to streamripper as it records on localhost:8000, so I wondered if it's possible to do the same using mplayer.

---

