---
title: "ffmpeg VBR?"
date: 2008-11-08
forum: Multimedia Software
---

### Post by mateoc15 on 2008-11-08
I am converting a VOR file (a form of MPEG I'm told) into a VOB and have done so successfully with the line below.
```
ffmpeg -i /media/Data_/Video/VR_MOVIE.VRO -acodec copy -vcodec copy /media/Data_/Video/main.vob
```
The original VOB is about an hour and a half long and I want to extract just a few minutes in the middle using this line:
```
 ffmpeg -i /media/Data_/Video/VR_MOVIE.VRO -acodec copy -vcodec copy -ss 00:18:21 -t 00:02:02  /media/Data_/Video/wakeskate1.vob
```
I'm getting the start time 18:21 by just playing the first file in the default Ubuntu player (Open with "Movie Player" when right clicking the icon for the file) and just writing down the time, but when I look at the file wakeskate1.vob it looks like it's actually starting the video from about 25 minutes into the first file. 

Is it possible that there is some variable bit rate that's causing the times I see in the Movie Player to be off by a few minutes?  How can I better determine where I actually want to split this thing?  Are there maybe some better tools to do this?  I saw some brief "buffer underflow" messages.  Is that something to worry about?

Thanks in advance!  Loving Ubuntu so far!

---

### Post by mateoc15 on 2008-11-09
One other part I'm having trouble with...

Let's assume that the lines above DO work to convert it to a usable VOB file (mpeg2 I guess?).  How might I generate the IFO and BUP files that need to go with it?  I can't find anything out there on IFO file contents.  If it's just a text file with some special syntax for menu information, etc that would be great.

Thanks!

---

### Post by johnjoe on 2008-12-22
Hi

Please see my reply to other VRO post

John

---

