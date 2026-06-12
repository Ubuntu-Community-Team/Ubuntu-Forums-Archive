---
title: "Stitching videos together"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Chrus on 2009-06-17
Im in the process of making a media server, so im ripping my dvd's for streaming to my xbox. (Dont worry, I own the dvd's)

Ive come across a few dvd's that have the movie spread over 2 or 3 titles, so when i rip them i end up with 2 or 3 .mp4 files.

Is there something i can do in command line to stitch them together into 1 file without changing the encoding or anything else?

Is this right?
```
cat part1.mp4 part2.mp4 part3.mp4 > movie.mp4
```
Would that work?

Cheers

---

### Post by Waappu on 2009-06-17
Hi

This guide might help you
[http://www.lynchconsulting.com.au/blog/index.cfm/2008/1/12/Joining-video-files-in-Ubuntu](http://www.lynchconsulting.com.au/blog/index.cfm/2008/1/12/Joining-video-files-in-Ubuntu)

---

### Post by Chrus on 2009-06-17
Well i was close. Thanks mate. Will give it a shot.

---

### Post by devilliers123 on 2012-01-18
I tried the same thing.

What I found worked was using that code with .mpeg file suffix but NOT .mp4

So what worked was   >>>>>    cat aaa.mpeg bbb.mpeg > nnn.mpeg

also I used    >>>>>                  mencoder -oac copy -ovc copy -idx -o nnn.mpeg aaa.mpeg bbb.mpeg

I found that the  -idx   whether entered or absent had no effect whatsoever.

What was strange was that the output made DOUBLE  clips i.e nnn.mpeg + nnn.mpeg in both cases

Otherwise the quality of video and sound was excellent in Movieplayer.

Anyone any ideas about that DUPLICATION?  It is like an ECHO?

---

