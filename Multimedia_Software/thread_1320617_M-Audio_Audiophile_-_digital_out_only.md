---
title: "M-Audio Audiophile - digital out only?"
date: 2009-11-09
forum: Multimedia Software
---

### Post by v0idnull on 2009-11-09
I have an M-Audio Audiophile, it worked in Ubuntu 9.04. Upgraded to 9.10 and it doesn't work.

I installed pulse audio volume control and clearly see a signal. However, I notice that various settings all over the place state that it's using Digital Stereo for an output, which I presume to be spdif. I have nothing to plug spdif into right now, so how do I get my analog outputs back?

:(

---

### Post by v0idnull on 2009-11-09
I solved my problems using the fix listed here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7)

A few more notes:

Removing auto-detection I commented out:
```

load-module module-udev-detect

```
and
```

load-module module-detect

```

Then I killed pulse audio:

```

$ sudo killall pulseaudio

```

Hope this helps others...

---

