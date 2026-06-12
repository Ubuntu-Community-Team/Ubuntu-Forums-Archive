---
title: "[SOLVED] Hello , and a video editing issue"
date: 2008-09-03
forum: Multimedia Software
---

### Post by eru777 on 2008-09-03
I'm having a problem with cinelerra. The raw video , which my digital camera provides, seems to have complications with the software.

The video is about 2 minutes long, and is roughly 500mb in size.
When I try to edit the video with cinelerra, while having put a music track, it renders and crashes at the 99% part, leaving the "rendered" video incomplete, with a rough blue image, and a size of 6GB.

I tried editing the raw video file with pitivi and some other video encoding means, to no result . I tried to edit the raw file first, so that it might be accepted by cinelerra better.

Is there any way, even with FFvideo , even by console command, to encode the RAW video file into a small youtube mp4 video without causing trouble?
Pitivi prompted me with something like "can't process". I guess there is a conflict with the video format.

What I want to do is make a video of a small size, with a music track playing in the background. No fancy effects, just a simple task, which would be a 2 minutes trouble with windows movie maker .

Ubuntu doesn't handle video editing well, in fact, it's horrible at it, I can't even succeed in making a simple video like that.

I am asking for a simple way to bypass this issue, and finally (hopefully) to render a small sized video, perfectly edited for youtube usage.

Thanks in advance, please give any information you think it might help, even in the slightest .

EDIT: I installed kdenlive but I can't make it start, not with f2 and the name, nothing .( it doesn't appear in the program list)
Any other video editing software (preferably with music) will be much appreciated. I have tried pretty much all of them to zero result.

---

### Post by mateuszbaranski on 2008-09-03
For this simple task you could use Kino - which is quite simple and has got one nice feature - it has got bult-in scripts which could export to XVID, and other formats. You could also use pipe and use your own script for exporting rendered video. If you need put a backround music there is a possibility there.If it's not enough sorry for bother you.

I use cinelerra very extensively (I need NLV, multitrack editing) but I have never sucseeded in exporting video directly by cinelerra. Always crashed, or went to endless loop doing something. If you still want to use cinelerra follow one one paths:
1) export to MPEG YUV stream, use PIPE, and write your script in ~/cine.sh in which you could use some coder - e.g. mpeg2enc or ffmpeg with your own set of parameters
more information on this you could find on MJPEGtools website or here:
[http://cinelerra.org/docs/cinelerra_cv_manual_en.html](http://cinelerra.org/docs/cinelerra_cv_manual_en.html)
The method which I use for DVD is here:
chapter 20.9.1.1 yuv4mpeg pipe through mpeg2enc 

And for you probably would suit this:
20.7 Rendering videos for the internet

2) export to RAW dv (so actually cinelerra just renders the movie - no encoding is made), check the movie with e.g. mplayer, and then encode using some command line tools (mpeg2enc or ffmpeg or some other favorite). This is good solution over 1) if you want to optimize the size of movie - in this case you don't need to render the movie in cinelerra again if the size of file would be to large for website.

p.s. the guys in us probably would use quicktime container instead of dv

---

### Post by eru777 on 2008-09-03
> **mateuszbaranski said:**
> For this simple task you could use Kino - which is quite simple and has got one nice feature - it has got bult-in scripts which could export to XVID, and other formats. You could also use pipe and use your own script for exporting rendered video. If you need put a backround music there is a possibility there.If it's not enough sorry for bother you.

I use cinelerra very extensively (I need NLV, multitrack editing) but I have never sucseeded in exporting video directly by cinelerra. Always crashed, or went to endless loop doing something. If you still want to use cinelerra follow one one paths:
1) export to MPEG YUV stream, use PIPE, and write your script in ~/cine.sh in which you could use some coder - e.g. mpeg2enc or ffmpeg with your own set of parameters
more information on this you could find on MJPEGtools website or here:
[http://cinelerra.org/docs/cinelerra_cv_manual_en.html](http://cinelerra.org/docs/cinelerra_cv_manual_en.html)
The method which I use for DVD is here:
chapter 20.9.1.1 yuv4mpeg pipe through mpeg2enc 

And for you probably would suit this:
20.7 Rendering videos for the internet

2) export to RAW dv (so actually cinelerra just renders the movie - no encoding is made), check the movie with e.g. mplayer, and then encode using some command line tools (mpeg2enc or ffmpeg or some other favorite). This is good solution over 1) if you want to optimize the size of movie - in this case you don't need to render the movie in cinelerra again if the size of file would be to large for website.

p.s. the guys in us probably would use quicktime container instead of dv

looks complicated

cinelerra cant even do it in RAW. Says cant open the file "file name" which i named the video

---

### Post by eru777 on 2008-09-03
thanks you polish man, you saved me .
After hours of legwork and failed attempts, massive anger, I found the solution.

1. Import video from cam
2.Encode RAW video as ogg vorbis with kino.
3.Edit video with cinelerra.
4.Render video with cinelerra, and put ogg vorbis as outcome file.
5.encode again with kino, only now export as mp4 double tracked, broadband quality.

Upload on youtube, you just figured out an ubuntu movie maker ;)

I hope this solves many other newbie problems like mine out there.

---

