---
title: "Converting .MTS to mpeg or avi"
date: 2016-02-25
forum: Multimedia Software
---

### Post by fishflop on 2016-02-25
Hey,

I am using Ubuntu 14.04, have a sony cyber shot camera and want to convert its videos from .mts to a readable .mpeg, mp4 or avi format in order to play them on my computer without any problems. I have read several threads that dealt with the conversion problem, tried avidemux and winff, but still failed to convert the files (when loading the mts files, avidemux responds: "H.264 detected - If the file is using B-frames as reference it can lead to a crash or stuttering. Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY." and then loads an inusable file. winff marks the .mts file as "invalid preset file" when trying to load it).

Any idea what I can do?

Thanks for the help

---

### Post by Rob Sayer on 2016-02-25
H.264 video isn't useless in Avidemux if you just want to convert.  I've done this many times, generally to mpeg-4 ASP (xvid).  Just select the safe mode.  BTW Mpeg, mp4 and avi are not formats, they're containers.  The file extension does not tell you what video or audio formats are there.  You should install mediainfo (mediainfo-gui is the package name) to see what you actually have there.

The safe mode does make editing pretty much impossible with avidemux but it'll convert.

---

### Post by fishflop on 2016-02-25
Thanks for the quick reply!

When I try to load the mts video in safe mode, it will just show a green stripe. And when I try to save the loaded video in .avi, avidemux saves a 8.5kb file and crashes...

---

### Post by blm-ubunet on 2016-02-25
You don't need to transcode from H264, you just need to "re-containerise" it into some sensible container  like mkv, mpegts, mpegps.
mpeg4-part-10-AVC (ITU H264) would have the widest h/w support of any codec.
 
This should be trivial with ffmpeg, mkvtoolnix or handbrake.
I would avoid avi & avidemux like the plague.

---

### Post by FakeOutdoorsman on 2016-02-25
I don't have any trouble playing my MTS files. Does it simply not have the processing power to deal with decoding (assuming you're not using any hardware acceleration)? What player are you using?

Providing some info about a typical MTS file will help us provide a better answer. The complete output of "ffmpeg -i input.MTS" will be informative.

---

