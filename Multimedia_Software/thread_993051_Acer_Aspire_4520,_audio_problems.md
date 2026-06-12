---
title: "Acer Aspire 4520, audio problems"
date: 2008-11-25
forum: Multimedia Software
---

### Post by Shagg on 2008-11-25
Hi everyone:

Here I was, using my faithful Acer Aspire 4520 notebook, when suddenly, the printer and the mouse stopped working (both are usb devices). I was in a REAL hurry, so I turned off the computer &#8220;the hard way&#8221; (by pressing the power key). When I booted Ubuntu back, sound was dead!

Now, using the comprehensive sound problem solution guide, I managed to get sound back to life, but it is not working properly, i.e., if in preferences I choose to test &#8220;Alsa Digital&#8221;, it doesn't sound at all, and if I try to test &#8220;Alsa Analog&#8221;, the following error is shown:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink:Could not open audio device for playback
```

For the record, audio used to work out of the box.

So, the thing is: should I just re-install ubuntu, even when I already got the alsa drivers from a fresh kernel, according to the comprehensive sound problem solution guide? Will I lose my entire configuration (video, wireless, etc.) in the process?

And, how did this happened in the first place? All because a bad turn off?

Well, thanks for reading this and hope someone out there can give me a hand. Oh, and if you need to know anything else, feel free to ask (is just that I'm really lost here so wouldn't know where to start).

Edit: I'm on 32bits Intrepid.

---

