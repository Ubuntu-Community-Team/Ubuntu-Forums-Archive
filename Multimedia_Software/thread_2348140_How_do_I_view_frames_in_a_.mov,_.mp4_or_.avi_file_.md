---
title: "How do I view frames in a .mov, .mp4 or .avi file on OpenShot?"
date: 2017-01-01
forum: Multimedia Software
---

### Post by Music_Guy on 2017-01-01
I would like to cut out about 11 minutes from a 53 minute video using open shot. The video is now in .mov format (though I can convert it to mp4 or avi if necessary). When I import the video into OpenShot and add it to the timeline I only see basically one thumbnail. I don't know how to expand it further. I could not find any similar questions on this thread (though I certainly may have missed some). Any suggestions?

Thanks.

---

### Post by SeijiSensei on 2017-01-01
I'd use [ffmpeg]("https://trac.ffmpeg.org/wiki/Seeking")  from the command line with the start time and duration of the clip you want.

```
ffmpeg -i input.mp4 -vcodec copy -acodec copy -ss  00:10:00 -t 21 output.mp4
```

This extracts a twenty-one second clip starting ten minutes into input.mp4 and writes it to output.mp4.  You can specify a different output container like Matroska by using "output.mkv" instead.  Using "-vcodec copy -acodec copy" tells ffmpeg not to reencode the tracks but copy them intact.  You can also use "-to h:m:s" to specify an end time rather than -t which specifies a duration in seconds.

FFMpeg handles .mov files and the Apple "prores" codec.  You can see the list of supported formats with "ffmpeg -decoders" and "ffmpeg -encoders".  I recently used it to reencode such a file into WMV3 video and added an AAC audio track like this:

```
ffmpeg -i input.mov -i music.ogg -vcodec wmv3 -acodec aac -strict -2 output.mp4
```

This particular combination of codecs played correctly on Windows, OS X, and Linux.  It also reduced the size of the file from over 2 GB to 40 MB!

I often use SMPlayer to write a sequence of frames to PNG files. You can use Shift+D to start and stop the frame capture.  I can then import the frames into GIMP to create [animated](http://www.takinganimeseriously.com/images/avatars/) [avatars](https://forums.animesuki.com/album.php?albumid=115).

---

