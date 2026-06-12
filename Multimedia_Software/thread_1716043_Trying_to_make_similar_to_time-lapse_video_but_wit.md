---
title: "Trying to make similar to time-lapse video but with mpg"
date: 2011-03-27
forum: Multimedia Software
---

### Post by nosebreaker on 2011-03-27
I took a road trip around the ENTIRE CONTINENTAL USA.  10,000 miles.  All along the trip, I had a little webcam on the dash recording as I went along, at about 320x200.  At the end of the trip, I have 139GB of mpeg videos.  I'd like to combine all these videos into one short 1hr video of the entire trip, so you can experience the trip for yourself, sort of like driving at 500Mph :)  I'd also like to change the audio to be a music file or something, since listening to "super-chipmunks" won't be helpful.

I have tried using ffmpeg to do the conversion, but the obvious options (setting source or output fps) doesn't seem to work.  I must be missing something.  The only thing I can do is change the video from 24fps (normal) to 1fps, and the audio is the same speed.

Any help is appreciated!

---

### Post by nosebreaker on 2011-03-28
I may have been mistaken, I may actually want a time-lapse video.  There is a quick script someone wrote that I am using to go through the videos now.  It takes one frame out of the video every X seconds that you specify and turns it into a PNG, and then combines all those pictures into a new movie.

The link in case anyone is wondering:
[http://pr0gr4mm3r.com/linux/how-to-create-a-time-lapse-video-using-ffmpeg/](http://pr0gr4mm3r.com/linux/how-to-create-a-time-lapse-video-using-ffmpeg/)

---

### Post by nosebreaker on 2011-03-28
Yes, it looks like this is what I want it to do!  I'll just run it through this script a few times and it should give me what I want.

---

### Post by FakeOutdoorsman on 2011-03-28
There are better methods than the one your link uses. That method requires intermediate PNG files and the last command that re-encodes everything is outdated and probably won't work anymore. It uses 512 bits per second for the output bitrate which is so low that I'm not sure if FFmpeg will allow you to use that. Less ancient FFmpeg version would require a **k** to be added to that option, for *kilo*bits, as in *-b 512k*. Anyway, that command won't give you an optimal output.

There are a few methods that you can use to speed up video in FFmpeg, but I'll show you the easier one. This first step requires you to compile FFmpeg because, as of Maverick, the version from the repository does not have the required filters. Compiling is easy if you can copy and paste the commands from this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

This command will use **cat** to feed all of the mpg files in your current directory to FFmpeg via a pipe, and the setpts filter will perform the speeding up of the video:
```
cat *.mpg | ffmpeg -i - -vcodec libx264 -vpre fast -crf 24 -an -threads 0 \
-vf setpts=0.5*PTS fastvideo.mp4
```
This example doubles the speed of the video (and also shortens the duration by half). Adjust the setpts value to change the speed. This command won't affect the audio, so now you can add audio:
```
ffmpeg -i fastvideo.mp4 -i audio.mp3 -shortest -vcodec copy -acodec libfaac \
-aq 100 -metadata title="A Title" output.mp4
```

---

