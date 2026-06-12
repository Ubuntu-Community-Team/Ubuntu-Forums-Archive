---
title: "Music playback command line"
date: 2011-12-23
forum: Multimedia Software
---

### Post by B-2-10 on 2011-12-23
I'm really loving clementine music player, it seems to be the only one that I've found that actually deals with multiple-artist-albums... But I digress!

I want to have an alarm clock on my laptop using a music player - but clementine doesn't have an alarm clock plugin. I've used sentinella before now to schedule music players in alarm-clocking, but because they had a "start playback on startup" option.
Is there a way to input a command to sentinella (essentially just one that would work from a terminal) that would start playback immediately?
Something like ```
clementine --playback
``` perhaps?

---

### Post by nothingspecial on 2011-12-23
I'm pretty sure that clementine uses mpris

[http://www.mpris.org/2.1/spec/](http://www.mpris.org/2.1/spec/)

So command line playback should be possible. I have no experience whatsoever with clementine but guayadeque, which also uses mpris can be started like this

```
dbus-send --print-reply --type=method_call dest=org.mpris.guayadeque /Player org.freedesktop.MediaPlayer.Play
```

It should be similar.

---

