---
title: "Converting IV50 .avi files to theora"
date: 2010-07-21
forum: Multimedia Software
---

### Post by kev717 on 2010-07-21
I have a bunch of old .avi videos encoded using the IV50 codec and I can't find a way to convert them to .ogv or .ogg (or what-evs).  So far I've tried ffmpeg2theora, VLC, ffmpeg and mencoder to no avail.  The only way I could get these video files to even play is through installing the w32codecs and playing them through mplayer.  
attachment: zipped video file - demo video for the camera.

Basically I just want to convert all of these old .avi videos to a free file format so that I don't loose all of them in the future and so that I can (try to) put together a memorial video.  

Thank-you in advance to all who can help
-kev717

---

### Post by FakeOutdoorsman on 2010-07-21
FFmpeg is now able to decode Indeo 5, but you'll need to use a recent FFmpeg to do this.  Lucid's FFmpeg is too old, but you can easily compile FFmpeg SVN:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Example to encode to a H.264 MKV:
```
ffmpeg -i FishTank.avi -vcodec libx264 -vpre slow -crf 18 -acodec copy -threads 0 FishTank.mkv
```

You can convert this into a batch command with *find* as described here:
[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

Or you could use WinFF to batch convert with FFmpeg and create your own WinFF preset.

Ubuntu Maverick's FFmpeg is new enough too.  Or you can decode it with MPlayer and encode with the older FFmpeg in the Lucid repository using a named pipe.

---

### Post by kev717 on 2010-07-23
Ah, thank-you.  The new ffmpeg seems to work perfectly at converting these videos.  Thank-you for your help.
-kev717

---

