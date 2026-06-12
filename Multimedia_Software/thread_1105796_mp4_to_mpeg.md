---
title: "mp4 to mpeg"
date: 2009-03-25
forum: Multimedia Software
---

### Post by madman92 on 2009-03-25
I've got a whole bunch of mp4's from an old mac. I need to convert them to mpeg so i can use them in a powerpoint. I've tried ffmpeg, mencoder, vlc, and transcode, but nothing seems to work.

---

### Post by Agent.Logic_ on 2009-03-25
Hi madman92,

Check out this [post](http://ubuntuforums.org/showthread.php?t=503018), and see if DeVeDe or Avidemux works for you.

---

### Post by andrew.46 on 2009-03-25
Hi madman92,

> **madman92 said:**
> I've got a whole bunch of mp4's from an old mac. I need to convert them to mpeg so i can use them in a powerpoint. I've tried ffmpeg, mencoder, vlc, and transcode, but nothing seems to work.

I am not familiar with the formats that powerpoint that will take but I suspect that you are after mpeg-1 or mpeg-2 video and mp3 sound with a 'filename.mpg' naming scheme. FFmpeg can convert to this quite easily but it would be interesting to know the contents of your mp4s. Can you run FFmpeg over a sample of these:

```
ffmpeg -i myfile.mp4
```

and this will give a guide to the syntax that will be required. Which I am sure someone can demonstrate to you if you would like :-).

All the best,

Andrew

---

### Post by madman92 on 2009-03-26
thanks for your help guys. Turns out I didn't have the right codecs installed.

I just used ffmpeg -i movie.mp4 -vcodec mpeg1video out.mpeg

Now it plays with windows media player and quicktime
I'm just a little worried about a lossy conversion.
Do you guys think that is a problem?

---

### Post by FakeOutdoorsman on 2009-03-26
> **madman92 said:**
> ...
I'm just a little worried about a lossy conversion.
Do you guys think that is a problem?
If it plays and looks ok in PowerPoint then I don't see any problems with doing it this way.  If you want better quality either declare a higer bitrate (default is 200kb/s) or use the "sameq" option which will automatically use an appropriate bitrate to attempt to match the quality of the original video.
```
ffmpeg -i movie.mp4 -sameq -vcodec mpeg1video out.mpeg
```

---

