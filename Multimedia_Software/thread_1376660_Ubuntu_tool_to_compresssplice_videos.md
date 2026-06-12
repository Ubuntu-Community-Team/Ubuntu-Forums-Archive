---
title: "Ubuntu tool to compress/splice videos?"
date: 2010-01-09
forum: Multimedia Software
---

### Post by Lakeside on 2010-01-09
I have a few '.flv's now (thanks to ffmpeg and the great help on this forum) and most are small enough to upload to my Joomla web site and play with AllVideos (extension) but a few are over the 10M limit, I have one that is actually 50M!  Is there something I can use to either splice the videos (make 2 or 3 out of one, upload seperately) or to compress down to 10M- w/o  wrecking the quality?  thanks.

---

### Post by FakeOutdoorsman on 2010-01-09
> **Lakeside said:**
> I have a few '.flv's now (thanks to ffmpeg and the great help on this forum) and most are small enough to upload to my Joomla web site and play with AllVideos (extension) but a few are over the 10M limit, I have one that is actually 50M!  Is there something I can use to either splice the videos (make 2 or 3 out of one, upload seperately) or to compress down to 10M- w/o  wrecking the quality?  thanks.

According to my last reply to you from another thread, you are using FFmpeg's *flv* encoder which is actually not very good and I think has not been seriously updated for quite some time.  It's outdated.  Also, you are using an old version of FFmpeg.  It is also outdated.

If you want to continue using the flv encoder with your version of FFmpeg, then you need to change your quality level.  You are currently using *-qscale 5*.  Increasing the *-qscale* value will decrease both your video quality and the final file size.   Doubling the *-qscale* value will roughly half the bitrate used to encode the video, and therefore will more or less cut your file size in half.  You could also use *-b* instead of *-qscale*.  With *-b* you can more accurately determine the final size of your video.  This option requires a value as well, such as *-b 512k*.  Remember: file size = bitrate * duration.

You could also just split your video:
```
ffmpeg -t 30 -ss 60 -i input.flv -acodec copy -vcodec copy output.flv
```
[indent]**-t** is the length of output.flv
**-ss** is the amount of seconds FFmpeg should ignore starting from the beginning of the input file.[/indent]
There is also the *-fs* option, but I've never used it.  From *ffmpeg -h*:
```
-fs limit_size      set the limit file size in bytes
```

You could also [compile FFmpeg](http://ubuntuforums.org/showthread.php?t=786095) to get a recent version and use one of the several examples using *libx264* that  I already gave you.

---

### Post by Lakeside on 2010-01-10
Thanks for all the extra info- you sure know your video stuff!  I opened one of the videos in ffmpeg (the gui) and figured out how to splice it, wasn't too hard. I like to learn the terminal though for fine tuning the quality, like you said.  I will read up on some tuts for that, probably lots on here :)  Turns out I was able to increase the 'upload max.' in Joomla- increased it to 20M (don't want to try anything higher just yet)  and I spliced a video on ffmpeg to about 15M, will try to upload it now.   do have to do some 'compiling' and updating of the ffmpeg like u say tho (when time allows, I'm supposed to be focused on college- Mining lol) Thanks again for so much help!

---

