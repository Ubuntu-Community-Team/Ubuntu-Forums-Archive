---
title: "trying to capture VHS tape"
date: 2013-11-26
forum: Multimedia Software
---

### Post by squakie on 2013-11-26
I have a Dazzle DVC-100 that seems to be working with the following command:

```
mplayer -tv  driver=v4l2:width=720:norm=NTSC:audiorate=48000:immediatemode=0:forceaudio:alsa:adevice=hw.2,0:device=/dev/video0:input=0  -vf pp=lb tv://
```

I found this [in this threa]("http://forums.linuxmint.com/viewtopic.php?f=42&t=123022")d.

I'm having a problem though, and since I don't know anything about this "stuff", I'm hoping some can help:

I hear the sound, but the video is just "noise" bars that fluctuate with the sound.  I have no idea what to do.  Do I need to add something so the the "capture" frame rate is like a VHS tape - 29.x I think.

Also, when this playback portion works, how do I save it to a file of hopefully type mp4?

---

### Post by squakie on 2013-11-28
Guess nobody must know about this either.

---

