---
title: "Mencoder: How to do 2 pass encoding?"
date: 2010-12-02
forum: Multimedia Software
---

### Post by keneo2 on 2010-12-02
I am using [[COLOR=#aa0000]mencoder[/COLOR]]("http://www.videohelp.com/tools/MPlayer"). I am trying to do a 2 pass encoding.
 
Here is the command line I used...
 
mencoder "program.ts" -oac copy -ovc x264 -x264encopts bitrate=1166: pass=2:threads=8 -of avi -o "program.avi"
 
I watched the status line during the encoding. The percentage indicator counted up from 0% to 100% and then the encoding finished. But I asked for 2 pass encoding. Didn't I? Shouldn't the percentage indicator have started all over at 0% for the second pass? did I make a mistake in the command line?
 
BTW this is on a windows system. But I imagine that the command syntax should be the same.
 
P.S. I placed a space in the command line between 1166: and pass=2 because if I didn't, the page would turn :+p into :p .  In the actual command I used there is no space at this point.

---

### Post by andrew.46 on 2010-12-02
Hi keneo,

Perhaps try *two* commands such as the following:

```

mencoder "program.ts" -oac copy -ovc x264 -x264encopts bitrate=1166:pass=1:threads=8:subq=1:frameref=1 -of avi -o "NUL"

mencoder "program.ts" -oac copy -ovc x264 -x264encopts bitrate=1166:pass=2:threads=8:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b -of avi -o "program.avi"

```

Note that I have not tested this under windows as it is not installed on my system :). Consider using FFmpeg instead of MEncoder, you will get better results and a greater choice of containers, h.264 is an uneasy occupant of the avi container.

Andrew

---

### Post by keneo2 on 2010-12-02
Thank you for suggesting FFmpeg.
 
I would like to give it a try, but it seems like FFmpeg was intended for people knowledgable in programing and compiling code.  I have been trying to get my hands on the FFmpeg executable, but have had a very difficult time finding it.  Why wouldn't they have a Windows executable file on the authors site? If they did I couldn't find it.
 
Can someone help me get it?
 
thanks so much for any help.

---

### Post by andrew.46 on 2010-12-02
Hi Keneo,

[http://ffmpeg.arrozcru.org/](http://ffmpeg.arrozcru.org/)

Andrew

---

