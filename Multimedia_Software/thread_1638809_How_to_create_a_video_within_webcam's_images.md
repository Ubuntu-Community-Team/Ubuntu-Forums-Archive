---
title: "How to create a video within webcam's images"
date: 2010-12-06
forum: Multimedia Software
---

### Post by the_craic on 2010-12-06
Hi there!

I have a very big image directory: One image per minute, whole a year, captured from a webcam.
Now I want to make a video (15 or 24FPS) with all the webcam captures, to see how it changed during this period.
I've tried automotion, but it makes a very low quality video, besides it blocks with lots of images.
I've also tried dvd-slideshow, but it's not possible to make a more-than-1FPS video.
What application would you advice me?

I also need to change the date in each webcam's images, because they are wrong, so it needed to overlay a little layout with the right date for each image, is that possible to manage within some application?
Preferibly shell applications which supports lots of Gb of information (anyway I always could make little videos and then glue them)

Thak you very much indeed

---

### Post by the_craic on 2010-12-06
Let me reply myself because I've found the solution for the second problem; 'adding a label to each image'
ImageMagick is the solution, I made some tests and here you have an example:

composite label:"05/12/10 11:05" -gravity southeast -geometry +1+2 input.jpg output.jpg

I strong recomend ImageMagick because it's a world of possibilities ;)

Could anyone help me with the other problem?

---

### Post by FakeOutdoorsman on 2010-12-06
ImageMagick sure is useful.  You can use FFmpeg to make the movie:
```
ffmpeg -r 24 -i input%03d.jpg -i audio.ogg -vcodec libx264 -vpre medium \
-crf 22 -acodec copy -threads 0 -metadata title="The Title" -metadata \
author="the_craic" output.mkv
```

Your input files must be sequentially named: the first image being named **1.foo*.  If my first image is named *input001.jpg*, then the FFmpeg input will be called *input%03d.jpg*. See the FFmpeg FAQ: [How do I encode single pictures into movies?](http://www.ffmpeg.org/faq.html#SEC14) This link also contains a script that will rename your images if they are not in the proper FFmpeg friendly order.

You may need to enable the **libx264** encoder to use my example:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

