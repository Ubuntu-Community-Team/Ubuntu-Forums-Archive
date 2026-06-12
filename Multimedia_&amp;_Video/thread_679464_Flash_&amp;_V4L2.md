---
title: "Flash &amp; V4L2"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by OrionFyre on 2008-01-27
For a while i've been finalizing the last bits of my laptop and tweaking everything. Everything is great except for what I feel is one helluva deal breaker. Which is unfortunate because i have come to love this Ubuntu install.

I have the dreaded 1839 Ricoh webcam.
lsusb:
```
 05ca:1839 Ricoh Co., Ltd
```

I've gotten the poor junker to work OK, i still don't have control over the settings like brightness and hue and contrast, but hey. I can use it in chat programs like aMSN and Cheese and even xawtv all well and good.

My deal breaker however is with Flash. Apparently Flash is not compatible with V4L2.

I have no idea what I'm asking here other than for my next step, I'd like to continue ot use Ubuntu Linux, but unless I can resolve this problem, Vista is comming back (however regretfully)

*kneels down and prays to the Ubuntu Forum Gods*

---

### Post by Dooglus on 2008-04-19
I had the same problem.

My webcam is V4L2.  Flash only supports V4L(1).

I worked around the problem following this:

  [http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

Now I can use my webcam on flash sites.  Yay!

---

