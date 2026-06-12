---
title: "Acidrip Filesize output"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by protorox on 2008-04-12
I'm having a problem with Acidrip..

When I specify the filesize for my xvid output file (700mb), it keep outputing a file of 526mb.

Any ideas?

---

### Post by K.Mandla on 2008-04-12
Moderation bump.

---

### Post by chewearn on 2008-04-12
I don't use Acidrip, so I don't know if my reply will be useful.  What I usually use for encoding is Avidemux.  When specifying final filesize output, you have to specify other processing elements first.  These elements are e.g. video frame resizing and cropping, deinterlacing, and audio encoding options.

Why are these needed?

You need to resize the frame because e.g. DVD mpeg2 is not 1:1 pixel ratio while the Xvid is.  To avoid tall skinny people in your video, you need to change from e.g. 16:9 / 720x480 of the DVD frame, to e.g. 16:9 / 720x384 of the Xvid frame.  You have to take into account that the pixel dimensions are divisible by 16 for optimal encoding.

Further, some videos are larger than 16:9, but hardcoded with letterbox (this is a requirement of the DVD standards).  When converting, you want to remove the letterbox, which mean cropping.

The subject is quite involved; I suggest you head to [www.doom9.org]("http://www.doom9.org") and read the tutorials if you want to understand more.

You also need to specify the audio encoding prior to the final filesize.  E.g. if you are using MP3, a CBR encoding is recommended, because it gives a constant bitrate.

Lastly, to address the original question, why are you getting incorrect filesize?  Basically, the bitrate calculation could be erroneous when you specify the filesize first, then add in other processing.  It failed to take into account the other factors.

---

### Post by pkkid on 2008-05-12
Im getting the same issues?  Anyone figure this out?

---

