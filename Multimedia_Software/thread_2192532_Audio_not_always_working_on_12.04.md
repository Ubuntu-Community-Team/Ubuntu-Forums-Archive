---
title: "Audio not always working on 12.04"
date: 2013-12-08
forum: Multimedia Software
---

### Post by magnus07 on 2013-12-08
I've had an random issues on a 12.04 64bit on Thinkpad T410.

After a couple of years of audio working I've experienced the following issues:
1) speakerphones not working while earphones are
2) Totem not working while Rhythmbox working

I've tried at least 5 possible solutions messing up configurations and bios settings but only the following one solved my problems:
[http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html)

In short it basically disables libgstvideoparsersbad.so and works for both 32 and 64 bits versions.
Don't know what libgstvideoparsersbad.so does but this solves.
I've also checked that it's supposed to be fixed but at least for me it wasn't.

Just wished to share.

---

