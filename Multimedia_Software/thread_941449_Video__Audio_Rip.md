---
title: "Video / Audio Rip"
date: 2008-10-08
forum: Multimedia Software
---

### Post by RJWEcology on 2008-10-08
Ahoy Hoy! 

I want to rip the audio from a youtube video I uploaded but don't have anymore. Any suggestion as to how I could do this?

Any help would be much appreciated. 

Rich

---

### Post by minky311 on 2008-10-08
I usually go to this website [http://www.zamzar.com]("http://www.zamzar.com") click on the download video tab and put in the url of the video I want converted and choose mp3.

---

### Post by RJWEcology on 2008-10-08
Thanks. I've tried it and I'm now waiting for the file to be emailed to me.

---

### Post by aeiah on 2008-10-08
if you are wanting to do this with a lot of videos, you might prefer using a scripted solution. there's a youtube-dl script knocking around somewhere. if you combine that with a simple ffmpeg conversion command you could just enter the youtube url and it'd spit out an mp3 for you onto your desktop.

---

### Post by SuperSonic4 on 2008-10-08
How would I go about creating a ffmpeg script for such a thing? For example for 160kbps mp3.

At the moment I use pacpl audio converter (not in the repos) or freez flv to mp3 converter under wine

---

### Post by FakeOutdoorsman on 2008-10-08
FFmpeg can just copy the audio stream without re-encoding.  This preserves the quality.  First use ffmpeg to find more info on the file:
```
[frink@hedron encode]$ ffmpeg -i input.flv
Input #0, flv, from 'input.flv':
Duration: 00:08:04.57, start: 0.000000, bitrate: 64 kb/s
Stream #0.0: Video: flv, yuv420p, 320x240, 29.92 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
```
It contains mp3, so now just copy the audio:
```
ffmpeg -i input.flv -acodec copy output.mp3
```

---

### Post by Zach-Warlock on 2009-06-09
I have been looking for this information for along time now and when I get home from school I'll try this out.
 
thanks:p

---

### Post by Zach-Warlock on 2009-06-09
that did not work for me but i will keep trying and find something that dose 
thanks any way

---

### Post by andrew.46 on 2009-06-10
Hi Zach-Warlock,

> **Zach-Warlock said:**
> that did not work for me but i will keep trying and find something that dose 
thanks any way

The FFmpeg syntax that FakeOutdoorsman gave should be pretty bulletproof. If you are interested in getting it going could you run the suggested line and post the *[I]complete*[/I] terminal output including the actual command here on the forum?

All the best,

Andrew

---

### Post by rading on 2010-01-15
Wow!!! Its "little" things like this that have vindicated my decision to jump to nix...

Worked perfectly!!

Never seen windows extract audio from a 700mb video file in less than a minute!! Unbelievable.....

Thanks alot for this.

---

### Post by klausner on 2010-01-31
> **Zach-Warlock said:**
> that did not work for me but i will keep trying and find something that dose 
thanks any way

The syntax suggested didn't work for me either, trying to rip audio from a MP4 video. Here's the message output:> $ ffmpeg -i TFC.mp4 -acodec copy TFC.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1

Seems stream 1 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'TFC.mp4':
  Duration: 00:04:21.66, start: 0.000000, bitrate: 324 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 320x240, 29.97 tbr, 29.97 tbn, 59.94 tbc
Output #0, mp3, to 'TFC.mp3':
    Stream #0.0(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo, s16
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    3982kB time=261.64 bitrate= 124.7kbits/s    
video:0kB audio:3982kB global headers:0kB muxing overhead 0.000785%
All it produced was a garbage file that generated a "click".

On a whim, I tried feeding the video file to soundconverter, which worked like a charm! No muss, no fuss. =D>

---

### Post by fivebells on 2011-01-14
> **klausner said:**
> The syntax suggested didn't work for me either, trying to rip audio from a MP4 video.  The problem was the "-acodec copy" clause combined with the ".mp3" suffix on the output file.  If you look at the ffmpeg analysis of the input file, you can see that the audio codec was aac.  The mp3 suffix implicitly requested mp3 output, which was inconsistent with the -acodec request for a direct copy of the audio stream in aac format.  If you had left off the "-acodec copy" or changed the output suffix to ".aac", it likely would have worked perfectly.

---

### Post by lisati on 2011-06-15
If you uploaded the video yourself, you should be able to log into Youtube and download it.

---

### Post by andrea000 on 2011-06-16
> **klausner said:**
> The syntax suggested didn't work for me either, trying to rip audio from a MP4 video. Here's the message output:
All it produced was a garbage file that generated a "click".

On a whim, I tried feeding the video file to soundconverter, which worked like a charm! No muss, no fuss. =D>

I think you need to recompile ffmpeg and add [COLOR="Red"]--enable-libmp3lame[/COLOR] to
your configuration.

---

### Post by klausner on 2011-06-16
.

---

