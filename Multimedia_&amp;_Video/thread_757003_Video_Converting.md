---
title: "Video Converting"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by popsad on 2008-04-16
Having spent most of the last year using mepis i decided to try out Ubuntu Hardy Heron and so far am very pleased.

But the one thing, no two things stop me from doing away with my dual boot, that is I have not found anything in Linux that can equal winavi for converting, not so much in the converting but in the time that it takes to do the conversion.

Under Linux so far it can take as long as the film runs to convert, sometimes to an mpeg then convert to dvd.

So my question is can i get a winavi equivalent under Linux that can convert and finish up with the dvd folder Audio and Video TS that is needed to create the dvd. In the same time it takes winavi to convert, it can do a film in 25 to 30 minutes ready for burning.

Secondly I use Pinnacle 10 for my Video work is there anything like this or is in the process of being implemented for Linux.

I cannot use wine as winavi and pinnacle do not run correctly under it

:)Thats all I need to stop dual booting, any takers:)

---

### Post by disturbedite on 2008-04-16
i don't know about winavi, but...
avidemux is the easiest to use yet very feature-rich app i know of for conversion.

---

### Post by ron999 on 2008-04-16
Hi
To make a DVD from a video file you can use **tovid** from the command line. When it's installed there's just 3 stages.

First, convert the file to correct format.
For NTSC:-
**tovid -ffmpeg -in <filename> -out movie**
For PAL:-
**tovid -pal -ffmpeg -in <filename> -out movie**

Second, make an xml file.
**makexml -dvd movie.mpg -out MyDisc**

Third, create the audio_ts and video_ts folders.
**makedvd -author MyDisc.xml**

Then it's ready to burn with K3b or similar.

There's information here:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")
Maybe tovid is in the Ubuntu repos, I'm not sure.

---

### Post by disturbedite on 2008-04-17
that method doesn't allow you to use the best settings.  with avidemux, you can set them & it is really easy to use.

---

### Post by cotcot on 2008-04-17
> **popsad said:**
> 
Secondly I use Pinnacle 10 for my Video work is there anything like this or is in the process of being implemented for Linux.

Cinelerra CV is a professional video editor for linux. It is worth a try.
The latest blender is also nice.
There are some others like kdenlive, lives, pitivi, jahshaka, open movie editor, kino, avidemux. All easier to use with somewhat less features than cinelerra but for sure worth to take knowledge of the features.

---

