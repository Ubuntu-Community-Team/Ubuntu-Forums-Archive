---
title: "Join 2 asf files"
date: 2011-07-12
forum: Multimedia Software
---

### Post by nelson777 on 2011-07-12
Hello,

I got 2 videos in ASF format. One has 122,6Mb and the other 29,1Mb. I'm trying to join them in a single file. Yet, when I try to do this using ffmpeg  or mencoder the resultant size is FAR greater than the original file.
I tried like this:
mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi
like this:
mencoder -oac copy -ovc copy -o output.avi video1.avi video2.avi video3.avi
like this:
ffmpeg -i ./video1.asf -i ./video2.asf -vcodec copy -acodec copy ./video.asf
I tried with cat as in:
[http://ffmpeg.org/faq.html#SEC27](http://ffmpeg.org/faq.html#SEC27)
tried to join both with cat vid1.asf vid2.asf > vid.asf and then convert with ffmpeg to .mpg. 
No deal. I can create the joined video but the least I get is 300Mb. 

Somebody knows how I can do this keeping the original size ? i.e. the resultant file should have aprox. 151,7Mb.

Thnx
-Nelson

---

### Post by andrew.46 on 2011-07-13
> **nelson777 said:**
> 
I tried with cat as in:
[http://ffmpeg.org/faq.html#SEC27](http://ffmpeg.org/faq.html#SEC27)
tried to join both with cat vid1.asf vid2.asf > vid.asf and then convert with ffmpeg to .mpg. 
No deal. 

Perhaps you have made a typo, the technique is to convert both files to mpg *first*, then cat them together and then finally to convert the concatenated file to the format and container of your choice.

---

