---
title: "mplayer tells me https protocol not found"
date: 2016-07-25
forum: Multimedia Software
---

### Post by NathanJoSharp on 2016-07-25
I'm trying to stream youtube videos through mplayer using cookie files. I'm following this tutorial.
[https://www.youtube.com/watch?v=QCuq0_nY3Xk](https://www.youtube.com/watch?v=QCuq0_nY3Xk)

```
mplayer -fs -cookies -cookies-file /tmp/cookie.txt$(youtube-dl -g --cookies /tmp/cookie.txt "https://www.youtube.com/watch?v=QCuq0_nY3Xk")

```

When I try to stream the video, I get this in the output. ```
https protocol not found, recompile FFmpeg with openssl, gnutls,
or securetransport enabled.
Failed to open
```

It didn't seem like a big deal, so I recompiled ffmpeg with openssl.
However, after this was all said and done, I got the same error message.

I even checked ```
ffmpeg -protocols
``` and it listed openssl and https as being active, but when I try to run an https address in mplayer it tells me that it can't find that protocol.

---

### Post by mc4man on 2016-07-26
mplayer either uses it's own internal ffmpeg or in the case of 16.04's version it uses the system shared ffmpeg libs.
In the later case https is working, in the former mplayer needs to be build with support. (gnutls should be fine

Edit: don't see where this works anymore (from yt), just get audio, no video. another method with curl produces video but no audio
mpv is better choice, i.e. it works simply from url

---

