---
title: "Trim vob files?"
date: 2009-08-10
forum: Multimedia Software
---

### Post by Cephi on 2009-08-10
How do you do trim a vob file?  I just want to make short clips out of long vob files (I'm editing old home movies).  

This seems like it should be so simple, but I've spent hours trying every program I can get my hands on, to no avail.  Cinelerra, Kino, Kdenlive, Blender, AviDemux, Open Movie Editor, ManDVD, ffmpeg, you name it I've spent a few hours fussing with it.  AviDemux seemed my best hope, but I get no audio.  (My audio output, in Preferences, is set to "dummy" and it gives me no other options.)

Joining clips would be nice, too, but isn't necessary, since I gather that vobs can be joined simply by "cat vob1.vob vob2.vob > finalvob.vob".  Which is part of why it's unbelievable to me that the splitting part is turning out to be so difficult.  Ideas? :confused:

PS: I don't want to transcode. I want to prevent any degredation.

---

### Post by arky on 2009-08-10
Since you have tried almost all video editing tools. I point to you to something recently read about in LJ

[http://www.linuxjournal.com/content/it-lives-video-editing-foss-movie-makers](http://www.linuxjournal.com/content/it-lives-video-editing-foss-movie-makers)

---

### Post by FakeOutdoorsman on 2009-08-10
FFmpeg should be able to do this:
```
ffmpeg -ss 00:23:45:00 -t 00:00:20:00 -i input.vob -acodec copy -vcodec copy output.vob
```
The *-ss* option is the time offset. The above example is in the hours:minutes:seconds:frames format and would ignore the first 23 minutes and 45 seconds of video.  The *-t* option is the length of video you want to save.  Yes, VOB can be joined with cat.  This is a direct stream copy and not a re-encode due to the *-vcodec copy* and *-acodec copy* options.

---

### Post by Cephi on 2009-08-10
> **FakeOutdoorsman said:**
> FFmpeg should be able to do this:
```
ffmpeg -ss 00:23:45:00 -t 00:00:20:00 -i input.vob -acodec copy -vcodec copy output.vob
```
The *-ss* option is the time offset. The above example is in the hours:minutes:seconds:frames format and would ignore the first 23 minutes and 45 seconds of video.  The *-t* option is the length of video you want to save.  Yes, VOB can be joined with cat.  This is a direct stream copy and not a re-encode due to the *-vcodec copy* and *-acodec copy* options.

Ah that seemed great (I didn't know about -*codec copy), but it outputs for me an empty file.  In the terminal output, it says that it cannot seek to the relevant position.  Maybe relatedly, when I play the files in vlc, vlc can't index the time properly.  If I skip ahead, for example, the time index doesn't skip ahead as it should.  Here's the whole terminal output:

> 
ffmpeg -ss 120 -t 105 -i vts_04_1.vob -acodec copy -vcodec copy clip1.vob
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
vts_04_1.vob: could not seek to position 120.333

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from 'vts_04_1.vob':
  Duration: 00:00:02.95, start: 0.333000, bitrate: 518662 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 6124 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
File 'clip1.vob' already exists. Overwrite ? [y/N] y
Output #0, svcd, to 'clip1.vob':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 6124 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=    0 fps=  0 q=-1.0 Lsize=       0kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead nan%


also, i've tried three different formats for the -ss and -t options, including the one you used.

---

### Post by FakeOutdoorsman on 2009-08-10
I think I've come across this issue before when working with a VOB made by vobcopy, but I don't remember what I did to fix it.  I may have switched to mplayer to grab the VOB:
```
mplayer dvd://2 -v -dumpstream -dumpfile output.vob
```

Anyway, do you get the same error if you decode first and then seek?
```
ffmpeg -i vts_04_1.vob -ss 120 -t 105 -acodec copy -vcodec copy clip1.vob
```

---

### Post by Cephi on 2009-08-12
> **FakeOutdoorsman said:**
> 
Anyway, do you get the same error if you decode first and then seek?
```
ffmpeg -i vts_04_1.vob -ss 120 -t 105 -acodec copy -vcodec copy clip1.vob
```

Hey hey, that seems to do the trick!  Thanks a bunch!

Incidentally I also tried copying the original file with

```
ffmpeg -i vts_04_1.vob -acodec copy -vcodec copy copy_of_vts_04_1.vob
```

to see if that would allow vlc to time-index the copy properly.  That seems to work too.

---

### Post by alphacrucis2 on 2009-08-12
> **Cephi said:**
> How do you do trim a vob file?  I just want to make short clips out of long vob files (I'm editing old home movies).  

This seems like it should be so simple, but I've spent hours trying every program I can get my hands on, to no avail.  Cinelerra, Kino, Kdenlive, Blender, AviDemux, Open Movie Editor, ManDVD, ffmpeg, you name it I've spent a few hours fussing with it.  AviDemux seemed my best hope, but I get no audio.  (My audio output, in Preferences, is set to "dummy" and it gives me no other options.)

Joining clips would be nice, too, but isn't necessary, since I gather that vobs can be joined simply by "cat vob1.vob vob2.vob > finalvob.vob".  Which is part of why it's unbelievable to me that the splitting part is turning out to be so difficult.  Ideas? :confused:

PS: I don't want to transcode. I want to prevent any degredation.

With Avidemux try setting Video and Audio to copy, set Format to MPEG-PS (A + V). Pretty sure that has worked for me in the past.

---

### Post by Cephi on 2009-08-12
> **alphacrucis2 said:**
> With Avidemux try setting Video and Audio to copy, set Format to MPEG-PS (A + V). Pretty sure that has worked for me in the past.


Already tried it.  Still have only "dummy" as an option for audio output, and hence no sound.  Ah well.

---

### Post by andrew.46 on 2009-08-13
Hi Fakeoutdoorsman,

> **FakeOutdoorsman said:**
> I think I've come across this issue before when working with a VOB made by vobcopy, but I don't remember what I did to fix it.

I have also encountered some odd problems with vobs made with both vobcopy *and* MPlayer. The solution I came up with was to use one of the transcode tools tccat which seems much more reliable:

```
tccat -i /dev/dvd -d 2 -T 1,-1,1 > outfile.vob
```

Definitely not the most user friendly program in the world that one but using tccat I have had less trouble with subsequent encoding/extraction of the generated vob.

Andrew

---

### Post by Cephi on 2009-08-13
> **andrew.46 said:**
> Hi Fakeoutdoorsman,



I have also encountered some odd problems with vobs made with both vobcopy *and* MPlayer. The solution I came up with was to use one of the transcode tools tccat which seems much more reliable:

```
tccat -i /dev/dvd -d 2 -T 1,-1,1 > outfile.vob
```

Definitely not the most user friendly program in the world that one but using tccat I have had less trouble with subsequent encoding/extraction of the generated vob.

Andrew

hmm, tried it and i still get the same time indexing problem. but ripping the vobs with

```
ffmpeg -i /dev/dvd/video_ts/inputfile.vob -acodec copy -vcodec copy outputfile.vob
```

does the trick for me.

(or actually, in my case,

```
ffmpeg -i /media/mountediso/video_ts/inputfile.vob -deinterlace -acodec copy -vcodec mpeg2video -b 6124k outputfile.vob 
```

for deinterlacing.)

---

### Post by FakeOutdoorsman on 2009-08-13
> **andrew.46 said:**
> Hi Fakeoutdoorsman,



I have also encountered some odd problems with vobs made with both vobcopy *and* MPlayer. The solution I came up with was to use one of the transcode tools tccat which seems much more reliable:

```
tccat -i /dev/dvd -d 2 -T 1,-1,1 > outfile.vob
```

Definitely not the most user friendly program in the world that one but using tccat I have had less trouble with subsequent encoding/extraction of the generated vob.

Andrew

Excellent.  I will have to try this one next time.  Thanks, Andrew.

---

### Post by MySchizoBuddy on 2009-12-02
how to do it in batch mode i have like 80 vob files that all need trimming

---

