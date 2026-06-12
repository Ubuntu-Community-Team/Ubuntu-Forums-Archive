---
title: "avconv segmentation fault when transcoding audio"
date: 2014-06-02
forum: Multimedia Software
---

### Post by kthardin on 2014-06-02
I recently upgraded my distro of Kubuntu to 14.04 from 12.04.  In version 12.04, I had been using avconv to extract the 5.1 AC3 audio from the video files I was taking with my camcorder.  From here, I was importing them into Audacity and adding things like fading in and out, some general gain adjustments, that sort of thing, and then exporting them back out to a separate 5.1 AC3 file, which I would then use when I transcoded the video into various formats.

Well, as it turns out, Audacity is no longer using FFMPEG to do anything due to older versions and newer versions of FFMPEG, without some hacking I'm not exactly able to do in this current version of Ubuntu.  I've made attempts to use avconv to output an audio file in a format that the currently crippled Audacity can use.  Here's the output:

avconv -i 'video.m2ts' -f aiff  'audio.aiff' 
avconv version 9.13-6:9.13-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on May  9 2014 13:34:03 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
Input #0, mpegts, from 'video.m2ts':
  Duration: 02:19:49.81, start: 4199.966633, bitrate: 13738 kb/s
  Program 1 
    Stream #0:0[0x1011]: Video: h264 (High) (HDMV / 0x564D4448), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 59.94 fps, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0:1[0x1100]: Audio: ac3 (AC-3 / 0x332D4341), 48000 Hz, 5.1(side), fltp, 384 kb/s
    Stream #0:2[0x1200]: Subtitle: hdmv_pgs_subtitle ([144][0][0][0] / 0x0090)
[graph 0 input from stream 0:0 @ 0x2389a60] Flat options syntax is deprecated, use key=value pairs
Output #0, aiff, to 'audio.aiff':
  Metadata:
    encoder         : Lavf54.63.104
    Stream #0:0: Video: png, rgb24, 1920x1080 [SAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 59.94 tbc
    Stream #0:1: Audio: pcm_s16be (NONE / 0x454E4F4E), 48000 Hz, 5.1(side), s16, 4608 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> png)
  Stream #0:1 -> #0:1 (ac3 -> pcm_s16be)
Press ctrl-c to stop encoding
Segmentation fault (core dumped)

I've attempted to create 5.1 channel aiff and wav files which have resulted in the segmentation fault above, so I cannot even use SoX.  Audacity cannot use any of the FFMPEG based files rendering it absolutely worthless.  With avconv unable to convert the files to a format which is relatively lossless and editable, it too is now worthless.

I'm at a total loss here.  I'm just trying to perform some relatively minor changes to a 5.1 audio file.  Anyone have any ideas?

---

### Post by andrew.46 on 2014-06-02
Using a current FFmpeg that command causes no problem, perhaps upgrade to the current git FFmpeg and try again?

BTW there is a step by step guide on these Forums that will get Audacity working again with FFmpeg for 14.04.....

---

### Post by Yellow Pasque on 2014-06-02
Link to guide: [http://ubuntuforums.org/showthread.php?t=2219907](http://ubuntuforums.org/showthread.php?t=2219907)

As far as segfaulting goes, it probably needs developer attention, so if you want to help solve that, you'll need a good stack trace: [https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

---

### Post by kthardin on 2014-06-03
Thanks, the guide for custom compiling and installing Audacity with its own build of FFMPEG worked very well.  I wound up using the build options from ron998 further down, which required that I install a couple more libraries, but not a problem once I found them.

Concerning the avconv problem, that one pissed me off enough that I deinstalled libav-tools, and compiled my own custom version of FFMPEG using the various tutorials found on its website and a couple of others.  Not as easy as I remember from the last time I did this (which was a couple years ago), due to several of the dev library packages being 'broken' from the get go requiring that I use aptitude to downgrade them to earlier versions, once I figured out how to do that anyway.

Thanks for the help.

---

### Post by andrew.46 on 2014-06-07
> **kthardin said:**
> Thanks, the guide for custom compiling and installing Audacity with its own build of FFMPEG worked very well.  I wound up using the build options from ron998 further down, which required that I install a couple more libraries, but not a problem once I found them.

Which were the extra libraries that you needed? I can add them to the main guide....

**Edit: **Perhaps not, looks like the issue has almost been resolved by various developers and package builders :)

---

