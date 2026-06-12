---
title: "FFMPEG Conversion Issues"
date: 2011-07-18
forum: Multimedia Software
---

### Post by EvMan4ca on 2011-07-18
I had just installed FFMPEG on my Ubuntu system and have been having a few conversion issues.

First I use Thoggen to create my video or audio file, and create the highest quality (Quality 63) for this file. I am not worried that much about file size as long as the original convert is closest to the original quality.

Once the conversion is done, I use FFMPEG to make my video or audio file into the file type of my choice. for instansce:

sudo ffmpeg -i input.ogv output.avi

Now usually when the conversion is done you will get something like this when it is finished:

7 fps=231 q=0.0 Lsize=  264051kB time=1462.87 bitrate=1478.7kbits/s    
video:240383kB audio:22827kB global headers:0kB muxing overhead 0.319538%

If you get this you can safely say that your conversion was successful. But what I have been getting for some files I have been converting were something like this:

frame=45186 fps=229 q=0.0 Lsize=  340911kB time=1553.67 bitrate=1797.5kbits/s  
blastman@ubuntu:~/

It seems that the conversion didn't finish and won't play.

Now I checked the original conversion file and that plays fine, but the file (from the second example) will not play. I have tried making the file sizes smaller, to see if it took too long to convert so then failed.. but that seemed to not be the problem. I also tried to convert to different file formats (ogv to mp4) but that still didn't resolve the issue.

I will keep trying to convert to different formats using different sizes and codecs, but I don't know if that is the direct issue. Any help would be appreciated!

---

