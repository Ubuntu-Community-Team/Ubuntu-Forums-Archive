---
title: "Delete Rhythmbox Album Art"
date: 2011-04-29
forum: Multimedia Software
---

### Post by WannabeFantasma on 2011-04-29
Hi all

I use my ubuntu machine as a media player, and I'm using Rhythmbox for music.

I still rip my cd's in Windows so when I get them to Linux I delete the cover art in the CD's map since I don't really care about the "coolness" factor :D.

Anyway, on some of the cd's there is still an album cover,(most of them downloaded from Jamendo) but searching ".jpg" in the music folder doesn't show the cover art.

Is there any place where Rhythmbox stores the Album art so I can delete it?

I'm using Ubuntu 10.04.

---

### Post by linuxyogi on 2011-04-29
Install **easytag**. 

AFAIK it can do that.

---

### Post by WannabeFantasma on 2011-05-01
Is it possible without a program?
Since I don't want "crap" on my PC....


just tried EYED3:> eyeD3 --remove-images * *.mp3


from this thread : [http://ubuntuforums.org/showthread.php?t=895514](http://ubuntuforums.org/showthread.php?t=895514)

but sometimes I get this error:

> -------------------------------------------------------------------------------
Uncaught exception: need more than 1 value to unpack
Traceback (most recent call last):
  File "/usr/bin/eyeD3", line 1215, in <module>
    retval = main();
  File "/usr/bin/eyeD3", line 1192, in main
    retval = app.handleFile(f);
  File "/usr/bin/eyeD3", line 504, in handleFile
    TagDriverBase.handleFile(self, f)
  File "/usr/bin/eyeD3", line 377, in handleFile
    self.audioFile = eyeD3.tag.Mp3AudioFile(f, self.opts.tagVersion);
  File "/usr/lib/python2.6/site-packages/eyeD3/tag.py", line 1623, in __init__
    hasTag = self.tag.link(f, tagVersion);
  File "/usr/lib/python2.6/site-packages/eyeD3/tag.py", line 474, in link
    padding = self.__loadV2Tag(f);
  File "/usr/lib/python2.6/site-packages/eyeD3/tag.py", line 1355, in
__loadV2Tag
    padding = self.frames.parse(fp, self.header, self.extendedHeader);
  File "/usr/lib/python2.6/site-packages/eyeD3/frames.py", line 1809, in parse
    self.addFrame(createFrame(frameHeader, data, tagHeader))
  File "/usr/lib/python2.6/site-packages/eyeD3/frames.py", line 2175, in
createFrame
    unsync_default=tagHeader.unsync)
  File "/usr/lib/python2.6/site-packages/eyeD3/frames.py", line 904, in
__init__
    unsync_default=unsync_default)
  File "/usr/lib/python2.6/site-packages/eyeD3/frames.py", line 714, in
__init__
    self._set(data, frameHeader);
  File "/usr/lib/python2.6/site-packages/eyeD3/frames.py", line 925, in _set
    (d, t) = splitUnicode(data[1:], self.encoding);
ValueError: need more than 1 value to unpack

and an error reading: > Unable to write ID3 V2.2

Gonna mark this thread as SOLVED since I'm gonna do little of them both (Easytag + EyeD3...)

---

