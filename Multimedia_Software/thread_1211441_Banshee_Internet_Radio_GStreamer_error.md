---
title: "Banshee Internet Radio GStreamer error?"
date: 2009-07-12
forum: Multimedia Software
---

### Post by rfLarke on 2009-07-12
Hey guys, just got Banshee a few weeks ago and am loving it. Eventually I decided to try out some of the Last.fm features, but ran into some issues. 

Whenever I try to play the songs it gives me, it simply won't play. Running from terminal, I get an error stating "[FONT="Courier New"]**GStreamer resource error: NotFound**[/FONT]". I get the same error connecting to any streaming Internet Radio, be it Last.FM, podcasts, anything.

I don't have any other problems with this on any local content, just streaming stuff. As far as I know, all GStreamer codecs are installed, unless I need to do something beyond the stuff that installs itself.

I've done a bunch of Google searching on this stuff but I can't seem to find anything that helps, so any assistance on this issue is appreciated.

---

### Post by igorzwx on 2009-07-12
It seems that they fix Pulse every day.
Every day you have some new problems.

---

### Post by rfLarke on 2009-07-12
...Er

Pardon?

---

### Post by igorzwx on 2009-07-12
Do you have PulseAudio?

---

### Post by rfLarke on 2009-07-12
According to Synaptic, apparently I do.

---

### Post by igorzwx on 2009-07-12
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by monraaf on 2009-07-12
Does this work for you?

```

gst-launch-0.10 souphttpsrc location=http://scfire-mtc-aa03.stream.aol.com/stream/1065 ! decodebin ! audioconvert ! alsasink

```

---

### Post by rfLarke on 2009-07-12
Monraaf: Yeah, it works fine

---

### Post by monraaf on 2009-07-12
Now if you create a new radio station in Banshee with the same url:

[http://scfire-mtc-aa03.stream.aol.com/stream/1065](http://scfire-mtc-aa03.stream.aol.com/stream/1065)

does it work?

---

### Post by rfLarke on 2009-07-12
Huh.. Yes it does, very well. Maybe I was mistaken about the Streaming Radio thing, though I'm having a hard time finding any other stations to test with

---

### Post by monraaf on 2009-07-12
It appears last.fm playback is currently broken in Banshee:

[http://osdir.com/ml/banshee-list/2009-07/msg00026.html](http://osdir.com/ml/banshee-list/2009-07/msg00026.html)

Normal internet radio stations should work fine though.

---

