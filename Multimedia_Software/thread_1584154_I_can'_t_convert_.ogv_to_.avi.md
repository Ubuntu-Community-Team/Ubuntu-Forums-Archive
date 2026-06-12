---
title: "I can' t convert .ogv to .avi"
date: 2010-09-28
forum: Multimedia Software
---

### Post by SpecialNeeds on 2010-09-28
I'm trying to convert a screencast of RecordMyDesktop, from .ogv to .avi.
I want to upload this video to youtube, but the problem that i found is:
When the convertion with mencoder is finished; the video resultant is longer that the original, the original video has 13:01 min and the converted video have 39:00, in wich only up to the minute 13:01 is reproducible.

And when I use Arista Transcoder, and convert the video to mp4 for example. The video resultant is normal, but when it's uploaded to , in the sound is ruined.

What I can do?

Thanks for the Answers!

---

### Post by ron999 on 2010-09-28
> **SpecialNeeds said:**
> 
What I can do?


What have you done so far?

---

### Post by SpecialNeeds on 2010-09-28
> **ron999 said:**
> What have you done so far?
Well I'm trying with Mencoder &  Arista Transcoder, and don't get good results.
The process of convert the video format takes time.
Why the Mencoder add more minutes to my original video?
I reinstall Mencoder and nothing happen.

I hope there is somebody that may help me.

I'm not a guru in Ubuntu, I'm just leaving out windows.
And sorry for my English I'm not a native English Speaker.

---

### Post by ron999 on 2010-09-28
Which command did you use with mencoder?

---

### Post by SeijiSensei on 2010-09-28
> **SpecialNeeds said:**
> Well I'm trying with Mencoder &  Arista Transcoder, and don't get good results.

If you ran mencoder yourself from the command line, post the command you entered so we can see what you're doing.

Do you need to convert the video codec as well?  How about the audio codec?

For instance, to create an file in the AVI container with the XviD video codec and the MP3 audio codec, I'd use a command like:

```
mencoder -o file.avi -ofps 24000/1001 -oac mp3lame -ovc xvid -xvidencopts pass=1 -vf harddup file.ogm

```

---

### Post by SpecialNeeds on 2010-09-28
> **ron999 said:**
> Which command did you use with mencoder?
I use:
mencoder originalvideo-xx.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o video-xx.avi

I found this statement in the web.
Where xx is a number of the video, I take a lot of screencast.

---

### Post by ron999 on 2010-09-28
> **SpecialNeeds said:**
> I use:
mencoder originalvideo-xx.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o video-xx.avi

I found this statement in the web.
Where xx is a number of the video, I take a lot of screencast.

OK
Try this command instead:-
```
mencoder originalvideo-xx.ogv -oac mp3lame -ovc lavc -o video-xx.avi 
```

---

### Post by SpecialNeeds on 2010-09-28
> **ron999 said:**
> OK
Try this command instead:-
```
mencoder originalvideo-xx.ogv -oac mp3lame -ovc lavc -o video-xx.avi 
```
Failed, again mencoder added 26 minutes more.
This is the log.
```
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x53a0105
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1360x768  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1360x768  fps:30.000  ftime:=0.0333
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 239.9 kbit/34.00% (ratio: 29990->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x98e0540]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1360 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1360x768 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.7s     22f ( 0%)  0.00fps Trem:   1min  64mb  A-V:0.067 [0:115]
Skipping frame!
Pos: 781.8s  23454f (100%) 111.50fps Trem:   0min  50mb  A-V:0.025 [416:122]
Invalid frame duration value (781.833/0.000 => -781.833). Defaulting to 0.033 sec.
Pos: 781.8s  23455f (100%) 111.50fps Trem:   0min  50mb  A-V:0.025 [416:122]
Skipping frame!
Pos: 781.8s  23456f (100%) 111.51fps Trem:   0min  50mb  A-V:0.028 [416:122]
Skipping frame!
Pos: 781.8s  23457f (100%) 111.51fps Trem:   0min  50mb  A-V:0.031 [416:122]
Skipping frame!
Pos: 781.8s  23458f (100%) 111.52fps Trem:   0min  50mb  A-V:0.035 [416:122]
23457 duplicate frame(s)!
Pos:1563.7s  23459f (100%) 111.43fps Trem:   0min  50mb  A-V:0.005 [208:122]
23459 duplicate frame(s)!
Pos:2345.7s  23460f (100%) 111.34fps Trem:   0min  50mb  A-V:78.205 [138:122]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  138.747 kbit/s  (17343 B/s)  size: 40682940 bytes  2345.733 secs  23460 frames

Audio stream:  122.160 kbit/s  (15269 B/s)  size: 11936743 bytes  781.714 secs

```

---

### Post by SpecialNeeds on 2010-09-28
> **SeijiSensei said:**
> If you ran mencoder yourself from the command line, post the command you entered so we can see what you're doing.

Do you need to convert the video codec as well?  How about the audio codec?

For instance, to create an file in the AVI container with the XviD video codec and the MP3 audio codec, I'd use a command like:

```
mencoder -o file.avi -ofps 24000/1001 -oac mp3lame -ovc xvid -xvidencopts pass=1 -vf harddup file.ogm

```
How know what's the audio codec that my Ubuntu use?
When I use Arista Transcoder and convert the original video.ogv to .mp4 the video and audio is fine, but when i upload this video to youtube, the sound in youtube is ruined.

---

### Post by ron999 on 2010-09-28
> MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x53a0105
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1360x768  24bpp  [COLOR="Red"]30.000 fps[/COLOR]    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1360x768  fps:30.000  ftime:=0.0333


Hi
With RecordMyDesktop you have got the 'Performance' set at **30** frames per second.
Maybe if you change it to **15** frames per second then use the mencoder command again.

---

### Post by SeijiSensei on 2010-09-28
> **SpecialNeeds said:**
> Failed, again mencoder added 26 minutes more.

26 minutes of what exactly?  What if you play the file with mplayer ("gmplayer /path/to/videofile.ogv")?  Does it think the file is 26 minutes longer than you do?  What does it show during that time?  I'm guessing it might be longer than you think it is.  You can truncate the file to 13:01 minutes by adding the "-endpos 00:13:01" parameter in mencoder.

> How know what's the audio codec that my Ubuntu use?

What matters are the codecs that mencoder knows about.  By default it supports a number of video and audio codecs.  You can see a list by typing "mencoder -ovc help" and "mencoder -oac help".  

I'd endorse ron999's suggestion of using "-ovc lavc" instead of "-ovc xvid".  Does that help?

---

### Post by SpecialNeeds on 2010-09-28
> **ron999 said:**
> Hi
With RecordMyDesktop you have got the 'Performance' set at **30** frames per second.
Maybe if you change it to **15** frames per second then use the mencoder command again.
:confused:But if I reduce the fps, the new video will not have good quality?
Well I'll tryng reducing fps.

---

### Post by SpecialNeeds on 2010-09-28
> **SeijiSensei said:**
> 26 minutes of what exactly?    

I'd endorse ron999's suggestion of using "-ovc lavc" instead of "-ovc xvid".  Does that help?
26 minutes of nothing, only the last picture of the last second without audio.
The change between "-ovc lavc" and "-ovc xvid" did nothing new.

---

### Post by SeijiSensei on 2010-09-28
> **SpecialNeeds said:**
> 26 minutes of nothing, only the last picture of the last second without audio.
The change between "-ovc lavc" and "-ovc xvid" did nothing new.

Something is funky with the source file.  Did you try playing the original in (g)mplayer?  How about the "-endpos" parameter?  Does that lop off the blank part, or does it truncate actual material?

---

### Post by SpecialNeeds on 2010-09-28
> **SeijiSensei said:**
> Something is funky with the source file.  Did you try playing the original in (g)mplayer?  How about the "-endpos" parameter?  Does that lop off the blank part, or does it truncate actual material?
The Gnome MPlayer can't play the original; but the Movie Player(I don't know if it's the correct name in English) can play the original.

How put the "-endpos" parameter?

---

### Post by SpecialNeeds on 2010-09-28
> **ron999 said:**
> Hi
With RecordMyDesktop you have got the 'Performance' set at **30** frames per second.
Maybe if you change it to **15** frames per second then use the mencoder command again.
I change to 15 fps and record a new screencast; the GNOME MPlayer play the new screencast with a screen blur with a lot of colors "illegible".
And the size of the new video grew, compared to the previous videos.

I use the statement:
```
mencoder video-xx.ogv -oac mp3lame -ovc lavc -o video-xx.avi
```
And the new video apparently works fine,the length is alright.
But the matter now is the quality of the new .avi This video in some seconds the screen tend to be blur.

---

### Post by ron999 on 2010-09-29
Hi
When you were using 30 frames per second mencoder was skipping frames.
That's why the extra minutes were added.
> MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x53a0105
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1360x768  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1360x768  fps:30.000  ftime:=0.0333
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 239.9 kbit/34.00% (ratio: 29990->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x98e0540]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1360 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1360x768 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.7s     22f ( 0%)  0.00fps Trem:   1min  64mb  A-V:0.067 [0:115]
[COLOR="Red"]Skipping frame!
Pos: 781.8s  23454f (100%) 111.50fps Trem:   0min  50mb  A-V:0.025 [416:122]
Invalid frame duration value (781.833/0.000 => -781.833). Defaulting to 0.033 sec.
Pos: 781.8s  23455f (100%) 111.50fps Trem:   0min  50mb  A-V:0.025 [416:122]
Skipping frame!
Pos: 781.8s  23456f (100%) 111.51fps Trem:   0min  50mb  A-V:0.028 [416:122]
Skipping frame!
Pos: 781.8s  23457f (100%) 111.51fps Trem:   0min  50mb  A-V:0.031 [416:122]
Skipping frame!
Pos: 781.8s  23458f (100%) 111.52fps Trem:   0min  50mb  A-V:0.035 [416:122]
23457 duplicate frame(s)!
Pos:1563.7s  23459f (100%) 111.43fps Trem:   0min  50mb  A-V:0.005 [208:122]
23459 duplicate frame(s)![/COLOR]
Pos:2345.7s  23460f (100%) 111.34fps Trem:   0min  50mb  A-V:78.205 [138:122]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  138.747 kbit/s  (17343 B/s)  size: 40682940 bytes  2345.733 secs  23460 frames

Audio stream:  122.160 kbit/s  (15269 B/s)  size: 11936743 bytes  781.714 secs

If the quality isn't good enough using 15 frames per second then try other numbers such as 20 or 25.
Try to get the best quality without skipping any frames.

---

### Post by SpecialNeeds on 2010-09-29
> **ron999 said:**
> Hi
When you were using 30 frames per second mencoder was skipping frames.
That's why the extra minutes were added.


If the quality isn't good enough using 15 frames per second then try other numbers such as 20 or 25.
Try to get the best quality without skipping any frames.
Well everything went well, the new video is fine, and I use Arista Transcoder to convert the .ogv in .mp4 twice videos plays fine.
And then uploaded it(.mp4) to youtube, but in youtube the original audio practically disappears and I hear noise.

And now i notice that can't use mencoder to convert a video:

```
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x19fd05
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1360x768  24bpp  20.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1360x768  fps:20.000  ftime:=0.0500
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22500 Hz, 1 ch, s16le, 90.0 kbit/25.00% (ratio: 11248->45000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x932f820]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1360 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1360x768 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).
If everything else fails, try a preset.
Exiting...

```
I have ffmpeg :confused:

---

### Post by ron999 on 2010-09-30
> **SpecialNeeds said:**
> 
I have ffmpeg :confused:

Hi
If you have an _**updated version of ffmpeg**_ then this command will convert the RecordMyDesktop ogv file into a suitable format for YouTube:-

```
ffmpeg -i video-xx.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy video-xx.mkv
```

To update ffmpeg (and x264) the tutorial is here:-
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")

---

### Post by psycho5 on 2010-09-30
Perhaps recordmydesktop didn't finish encoding the file or it was interrupted. 

You can use WinFF which is ffmpeg with a GUI and it has alot of options you can convert to. Just make sure you've got the necessary mp3lame or fluendo codecs to convert.

---

### Post by SpecialNeeds on 2010-09-30
> **psycho5 said:**
> Perhaps recordmydesktop didn't finish encoding the file or it was interrupted. 

You can use WinFF which is ffmpeg with a GUI and it has alot of options you can convert to. Just make sure you've got the necessary mp3lame or fluendo codecs to convert.

Well must be happen something.

Yesterday I just uninstall WinFF
and Install Jackd(I don't know why? I think that could be help. And edit **/etc/security/limits.conf** for Jack and nothing more.)
```
sudo apt-get install jackd qjackctl
```

But yesterday remember that I can convert with Winff, but today appears the next log:

```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[ogg @ 0x8d49a60]Could not find codec parameters (Invalid Codec type -1)
[ogg @ 0x8d49a60]Could not find codec parameters (Video: theora, 1360x768)
Input #0, ogg, from '/home/user/Videos/video-26.ogv':
  Duration: 00:00:09.65, start: 0.000000, bitrate: 1411 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, 1360x768, PAR 1:1 DAR 85:48, 20 tbr, 20 tbn, 20 tbc
    Stream #0.2: Audio: vorbis, 22500 Hz, mono, s16, 89 kb/s
File '/home/user/Videos/protovideo-26.avi' already exists. Overwrite ? [y/N] y
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context

```

---

### Post by SpecialNeeds on 2010-09-30
> **ron999 said:**
> Hi
If you have an _**updated version of ffmpeg**_ then this command will convert the RecordMyDesktop ogv file into a suitable format for YouTube:-

```
ffmpeg -i video-xx.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy video-xx.mkv
```

To update ffmpeg (and x264) the tutorial is here:-
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")
Don't work, and the log that appears is:
```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[ogg @ 0x9498a60]Could not find codec parameters (Invalid Codec type -1)
[ogg @ 0x9498a60]Could not find codec parameters (Video: theora, 1360x768)
Input #0, ogg, from 'protovideo-26.ogv':
  Duration: 00:00:09.65, start: 0.000000, bitrate: 1411 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, 1360x768, PAR 1:1 DAR 85:48, 20 tbr, 20 tbn, 20 tbc
    Stream #0.2: Audio: vorbis, 22500 Hz, mono, s16, 89 kb/s
File for preset 'medium' not found

```


I think that the matter could be about something codec of audio when the video is converted, because yesterday I miss and upload a .ogv video to youtube, and note that the audio is fine, but the video obviously does not appear, and when upload the same video "converted to .mp4" the audio of the new youtube video is full of noise.

---

### Post by ron999 on 2010-09-30
> **SpecialNeeds said:**
> Don't work, and the log that appears is:
```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) [COLOR="Red"]2000-2009[/COLOR] Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[ogg @ 0x9498a60]Could not find codec parameters (Invalid Codec type -1)
[ogg @ 0x9498a60]Could not find codec parameters (Video: theora, 1360x768)
Input #0, ogg, from 'protovideo-26.ogv':
  Duration: 00:00:09.65, start: 0.000000, bitrate: 1411 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, 1360x768, PAR 1:1 DAR 85:48, 20 tbr, 20 tbn, 20 tbc
    Stream #0.2: Audio: vorbis, 22500 Hz, mono, s16, 89 kb/s
File for preset 'medium' not found

```


Because it's not an updated version.

---

### Post by SpecialNeeds on 2010-09-30
> **ron999 said:**
> Because it's not an updated version.
Then I just do:
[]("http://ubuntu-ky.ubuntuforums.org/sh...ng+FFmpeg+x264")
to Update.
But why today I can't use Mencoder? Yesterday the Mencoder works right, but the the new .avi had low quality.
And today when I use:
```
mencoder video.ogv -oac mp3lame -ovc  lavc -o newvideo.avi

```
Don't work and appear:
```
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x19fd05
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1360x768  24bpp  20.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1360x768  fps:20.000  ftime:=0.0500
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22500 Hz, 1 ch, s16le, 90.0 kbit/25.00% (ratio: 11248->45000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x8c7c820]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1360 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1360x768 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).
If everything else fails, try a preset.
Exiting...

```
What's mean? 
[B]Missing extradata!
Could not open codec.
VDecoder init failed :([/B]


**I need learn how to do backup.**
I just did:
[LIST=1]
[*]Uninstall WinFF
[*]Install Jackd
[/LIST]
What's mean? 
[B]Missing extradata!
Could not open codec.
VDecoder init failed :([/B]

---

