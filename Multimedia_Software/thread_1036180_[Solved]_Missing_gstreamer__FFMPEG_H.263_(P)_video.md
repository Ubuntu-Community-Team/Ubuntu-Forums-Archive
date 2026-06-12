---
title: "[Solved] Missing gstreamer / FFMPEG H.263 (P) video encoder"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Dksaarth on 2009-01-10
Hi Guys

Just thought I'd leave a note here for anybody who is perhaps having some ffmpeg difficulties. I need to use the gstreamer element ffenc_h263p for some of my research, and noticed that on some of our lab pcs that it could not be found.

```
gst-inspect-0.10 | grep h263p
```
 This in turn led me to discover that ffmpeg did not support h263p in its current status on those machines.

```
ffmpeg -formats | grep h263
```
I couldn't find anything about this by searching the internet for clues regarding ffmpeg and h263, but managed to solve it after a while.

It can be solved by

```
 sudo aptitude install libavcodec-unstripped-51
```
Hope that helps some one in the future.

---

### Post by sandbar on 2009-08-01
Newb level answer needed.

I tried this fix and it couldn't install because libvacodec-unstripped-51 couldn't be found. Now what?

THX

---

### Post by Dksaarth on 2009-08-02
Hi

I think there is a new version - Try

```
 sudo aptitude install libavcodec-unstripped-52 
```

Hope that helps :)

---

### Post by HappyFeet on 2009-08-02
> **sandbar said:**
> Newb level answer needed.

I tried this fix and it couldn't install because libvacodec-unstripped-51 couldn't be found. Now what?

THX

Did you install the medibuntu repos?

---

### Post by michaelayland on 2010-01-29
Thank you for this valued information  Using Remix and trying two quicktime movies it refused to play but after your command line we were away.  Wonderful Thank you for your information  Best Regards mike a

---

