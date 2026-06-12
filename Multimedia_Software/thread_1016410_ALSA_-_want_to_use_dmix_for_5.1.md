---
title: "ALSA - want to use dmix for 5.1"
date: 2008-12-19
forum: Multimedia Software
---

### Post by Cracauer on 2008-12-19
I use dmix for stereo just fine. But when there's a video playing 5.1, the hardware device becomes busy.

I've been told to up-mix stereo to 5.1 and then play everything as 5.1.

This snipset does the upmix:
```

pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}

```

But I can't figure out how to put the "surround51" pcm on top of dmix.

How does dmix know how many channels there are?

---

