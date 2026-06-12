---
title: "Grabbing DVD clips"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by marksy1984 on 2007-08-16
Hello. I would like to be able to grab (2.5 minute) DVD clips from any DVD and convert them to a format I can use in presentations. 

On Windows XP I used a combination of DVD43, Handbrake, and MPEGStreamclip. 

Can anyone point me in the right direction to do the same in Ubuntu 7.04? 

Is there any alternative software?

---

### Post by kellemes on 2007-08-16
Maybe [Kino]("http://www.kinodv.org/") can do this?
But maybe not..

---

### Post by marksy1984 on 2007-08-17
Hi. I haven't installed Kino yet, but having read around, I don't think it'll do it. Thanks though, I will try it. Any others anyone?

---

### Post by heidfirst on 2007-08-17
It maybe possible to achieve this using acidrip and gopchop.

---

### Post by vanadium on 2007-08-17
You can do this with avidemux. 

* First rip the vob's to your hard disk. The easiest way is the command vobcopy. From a terminal, type

vobcopy -l

This will automatically rip the longest program on your DVD to one single VOB in the current directory.

* You can now open de VOB with avidemux. Avidemux is a graphical linear video editing utility (with lots of resemblance to Windows only Virtualdub). You can now delete the sections you do not want (non-destructively) and then copy the result to an output format of your choice, either with direct copy or transcode of video and/or audio.

---

