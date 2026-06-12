---
title: "GStreamer vs Xine"
date: 2009-04-02
forum: Multimedia Software
---

### Post by DPic on 2009-04-02
Although there have been threads in the past discussing this, they don't address which is conceptually superior and fail to really explain the difference between the two projects like scope, idology, and development process. Anybody know?

---

### Post by Melcar on 2009-04-03
Xine is a pain to work with on fglrx drivers and since my main desktop is GNOME, I stick with gstreamer.  While I find that both are able to play pretty much anything once the right plugins are in place, Xine sometimes displays artifacts with certain video files.  However, on my Kubuntu laptop I just stick with Xine (open source ati drivers).  I really have no preference; I simply use what works in a given system.

---

### Post by SunnyRabbiera on 2009-04-03
For me Xine works better, Gstreamer tends to be sloppy.

---

### Post by steeleyuk on 2009-04-03
Both has benefits which is why I use both.

Xine has better DVD menu support and allows you to skip through PUOs on DVDs. I have problems playing certain FLAC files back in Xine though.

Gstreamer is arguably a better framework, however DVD menu support is buggy at the moment.

---

### Post by DPic on 2009-04-03
> **steeleyuk said:**
> Gstreamer is arguably a better framework

aha, now this is what i am trying to get at. 

Why/how is it a better framework?

---

### Post by steeleyuk on 2009-04-03
I'm not a developer so this is my own personal opinion and observations but:

Modular - the Good, Bad and Ugly sets allow splitting of codecs based on license and code quality (not sure if Xine can do that due to how its structured)
Extensions - lots of extensions, you could easily load a Gstreamer module into python and quickly create a video playback app (as an example)
Backing - Intel and Nokia sponsorsed development which lead to the 10.x series. Fluendo is also a company heavily invested in Gstreamer development.

If there's any more than that, then I'm not the person to ask. :)

One issue I just spotted on Wikipedia to do with Xine:

> To prevent a screensaver from starting, xine sends a scroll lock key signal to the environment to pretend keyboard interaction took place. This can often lead to issues with other programs running as they receive the scroll lock key as normal input. One example is the Konsole terminal emulator, which changes the behaviour of the arrow keys when scroll lock is used.

---

