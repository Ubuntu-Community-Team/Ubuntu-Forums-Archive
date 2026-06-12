---
title: "ffmpeg and x264 - resize quality is poor"
date: 2009-01-18
forum: Multimedia Software
---

### Post by listerthrawn on 2009-01-18
Can anyone help with this issue?

Some background.

I have recorded some TV programs using a DVB-T card and VDR.  I wish to keep some of these, but in a format that I can play both on my laptop and my iPod.  The streams are in the VDR format, which I believe is Mpeg2 TS

I use ProjectX to demux the video and cut out commercials etc, then use mplex -f 8 -o output.mpg 001.m2v 001.mp2 to rejoin the audio and video (there are 2 audio streams for some reason on my recordings)

Now I come to encode the video.  The source is interlaced, but I've not noticed any problems with that when I use ffmpeg to encode the file but I have noticed vertical bands in the video, especially in darker areas.  I tried encoding but keeping the size the same as the original and the quality is much better, it seems to be the resizing that is making it look bad.

I thought it may be due to the interlaced input file, but I've tried again with a video file (an avi I got off the net) which isn't interlaced and the same vertical lines appear.

Here's the command I use to encode: -

```
ffmpeg -y -i input.mpg -pass 1 -vcodec libx264 -vpre fastfirstpass -vpre hq -vpre ipod640 -b 1000k -bt 1000k -s 640x360 -padtop 4 -padbottom 4 -threads 0 -f mp4 -an /dev/null
```

Followed by

```
ffmpeg -i input.mpg -pass 2 -acodec libfaac -ab 96k -ac 2 -vcodec libx264 -vpre hq -vpre ipod640 -b 1000k -bt 1000k -s 640x360 -padbottom 4 -padtop 4 -threads 0 -f mp4 Output.mp4
```

I could post a screen capture showing the difference if it would help.  If this is a limitation of ffmpeg, could anyone suggest a good tool to resize the mpeg2 before I pass it to ffmpeg?

Thanks a lot

Chris

---

### Post by FakeOutdoorsman on 2009-01-19
Could you post a screen capture?  I think it will help in finding the problem.  Also show the result of:
```
ffmpeg -i originalvideo.avi
```

---

