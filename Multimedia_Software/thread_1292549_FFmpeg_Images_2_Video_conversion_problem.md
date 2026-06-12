---
title: "FFmpeg Images 2 Video conversion problem ??"
date: 2009-10-16
forum: Multimedia Software
---

### Post by rahul23 on 2009-10-16
I got folder full of images , number of images = 600 , I want to make a video which plays one image per second hence duration of that video gona be 600 sec i.e 10 mins . (frame rate 1per sec) 

So to do this i gave 
Code:
```
ffmpeg -i /home/user/folder/image%d.jpeg -r 1 -f avi output.avi
```



but ffmpeg only processed 28 images and made the output video of duration 28 sec . 

and when I increased -r value to 2 it processed 56 images with output video of duration 28 sec. 

somehow its making output video always of 28 sec ?? 
I got no clue why its doing this my ffmpeg version is 0.5 , operating system Ubuntu 9 . 

Thanks in Advance.

---

