---
title: "good .flv to .avi converters?"
date: 2009-05-07
forum: Multimedia Software
---

### Post by crazypeppo on 2009-05-07
I have checked around for some flv. to .avi converters and none seem to work right with ubuntu 8.10. Does anyone have any recommendations? 
I currently have tried Mencoder and I get no sound after converting?

chnge to the directory you have files in - 
"mencoder -oac copy -ovc lavc -o video.avi video.flv"

---

### Post by andrew.46 on 2009-05-07
Hi crazypeppo,

> **crazypeppo said:**
> 
```
mencoder -oac copy -ovc lavc -o video.avi video.flv
```

This should work but perhaps your copy of MEncoder/MPlayer is not setup for mp3? Try the following:

```


andrew@skamandros~/Desktop$ **[COLOR="Red"]mencoder -oac help[/COLOR]**
MEncoder SVN-r29242-4.2.4 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder


```

and then:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac help | grep mp3[/COLOR]**
mp3         mp3lib    working   mp3lib MPEG layer-2, layer-3
ffmp3on4    ffmpeg    working   FFmpeg Multi-channel MPEG layer-3 on MP4 audio  [mp3on4]
ffmp3       ffmpeg    working   FFmpeg MPEG layer-3 audio  [mp3]
ffmp3adu    ffmpeg    working   FFmpeg MPEG layer-3 adu audio  [mp3adu]
mp3acm      acm       working   MPEG layer-3  [l3codeca.acm]

```

Andrew

---

### Post by inobe on 2009-05-07
> **crazypeppo said:**
> I have checked around for some flv. to .avi converters and none seem to work right with ubuntu 8.10. Does anyone have any recommendations? 
I currently have tried Mencoder and I get no sound after converting?

chnge to the directory you have files in - 
"mencoder -oac copy -ovc lavc -o video.avi video.flv"

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

---

### Post by Arup on 2009-05-07
Have you tried Handbrake or WinFF, both work quite well in my system. WinFF is in the reopos. If using multi core CPU, make sure to select that under WinFF options.

---

### Post by rainwalker on 2009-05-07
> **Arup said:**
> Have you tried Handbrake or WinFF, both work quite well in my system. WinFF is in the reopos. If using multi core CPU, make sure to select that under WinFF options.

+1 for WinFF

---

### Post by colau on 2009-05-08
WinFF is fine.

---

### Post by crazypeppo on 2009-05-08
@ Andrew
I get this:
Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   _twolame  - Twolame MP2 audio encoder_
   faac     - FAAC AAC audio encoder
then:
linux@SSL-UB:~$ mplayer -ac help | grep mp3
mp3         mp3lib    working   mp3lib MPEG layer-2, layer-3
ffmp3on4    ffmpeg    working   FFmpeg Multi-channel MPEG layer-3 on MP4 audio decoder  [mp3on4]
ffmp3       ffmpeg    working   FFmpeg MPEG layer-3 audio decoder  [mp3]
ffmp3adu    ffmpeg    working   FFmpeg MPEG layer-3 adu audio decoder  [mp3adu]
mp3acm      acm       working   MPEG layer-3  [l3codeca.acm]

Will the underlined cause any issues?

---

### Post by crazypeppo on 2009-05-08
I must say WinFF is pleasing me... I had to add a new repos and change some command line stuff for intrepid but, it seems to be well worth the time installing it! Thanks for the recommendation all.

Still seeking answer for 1st part...

---

### Post by xc3RnbFO8P on 2009-05-08
Have tried Avidemux?

---

### Post by mattgyver83 on 2009-05-08
you can also use ffmpeg from the command line, works rather well.

sudo ffmpeg -i video.flv video.avi

---

### Post by andrew.46 on 2009-05-08
Hi crazypeppo,

> **crazypeppo said:**
> 
Available codecs:
```
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   _twolame  - Twolame MP2 audio encoder_
   faac     - FAAC AAC audio encoder
```
then:
linux@SSL-UB:~$ mplayer -ac help | grep mp3
```
mp3         mp3lib    working   mp3lib MPEG layer-2, layer-3
ffmp3on4    ffmpeg    working   FFmpeg Multi-channel MPEG layer-3 on MP4 audio decoder  [mp3on4]
ffmp3       ffmpeg    working   FFmpeg MPEG layer-3 audio decoder  [mp3]
ffmp3adu    ffmpeg    working   FFmpeg MPEG layer-3 adu audio decoder  [mp3adu]
mp3acm      acm       working   MPEG layer-3  [l3codeca.acm]
```

Well that looks all ok to me and I am a little puzzled as to why the sound is failing. Is it possible that you could run the command again and paste the command and *full* terminal ouput here?

All the best,

Andrew

---

### Post by colau on 2009-05-08
> **mattgyver83 said:**
> you can also use ffmpeg from the command line, works rather well.

sudo ffmpeg -i video.flv video.avi
+1 for ffmpeg.

---

### Post by FakeOutdoorsman on 2009-05-08
> **mattgyver83 said:**
> you can also use ffmpeg from the command line, works rather well.

sudo ffmpeg -i video.flv video.avi
Using *sudo* for this command is unnecessary and a bad habit.  Your resulting file will be owned by *root* and not your user account.

---

### Post by crazypeppo on 2009-05-08
@colau, mattgyver83 ,FakeOutdoorsman - Are there any conflicts having both ffmpeg and mencoder installed same time?

@ Ringi - I have read all about avidemux never tried it, I read you could convert to many different file types, I just assumed it was a windows only...I'll have to try it next. Thanks

---

### Post by crazypeppo on 2009-05-09
andrew.46 - I have done this several times on several different .flv files of different sizes all of which have no audio. So, I chose to give you a small one for posting sake. Here's what happens:

linux@SSL-UB:~$ cd /home/linux/Desktop/Videos
linux@SSL-UB:~/Desktop/Videos$ mencoder -oac copy -ovc lavc -o panda.avi panda.flv
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2800+ (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x8cab4
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  29.917 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x31564C46  size:320x240  fps:29.92  ftime:=0.0334
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
audiocodec: framecopy (format=55 chans=2 rate=22050 bits=16 B/s=1000 sample-0)
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   2.0s     61f (11%)  0.00fps Trem:   0min   0mb  A-V:0.069 [92:13]
Skipping frame!
Pos:   2.3s     71f (11%)  0.00fps Trem:   0min   0mb  A-V:0.069 [128:17]
Skipping frame!
Pos:   2.7s     82f (17%)  0.00fps Trem:   0min   0mb  A-V:0.069 [155:20]
Skipping frame!
Pos:   3.2s    100f (17%)  0.00fps Trem:   0min   0mb  A-V:0.069 [176:24]
Skipping frame!
Pos:  15.6s    471f (99%) 315.47fps Trem:   0min   0mb  A-V:0.069 [279:41]]
Skipping frame!
Pos:  15.8s    477f (99%) 310.95fps Trem:   0min   0mb  A-V:0.054 [280:41]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  280.256 kbit/s  (35032 B/s)  size: 552706 bytes  15.777 secs  477 frames

Audio stream:   41.082 kbit/s  (5135 B/s)  size: 81828 bytes  15.935 secs
linux@SSL-UB:~/Desktop/Videos$ 

I have tried downloaded .flvs from different urls and none have audio this way...
I have default totem player opening files. Mplayer gives fatal error: error opening/inializing the selected video-out (-vo)device - which is why I was using totem.

I have been using WinFF as suggested with 100% success. Videos converted this way play fine in Totem but ONLY give audio in Mplayer and still have the fatal error...I am converting these to play on my WD HD multimedia player on my tv. All play fine on the tele after the WinFF transcoding.

I still have the question if both FFmpeg and Mencoder can be installed at once with no conflicts (I have both currently installed)...I see the FFmpeg opening in the terminal command even though I typed Mencoder...Is this regular? Are there any other obscure codecs I might need? I believe I have everything I need installed. 

So, I would still like to figure out why things went sour!?!
Thanks for your time on this btw.

---

### Post by andrew.46 on 2009-05-09
Hi crazypeppo,

> **crazypeppo said:**
> 

```
Video stream:  280.256 kbit/s  (35032 B/s)  size: 552706 bytes  15.777 secs  477 frames
Audio stream:   41.082 kbit/s  (5135 B/s)  size: 81828 bytes  15.935 secs
```

It looks like both video and audio have successfully been transcoded / copied. Can you run FFmpeg across the completed file just to double check the results:

```
ffmpeg -i panda.avi
```

and post the full results including the commandline here? It *should* show mpeg4 video and mp3 sound.

> Mplayer gives fatal error: error opening/inializing the selected video-out (-vo)device - which is why I was using totem.

On a side note you might be better to use a newer copy of MPlayer and I would suggest using the one generously provided by rvm from his PPA:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

and also install SMPlayer from the repository to get a decent gui. If you are happy to do this you may very well find that panda.avi will play successfully.

> I still have the question if both FFmpeg and Mencoder can be installed at once with no conflicts (I have both currently installed)

There should be no conflict. MPlayer / MEncoder use a static copy of FFmpeg and will not conflict with your copy of FFmpeg.

Hopefully this will help things along a little :-).

Andrew

---

### Post by isa.k on 2009-05-09
> **inobe said:**
> [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

Thanks for that, will give it a go :D

**EDIT:**
**[COLOR="Red"]Error: Wrong architecture (i386)[/COLOR]** #-o

Had the same problem with Vista 64 bit :(

Any FLV-MP4 converters that work with 64 bit Ubuntu (Jaunty Jackalope)?

[[IMG]http://img413.imageshack.us/img413/8840/screenshotpackageinstal.png[/IMG]](http://img413.imageshack.us/my.php?image=screenshotpackageinstal.png)

---

### Post by mattgyver83 on 2009-05-09
I have had no issues in that reguard.

---

### Post by isa.k on 2009-05-09
> **mattgyver83 said:**
> I have had no issues in that reguard.

So let me get this straight, you run **64bit** Ubuntu, and **not** an i386 version, and can also run this piece of conversion software with no hiccups?

---

### Post by Arup on 2009-05-09
FFMPEG is in Jaunty repos, the ones in x64 Jaunty is is total x64 version, not x32.

---

### Post by inobe on 2009-05-09
> **isa.k said:**
> So let me get this straight, you run **64bit** Ubuntu, and **not** an i386 version, and can also run this piece of conversion software with no hiccups?

[http://ubuntuforums.org/showthread.php?t=1095870](http://ubuntuforums.org/showthread.php?t=1095870)

---

### Post by crazypeppo on 2009-05-09
@andrew.46
"Can you run FFmpeg across the completed file just to double check the results:
```
ffmpeg -i panda.avi
```
and post the full results including the commandline here? It *should* show mpeg4 video and mp3 sound."


linux@SSL-UB:~$ cd /home/linux/Desktop/Movies
linux@SSL-UB:~/Desktop/Movies$ ffmpeg -i panda.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1,2000-2008 rice Bell, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 359.00 (359/1) -> 29.92 (359/12)
Input #0, avi, from 'panda.avi':
  Duration: 00:00:15.9, start: 0.000000, bitrate: 333 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 29.92 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, 8 kb/s
Must supply at least one output file
Hmmm...

---

### Post by andrew.46 on 2009-05-09
Hi crazypeppo,

> **crazypeppo said:**
> 
```
Input #0, avi, from 'panda.avi':
Duration: 00:00:15.9, start: 0.000000, bitrate: 333 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 29.92 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, stereo, 8 kb/s
```

This means that the copying and transcoding by MEncoder has been successful so your problem is in playback of this file. However 8 kb/s for the mp3 is a little unusual and I wonder if this could be the problem with playback.

Having said all that I have downloaded a similar flv file and tried several combinations of commands to convert with MEncoder and I have to say that the sound can be a little unpredictable. This is with simply copying the audio or by using mp3lame. I had much more reliable results with FFmpeg and syntax similar to this:

```
ffmpeg -i panda.flv -acodec copy -vcodec mpeg4 -sameq -vtag XVID output.avi
```

and this worked reliably all the time. Perhaps this might be a better option rather than persisting with MEncoder, which in my own experimentation seemed a little wayward? If you are interested the FakeOutdoorsman maintains a couple of guides:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

