---
title: "Video Won't Show in Totem"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by WaeV on 2007-05-23
Hey I have an ATI All-in-Wonder 9800 Pro running beryl and ubuntu feisty with the ubuntu studio packages installed manually.  Recently however, videos have stopped showing up in Totem.  

When I listen to music, the screen is black but at the very end of the song I see a flash of the color effects.  Sometimes I see flashes of the movie when the Totem screen is moved around.  I can still watch flash stuff like YouTube however.  What is the problem?:confused:

---

### Post by ronocdh on 2007-05-23
> **WaeV said:**
> Hey I have an ATI All-in-Wonder 9800 Pro running beryl and ubuntu feisty with the ubuntu studio packages installed manually.  Recently however, videos have stopped showing up in Totem.  

When I listen to music, the screen is black but at the very end of the song I see a flash of the color effects.  Sometimes I see flashes of the movie when the Totem screen is moved around.  I can still watch flash stuff like YouTube however.  What is the problem?:confused:
I just came across [this post]("http://ubuntuforums.org/showthread.php?t=452618") in Desktop Config. I don't know whether it'll help you, but perhaps it's a start? 

If you've added Studio packages, perhaps it's a codec error? Try playing the same video files in a fresh install of VLC (--purge remove beforehand) and see whether that works.

---

### Post by WaeV on 2007-05-23
Yes that worked thank you.

I had to change the gstreamer settings to no Xv.

---

