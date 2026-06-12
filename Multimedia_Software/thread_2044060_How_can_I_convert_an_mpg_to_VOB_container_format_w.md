---
title: "How can I convert an mpg to VOB container format without transcoding?"
date: 2012-08-18
forum: Multimedia Software
---

### Post by sir_robert007 on 2012-08-18
What I wanna do is simply take the video from the mpg and repackage it into a DVD compliant VOB without transcoding. I use DVD Styler to make my DVD's so is there any options I can use to convert to VOB? I also hear Handbrake is also capable of this also.

How can I use DVD Styler or Handbrake to repackage into the VOB container format. Any other tools I should be aware of?

---

### Post by veroslav on 2012-08-18
I would probably use AviDemux and set the outputs to the following:

Video: Copy
Audio: Copy
Format: MPEG-PS

This is how I normally do it when I want to export a VOB after editing.

If all you want is to make a DVD from your MPEG, you could use DeVeDe and while adding the MPEG (under Advanced options-Misc), select "This file is already a DVD/xCD-suitable MPEG-PS file"

---

### Post by qyot27 on 2012-08-18
I suspect the real issue is the lack of NAV packets in the MPEG-2 file, not the container (as VOB is not all that distanced from MPEG-PS to start with, but VOBs have NAV packets).

This can be done easily when muxing the constituent .m2v and .ac3 (or .mp2) streams together with mplex (from the mjpegtools package):
```
mplex -f8 -V input.m2v input.ac3 -o output.mpg
```
The -f8 parameter tells it to use NAV packets.

---

