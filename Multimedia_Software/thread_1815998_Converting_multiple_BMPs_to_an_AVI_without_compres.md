---
title: "Converting multiple BMPs to an AVI without compression"
date: 2011-08-01
forum: Multimedia Software
---

### Post by wujj123456 on 2011-08-01
Hello everyone,

I am trying to convert hundreds of BMPs into a single AVI file, without compression. Since every pixel matters in my case, I don't want any kind of compression. It's fine if the output file is extremely large. 

I'd like to know if it's possible to achieve this with packages coming with Ubuntu 11.04. I have tried ffmpeg/mencoder, but they either compressed the output file, or the output file is not playable in totem. I am a new user for both tools. Please correct me if there is actually a way to get uncompressed avi from these tools. 

"BMP to AVI Sequencer" ([http://sourceforge.net/projects/bmpseq/](http://sourceforge.net/projects/bmpseq/)) does the job perfectly. I successfully converted 180 1080P BMPs into a 1G avi, running at 30 fps. Unfortunately I need a command line tool this time. 

Thanks.

---

### Post by FakeOutdoorsman on 2011-08-01
You can use the *huffyuv* encoder to create a lossless output:
```
ffmpeg -i img%d.jpg -vcodec huffyuv output.avi
```
or *rawvideo*:
```
ffmpeg -i img%d.jpg -vcodec rawvideo output.avi
```
By default this will assume your input frame rate is 25, so you can add an option to change it:
```
ffmpeg -r 30 -i img%d.jpg -vcodec huffyuv output.avi
```
By default the output will inherit the input frame rate. You can apply the same option to the output. By changing the frame rates you can achieve a certain duration. For example, if I have 900 images and want the output duration to be 60 seconds with an output frame rate of 30, then 900/60=15.
```
ffmpeg -r 15 -i img%d.jpg -r 30 -vcodec huffyuv output.avi
```
Note that your images must be named in a sequence starting with *1*, and although some encoders are lossless there can be some loss due to colorspace conversion. See FFmpeg FAQ: [How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#SEC14) for more info.

---

### Post by wujj123456 on 2011-08-01
Thank you very much! You saved my day. 

Your commands worked perfectly. With* huffyuv*, the file size is reduced by 80% with perfect quality.

---

