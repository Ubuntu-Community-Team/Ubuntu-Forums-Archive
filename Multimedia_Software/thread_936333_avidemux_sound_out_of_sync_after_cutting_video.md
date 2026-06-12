---
title: "avidemux sound out of sync after cutting video"
date: 2008-10-02
forum: Multimedia Software
---

### Post by sdowney717 on 2008-10-02
for some reason, the sound is totally way out of sync when I cut out video.
When I cut out a section of video and save it, it is totally out of sync

I just also discovered it is out of sync if I just load it and play it.

any ideas?

---

### Post by xc3RnbFO8P on 2008-10-02
Did you try to** rebuild frames** in tools before you cut the video?
You can also use [Devede]("http://www.getdeb.net/app/DeVeDe") to rebuild frames.

---

### Post by sdowney717 on 2008-10-02
ok, just tried it and still out of sync. This is a movie trailer off a dvd.
It is a .VOB file

Ok, load file into VLC, sound is in sync.
load file into avidemux, sound is delayed by several seconds

I actually thought it was avidemux when editing the file, but it is out of sync when just loaded and played.

---

### Post by mirko_3 on 2009-04-02
Ever figured it out? I have the same problem, loading a .VOB

---

### Post by lee321987 on 2010-08-16
I looked everywhere for this and had a hard time finding it, so I'm posting the answer here:

>       Some DVDs are coded as 23.976 aka FILM (most movies actually). Some others are coded as 29.96 (NSTC), soap for example. In the first case, the DVD player does an operation to convert it on the fly to NSTC format (telecine). So the MPEG header always says 29.96 as it will always be the final format.

      Avidemux uses mpeg2dec to decode MPEG streams (with a little patch). mpeg2dec does not do the telecine on FILM movies (and that's better that way).

      It means that Avidemux cannot tell the difference between FILM and NSTC. So if the MPEG looks progressive (not interlaced) and obvious desync appears (and gets worse and worse), use Video->Frame Rate and set it to 23.976.

      For PAL MPEG, there is no problem, it is always 25 fps.
Source:  [http://avidemux.berlios.de/doc/en/dvd2mp4.xml.html](http://avidemux.berlios.de/doc/en/dvd2mp4.xml.html)

Sorry for posting in such an old thread.

---

### Post by rogerdpack on 2011-05-16
Confirmed other fella's fix (have the same issue on windows, too).  Going to  Video menu -> frame rate, select "FILM - 24 FPS" from the drop down box and it seems to fix it well, instead of it being about 10 minutes out of sync (audio from the video).

Thanks!

Unfortunately this only gets it "pretty" close since with some (most?) VOB files the frame rate sometimes shifts temporarily to 30fps and then back to 24, and so avidemux (doesn't handle this) gets out of sync, but it's closer :)

ref: [http://www.fedoraforum.org/forum/archive/index.php/t-155783.html](http://www.fedoraforum.org/forum/archive/index.php/t-155783.html)

---

