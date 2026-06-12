---
title: "Totem - subtitles"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by iBoniek on 2008-03-25
Hi

Is there any idea how to show subtitles lines which are changing in a short period of time. For now I have to wait about  seconds so it's a little frustrating.

---

### Post by erginemr on 2008-03-25
You may consider giving a try to totem-xine, totem with Xine backend (as compared to the default GStreamer backend) and while you are on it, GXine. From a terminal:
```
sudo aptitude install totem-xine
```
```
sudo aptitude install gxine
```
Totem-xine works better than totem-gstreamer in my computer, but if it you don't like the result (subtitle speed in your case), you may always revert to the original with:
```
sudo aptitude install totem-gstreamer
```
```
sudo aptitude remove gxine
```

You may also give a try to vlc:
```
sudo aptitude install vlc
```

---

### Post by iBoniek on 2008-03-25
Yes that helps a lot. but now I can't rewind my film smoothly. Is this just a matter of totem and it is better to change to different one like vlc?

---

### Post by erginemr on 2008-03-25
I'd say, if vlc works, go for it, because it has a well-deserved reputation among fellow Ubuntu users. GXine is also better than Totem-Xine in terms of responsiveness.

You can even try another legendary video player, **mplayer **with:
```
sudo aptitude install mplayer
```

---

