---
title: "Rotate AVI video from canon camera"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by rscarriere on 2007-03-20
I'm hoping this will help someone because it too me a while to figure out (and is relatively simple).  I know almost nothing about video - so please take this with a grain of salt.

I have a canon S3IS digital still camera which is also able to record video.  Problem is that sometimes I want to take video in "portrait" mode rather than "landscape" (in other words - hold the camera sideways).  To rotate the video you can use this command:

mencoder -vop rotate=1 <INPUT_FILE_NAME.AVI> -ovc x264 -oac copy -o <OUTPUT_FILE_NAME.AVI> 

I'm pretty sure this also converts the video to x264?  Anyways - it reduced my file size by 1/4.

good luck.

---

### Post by martinimnetz on 2007-06-10
Hi rscarriere,

Thanks so much for the post! That was exactly what I needed. Glad that I found your post. I tried to tackle the task about a month ago without much success: with the help of other threads in this forum and at linuxquestions.org, I got the rotating done; however, subsequently, the pics were very grainy and the audio track was misaligned. After having been tied up jobwise since then, today I got back to the task. As I couldn't remember anything from my first approach, I just searched the forums again - and voil`a, there I found your post and got the videos rotated in no time and with an excellent result at that.

By the way, both my videos have been reduced in size by app. 45% in the process without any noticable loss in quality.

So thanks again! I simply love those forums!

Cheers,
martinimnetz

---

