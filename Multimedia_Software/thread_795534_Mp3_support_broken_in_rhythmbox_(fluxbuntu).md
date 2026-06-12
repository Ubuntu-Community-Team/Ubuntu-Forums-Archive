---
title: "Mp3 support broken in rhythmbox (fluxbuntu)"
date: 2008-05-15
forum: Multimedia Software
---

### Post by fINTiP on 2008-05-15
My rhythmbox stopped playing MP3's. :\

```
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
```

That's what I see, (repeated 3 times as it tries multiple times, I assume), in the terminal where I opened rhythmbox.

What broke? I remember at some point a while ago I installed something with Aptitude in the terminal, and it started uninstalling a bunch of stuff. I didn't know what to do, and figured the damage would be cleaner if I just let it do what it did then try and cancel in the middle...

It wasn't an install related to anything multimedia, so I don't know why it did that.

NOTES-

-I *did* do a google, didn't see anything that could help.
-Rhythmbox *does* still play ogg's.
-I went and tried to install the meta package with all the gstreamer libraries, and restarted rhythmbox, and that didn't do anything for me. :\
-I am using Edgy

So, 

1. How do I get it to play Mp3's again?
2. Why did aptitude do this, and how can I stop it from doing this in the future? [assuming the brokeness came from aptitude]

Thank you kindly.

.L

---

### Post by fINTiP on 2008-05-15
I don't know exactly what the problem was, but I eventually succumbed to actually opening up Synaptic instead of just using the terminal, and installed a few things that looked potentially useful, mostly gstreamer codecs (ugly wasn't installed, I think), and a few other small things.

I would still like to know why aptitude went stupid on me and deleted stuff. :\

.L

---

