---
title: "mplayer, ladspa &amp; 2X playback"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by drs305 on 2007-10-16
I am trying to find a linux-based program to play mp3s at 2X speed. I came across this command but can't get it to work:

```
mplayer -speed 1.5 -af ladspa=tap_pitch:tap_pitch:0:-33:-90:0 filename.mp3
```

(from: [http://mark.santaniello.com/archives/260](http://mark.santaniello.com/archives/260) )

I used synaptic to install mplayer, ladspa-sdk and tap-plugins. I didn't find a straight ladspa entry in synaptic. I don't really know how to configure mplayer to add the plugins necessary, but in any case when I use the above command it doesn't work. It was originally for an .avi file and perhaps it won't work on an mp3 file (I don't know).

When I run the above command, I get:
```
ladspa: (tap_pitch:tap_pitch): failed to load tap_pitch
        tap_pitch: cannot open shared object file: No such file or directory
[libaf] Couldn't create or open audio filter 'ladspa'
Error at audio filter chain pre-init!
Exiting... (Fatal error)

```

So what do I have to do to load tap_pitch and get ladspa to open. Or even easier, how do I get mp3's to play at 2X  :grin:

Thanks for the replies.

---

### Post by Matt05 on 2008-05-18
It works with the full path for the library:

```

mplayer -speed 1.5 -af ladspa=/usr/lib/ladspa/tap_pitch.so:tap_pitch:0:-33:-90:0 podcast.mp3

```

---

### Post by drs305 on 2008-05-19
thanks matt05. it appears you are playing it from a file on your computer. i'm trying to get it to play off the internet feed. i'll give the commands a look and see if they translate to that mode.

---

