---
title: "Wikipedia slows audio down"
date: 2009-01-25
forum: Multimedia Software
---

### Post by k@e on 2009-01-25
Firstly, I have PulseAudio disabled and replaced by esound. My sound card is a Creative Labs Sound Blaster Live! 24-bit.

Whenever I try to play a multimedia file in Wikipedia, I hear nothing. If you too don't use PulseAudio, try it if it works for you. Example:

[http://en.wikipedia.org/wiki/Violin_Sonata_No._9_(Beethoven](http://en.wikipedia.org/wiki/Violin_Sonata_No._9_(Beethoven))

Now, this wouldn't be a serious problem if trying to play a file on Wikipedia didn't slow down the audio of the entire system. **Every** sound is played with half the original speed, basically a reverse chipmunk effect. Why is that? Anybody else having the same problem? Is there a fix for this?

If you try it and encounter the same problem, here is a workaround to get sound back to normal speed without having to restart your computer:

```
killall esd
esd
```

Thanks for replies!

---

### Post by k@e on 2009-01-26
This needs more attention.

---

