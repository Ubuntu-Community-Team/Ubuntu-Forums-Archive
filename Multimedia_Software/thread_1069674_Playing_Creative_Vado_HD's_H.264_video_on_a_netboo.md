---
title: "Playing Creative Vado HD's H.264 video on a netbook"
date: 2009-02-14
forum: Multimedia Software
---

### Post by talmage on 2009-02-14
Please help me figure out why the videos I make on my new [Creative Vado HD camera]("http://us.creative.com/products/product.asp?category=833&subcategory=834&product=18108&listby=") don't play on my Asus EEE PC 1000.  I'm running Ubuntu 8.10 with all the available updates.

The output of the Vado HD is 1280x720 30fps H.264.  Instead of smooth video with synchronised audio, I get one or two frames plus audio (w/totem and VLC) or I get nearly smooth video with unsynchronised audio (w/mplayer).  I find this strange because my netbook plays 1280x720 25fps H.264 videos perfectly.  Are those extra frames-per-second significant?

I've been able to make mplayer play the Vado HD's videos by using the command line options

```
-lavdopts fast:threads=2:skiploopfilter=all
```

The video output then is OK but not great.  Mplayer plays all of my other videos without any tweaking, so why should it need that for these new videos?  And why won't the other players play them?

---

### Post by talmage on 2009-02-16
I found an answer for VLC in ["How to get better performance when playing HD H.264"]("http://forum.videolan.org/viewtopic.php?f=2&t=42328").

Still looking for the answers for totem and mplayer.

---

