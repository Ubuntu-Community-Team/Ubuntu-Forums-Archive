---
title: "Problems uploading videos to Youtube"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Ironchew on 2007-06-03
I'm using the mencoder program to make videos to upload to Youtube, and I've tried to follow Youtube's recommendations for the format to upload (320x240 resolution, MPEG-4 video, MP3 audio, DivX).  I'm using a webcam (with EffecTV effects and vloopback to /dev/video2) and a microphone and I start up mencoder like this:

```
mencoder tv:// -tv driver=v4l:device=dev/video2:width=320:height=240:forceaudio -ovc lavc -oac lavc -lavcopts vcodec=mpeg4:acodec=mp3 -ffourcc divx -o video.avi
```

Suffice to say, the video records fine.  Ubuntu recognizes it as MPEG-4 with the DivX codec and MP3 audio, and I can play it back just fine.  When I try to upload the video to Youtube, Youtube doesn't give me any error messages about the format and it says the video will be ready in a few minutes.  So far, a couple of days later, none of my videos have shown up.  Is Youtube the issue, or what am I doing wrong?

---

### Post by earthbound01 on 2008-06-17
I also have this same problem.

---

