---
title: "encode in v0 with soundjuicer"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by holdie on 2008-02-28
Hey I'm having some trouble getting my CD's to rip to v0 with soundjuicer...I've tried a few different pipelines and they all either default down to a CBR of 128 or 192...I'm not sure what I'm doing wrong here, but what do you guys use to encode in v0

thanks

---

### Post by holdie on 2008-02-28
Correction: I found the following pipeline

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=0

Which I've found will encode VBR...however, the average bitrate is only around 160 or so, which I find to be pretty low for a v0 file...any suggestions/obvious problems with my code?

---

