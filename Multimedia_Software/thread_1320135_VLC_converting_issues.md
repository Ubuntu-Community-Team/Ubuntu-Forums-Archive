---
title: "VLC converting issues"
date: 2009-11-08
forum: Multimedia Software
---

### Post by newb85 on 2009-11-08
I'm having issues converting audio files using VLC.  For some reason, the output files are empty files.  I would like to resolve this problem without switching to a different program if possible, because I really like how versatile it is (or should be).  I would like to avoid having a program for watching videos, a program for ripping CDs, a program for listening to audio, etc.

---

### Post by newb85 on 2009-12-30
Turns out I simply needed to install the unstripped codecs package.  :lol:

---

### Post by HappyFeet on 2009-12-31
I searched for unstripped codecs and found nothing. What is the name of the package?

---

### Post by newb85 on 2009-12-31
It's called libavcodec-unstripped-52".  I think it's in the medibuntu repository.  (I installed it through synaptic.)

Edit:  Apparently, in Karmic, it's now called libavcodec-extra-52, instead.  If you installed the "unstripped" version in jaunty or earlier, upgrading to Karmic should automatically add the "extra" version--at least, it did for me.

---

