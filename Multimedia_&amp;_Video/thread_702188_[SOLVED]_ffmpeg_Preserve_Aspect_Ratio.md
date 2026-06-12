---
title: "[SOLVED] ffmpeg Preserve Aspect Ratio"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by what4893 on 2008-02-20
Hi,

I want to write a script to batch convert recorded TV shows, movies, and other such videos so that I can stream them to my iPhone. I have ffmpeg setup and it works great. The only issue I'm running into is with the aspect ratio of the incoming source video vs the output file. So that I can stream my videos over the EDGE network I would like to convert the video files to 320x240. The issue is that if I specify 320x240 as my size parameter in ffmpeg then the video is stretched or cropped to make it fit. How do I get the output video the scale the largest edge to 320 or 240 and keep the original aspect ratio of the source video file? Sorry if that is unclear. Let me know if you have any questions and thanks for any help you can offer.

Nick

---

### Post by philc on 2008-02-20
I think I understand what you're asking......

I'm assuming that your input video has an aspect ratio of 16:9. E.g. 720x404 for PAL footage.

A video at 320x240 has an aspect ratio of 4:3.

To avoid stretching or cropping the original image, I would recommend letterboxing the output file - black bands top and bottom.

Therefore, convert the 720x404 file to 320x180 and add 30 pixels of padding top and bottom. Essentially if you divide width by height of each (720/404 and 320/180) you should get the same result. However, keep in mind that you can only add even whole numbers when padding - you can't have an output height of 179.55555555.

Something like this:

```
ffmpeg -i input.file -s 320x180 -padtop 30 -padbottom 30 output.file
```

This will result in a 320x240 final file and the picture will retain the correct aspect ratio. Be sure to set the size flag prior to padding.

---

### Post by what4893 on 2008-02-20
This looks like a perfect solution. Any recommendations as to how I might go about getting video dimensions in a script? I'm new to video converting in Linux. Is there some command that will dump out info about the video file and then I could grep for the aspect ratio and dimensions? Thanks for your help.

---

### Post by philc on 2008-02-20
If you simply type:

```
ffmpeg -i input.file
```

FFmpeg will spit out a load of details about your file. The most interesting bits for you will probably look something like this:

> Duration: 00:00:51.7, start: 0.000000, bitrate: 862 kb/s
Stream #0.0(eng): Video: h264, yuv420p, 480x360 [PAR 0:1 DAR 0:1], 25.00 tb(r)
Stream #0.1(eng): Audio: mpeg4aac, 44100 Hz, stereo

Here's a How-To I wrote for creating a perl script to take some of these details, write them to a text file, then display back to the user the information in a slightly more friendly format:

[http://stream0.org/2008/01/find-and-extract-video-file-de.html](http://stream0.org/2008/01/find-and-extract-video-file-de.html)

---

### Post by what4893 on 2008-02-20
Thank you for all your help philc. I think that answers all my questions for the moment.

Nick

---

