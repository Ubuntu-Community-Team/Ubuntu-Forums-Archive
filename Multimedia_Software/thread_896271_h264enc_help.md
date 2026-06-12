---
title: "h264enc help"
date: 2008-08-21
forum: Multimedia Software
---

### Post by monoprotic on 2008-08-21
I'm attempting to encode a video using h264enc, but I only want to encode specific chapters. I looked all over, but I don't see where I'm supposed to specify what chapters I want, since the h264enc script doesn't ask which. I looked at the FAQ, which mentions encoding specific chapters, but it doesn't say how (which is frustrating).

Any help here is greatly appreciated!! Thank you!

---

### Post by elektronaut on 2009-07-24
A bit late, but maybe this helps the next person googling...

I don't know either how to specify a certain chapter in h264enc, what I have done so far is merging the vob files for a certain part of the DVD ('cat VTS_0x_01.VOB VTS_0x_02.VOB ... > one_big.vob') and then running h264enc on that vob file. 

But if you only want to have a certain chapter, I would try and cut it out and save it as a single vob.

---

