---
title: "Pausing Totem in Lucid = black screen"
date: 2010-04-21
forum: Multimedia Software
---

### Post by ed-koala on 2010-04-21
Has anyone else run into this?  If I pause a video in Lucid's Totem, the video shows a black screen, not a frozen frame of the video as in 9.10.

It's not a big deal to me, but I guess it's another small bug. I did a bug search but didn't see it, but I may have been looking in the wrong place.


Edit - Never mind, this is a known bug and is being worked on.

---

### Post by blankego on 2010-04-29
Yeah, I've experienced the same thing. It seems like Totem cannot refresh its screen, whenever it's toggled between fullscreen or window modes, or got paused, and so on, it got a black screen, and in the full-screen mode, after the slide-bar faded out, a black bar appeared on the bottom edge. If any other window got overlapped over Totem's screen, it also would leave a black area...:mad:

---

### Post by n.hinton on 2010-04-30
Yes, same here too. Using VLC for time being.

---

### Post by mirko_3 on 2010-05-05
experiencing the same problem, it's annoying

---

### Post by n.hinton on 2010-05-05
P.S. to post 3

Curious thing, ran totem as:```
totem --debug
``` to see if any clues, but totem behaved in debug.

---

### Post by zsenike on 2010-05-07
Hy,
I think I have the same problem with extras :( After the first login I don't have image with totem. Just audio. I have to log out and back in for video. But the black/blank screen in paused mode is still remains. It's a bit unpleasent :(

... waiting for solution

---

### Post by n.hinton on 2010-05-07
The following workaround was posted by mprince in another thread:> Press Alt+F2 and run "gstreamer-properties"-- on the video tab, change the default output plugin to "X Window System (No Xv)."

---

### Post by AlexDudko on 2010-05-07
Doesn't help, but activating one of drop-down menus makes video visible in my case.

---

### Post by n.hinton on 2010-05-07
> **AlexDudko said:**
> Doesn't help, but activating one of drop-down menus makes video visible in my case. and I bet fullscreen plays too.

Think it must be a totem issue, piping to gstreamer e.g.```
gst-launch playbin2 uri=http://www.redhat.com/v/ogg/TruthHappensRmx.ogg
```seems to work fine.

---

### Post by n.hinton on 2010-05-09
Latest update in lucid has fixed totem

---

