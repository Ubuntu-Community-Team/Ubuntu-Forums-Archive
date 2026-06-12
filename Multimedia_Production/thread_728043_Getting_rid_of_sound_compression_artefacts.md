---
title: "Getting rid of sound compression artefacts"
date: 2008-03-18
forum: Multimedia Production
---

### Post by EtienneG on 2008-03-18
Hello everybody,

I have ripped a bunch of talk radio from a Windows Media stream (mms://...wma, .wmv) to .wav using "mplayer -ao pcm:file=blah.wav".  Worked beautifully, except that the ripped sound files have an annoying artefact.  It is hard to describe, but it is like a slightly metallic echo.  It is pretty subtle, but it is not totally unlike the robot-like sound of voice synthetizer from the 80s.

I wonder if there is something I can do to get rid of that artefact.  I am not experienced at all in sound processing, but if someone have suggestion of effect/filter I could try, it would be awesome.  Using Audacity is ok, but I would rather use sox or something similar if at all possible to process all my rip in batch.

All suggestion welcome.  Thanks a lot!

EtienneG

---

### Post by kostkon on 2008-03-18
I think this is caused by the low quality (low bitrate and frequency) of your media. So, I don't know if you can do something about it.

Streaming media tend to have very low quality.

---

### Post by EtienneG on 2008-03-18
I think I need something like unsharp mask, but for sound.  Any suggestion would be appreciated, as the sox man page make me dizzy.

---

### Post by EtienneG on 2008-03-20
Talking about mask, the sox mask effect seems to do good:

    ```
sox -v 1.5 in.wav out.wav mask
```


The volume boost and added noise make the voice metallic buzz harder to notice.

---

