---
title: "[SOLVED] Question on Grip"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by slughappy1 on 2007-07-29
My question is, is there a way to change how Grip names the files it rips?  For example I just ripped a CD and the file name it gave me is glory_glory.mp3, but I would like the file to be named something like 1. Glory Glory.mp3 or close.  I want the files to be in track order NOT alphabetical.  In Grip, under the Config -> Encode - > Encoder tab, I have:

Encoder: lame
Encoder executable  /usr/bin/lame
Encoder command-line  -h -V 2 --vbr-new %w %m
Encoder file extension  mp3
Encoder file format ~/mp3s/%A/%d/%n.%x

Thanks in advance.

---

### Post by jynyl on 2007-07-30
Under Config > Encode > Encoder, in the "Encode file format" field, I use
 ~/mp3/%A/%d/%t%n.%x

which gives track number at the start of the filename.

HTH

Peter

---

