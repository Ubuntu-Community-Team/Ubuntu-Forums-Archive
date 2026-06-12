---
title: "No sound in flash player. Possible solution..."
date: 2008-12-29
forum: Multimedia Software
---

### Post by Kaze_no_Hibiki on 2008-12-29
I wasn't able to hear anything Flash player today (I just built my new computer, and installed Intrepid on it.)
A quick Google searched showed that I apparently was not the only one.
After trying many, MANY, different supposed fixes, one of the sites mentioned it might have something to do with Pulseaudio.
So a quick
```
sudo apt-get remove pulseaudio
```
Followed by a system restart, and there was sound.

So, I suppose if your having the same problem, try it.
And I am a bit of a noob, so, forgive me for asking, but what exactly is the purpose of pulseaudio? :-s

---

