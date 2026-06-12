---
title: "split video with ffmpeg without losing frames"
date: 2009-05-14
forum: Multimedia Software
---

### Post by yaelk on 2009-05-14
Hi,
 
I am trying to split a video into several consecutive clips using ffmpeg's -ss and -t options. I need to not lose or repeat frames between clips (i.e. clip 2 needs to start exactly where clip 1 ended). Since my videos are at 30 frames per second and ffmpeg's options only allow one to specify time to the second, how can I get around this? If it's not possible with ffmpeg, can somebody suggest other software (for windows and linux) that can do this? I will need to run a batch job, though, since I need to split lots of files, so software that is gui-only won't work.
 
Below is my ffmpeg code:
 
@echo on
FOR %%X IN (*.avi) DO (ffmpeg -i "%%X" -vcodec mjpeg -qscale 1 -an -ss 00:00:10 -t 00:00:30 "%%X1.avi" -ss 00:0040 -t 00:00:30 "%%X2.avi")
 
Thanks everybody! (This is my first post . . .)
Yael

---

### Post by FakeOutdoorsman on 2009-05-14
FFmpeg should allow you to specify time to the frame: **hh:mm:ss:ff**.  Also, instead of re-encoding each split section, you can try copying the stream.  I'm not sure if this works with all formats due to the nature of long GOP, etc:
```
ffmpeg -i input.avi -an -vcodec copy -ss 00:00:10:15 -t 00:00:30:00 output1.avi -an -vcodec copy -ss 00:00:20:16 -t 00:00:30:00 output2.avi
```

---

### Post by yaelk on 2009-05-14
Cool. Thanks!
 
Do you know if there's a way of having ffmpeg find out the total length of the video in time? All I know is the size of the file. I would ideally like to split the files into equal parts. Also, is there a way of saying 'encode until you get to the end' if I don't know where the end is?

Thanks again!

---

### Post by sudhipro on 2010-05-19
Hi,
Finding total length of video was quite tricky
Please check the following url:
[http://leaveurdream.blogspot.com/2010/05/get-total-length-of-video-in-php.html](http://leaveurdream.blogspot.com/2010/05/get-total-length-of-video-in-php.html)

---

