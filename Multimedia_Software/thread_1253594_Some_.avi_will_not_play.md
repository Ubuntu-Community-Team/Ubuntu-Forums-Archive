---
title: "Some .avi will not play"
date: 2009-08-30
forum: Multimedia Software
---

### Post by hgraham on 2009-08-30
Some of my .avi files will not play in ubuntu 9.04.
I ran ffmpeg -i problem_file.avi and was shown

libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.37. 0 / 52.37. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Aug 13 2009 11:27:42, gcc: 4.3.3
xxxxxxxxxxxxxxx.avi: Unknown format

I have run all the possible updates for non-free and reinstalled many things.  All packages suggested return 0 updates 0 packages installed.
All attempts to convert the files to other formats have failed.  The .avi files are said to be unrecognized by the conversion programs.

Any ideas will be appreciated.

Thanks

Howard

---

### Post by andrew.46 on 2009-08-30
Hi Howard,

Could you have a look at the following page:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and update your copy of FFmpeg as described there? If you then run your previous command:

```
ffmpeg -i problemfile.avi
```

you will hopefully get fuller information. Post the *full* terminal output, including the command, here and hopefully the file can be identified and played :-).

All the best,

Andrew

---

### Post by hgraham on 2009-08-30
I did as you said and recompiled the ffmpeg ans x264

The files now play.  Something must have been messed up.

Thanks for your help.  The web page you directed me to was the best description of how compile ffmpeg and x264   Very helpful

Howard

---

### Post by andrew.46 on 2009-08-30
Hi Howard,

> **hgraham said:**
> Thanks for your help.  The web page you directed me to was the best description of how compile ffmpeg and x264   Very helpful

The Fakeoutdoorsman's guide is one of the more useful guides on this forum, well written, researched and supported.

Andrew

---

