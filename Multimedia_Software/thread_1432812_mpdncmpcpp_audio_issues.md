---
title: "mpd/ncmpcpp audio issues"
date: 2010-03-18
forum: Multimedia Software
---

### Post by diethylamine on 2010-03-18
I'm currently running 9.04, and got mpd/ncmpcpp to work.  However, the problem is that I can't seem to have mpd playing nicely with anything else that ones to play audio - whenever I get mpd/ncmpcpp to play music, I can't play music in Firefox, for example.  And if I restart my computer, then I can play music through other audio players (rhythmbox, exaile) and firefox, but then no output comes from mpd even though it claims to be playing a file. 

I've attached my mpd.conf - anyone have any idea what's up with this?

Thanks!

---

### Post by mcduck on 2010-03-18
You could try setting MPD to use PulseAudio instead of ALSA:

```
audio_output {
        type    "pulse"
        name    "MPD PulseAudio Output"
        #server  "localhost"   # optional
        #sink    "alsa_output" # optional
}
```
[http://mpd.wikia.com/wiki/PulseAudio]("http://mpd.wikia.com/wiki/PulseAudio")

It might also help to set some mixer type, if nothing else then enable the software mixer.

---

