---
title: "Strange Audio Problem"
date: 2008-12-28
forum: Multimedia Software
---

### Post by jlr4u on 2008-12-28
I've been trying to get audio recording working. The problem is recording from an old happauge 150 card. What I discovered is that after a fresh reboot, If I first played an AVI file, then recordings will work. The code that I use to test a recording is.```
cat /dev/vide0 > /tmp/test_capture.mpg
``` and I am using VLC to verify it recorded.```
vlc /tmp/test_capture.mpg
```

The problem appears to be that the audio in an mpg file is not being recorded when I do a fresh re-boot and don't play an avi file for a few seconds before attempting to record.

Strange Problem:confused:

---

