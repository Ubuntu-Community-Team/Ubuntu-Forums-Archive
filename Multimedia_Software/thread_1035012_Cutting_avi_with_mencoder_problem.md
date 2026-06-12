---
title: "Cutting avi with mencoder problem"
date: 2009-01-09
forum: Multimedia Software
---

### Post by anlag on 2009-01-09
Simply put, I want to cut an avi video clip (without sound) into shorter time, but am having some problems doing so with mencoder. I use the following:

$ mencoder -ss 00:00:20 -ovc copy 001hi.avi -o cut001.avi

This should cut off the first 20 seconds of the original clip, right? That clip (001hi.avi) is 1m33sec long, so I would expect the output to be 1m13sec. However, the output is only 1m08sec, and it also starts later than 20 seconds into the original clip.

It turns out even as I vary the 20 seconds input parameter, to 15 seconds, or 10, or 5, or even 25 seconds, the output is still always 1m08sec. However, if I tell it to cut the first 30 seconds out, the output is suddenly only 43 seconds long, that is, 50 seconds shorter than the input.

Why does mencoder only cut the file in chunks rather than exactly where I tell it to?

For reference:

MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team

---

