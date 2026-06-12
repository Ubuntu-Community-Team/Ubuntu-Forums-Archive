---
title: "FFmpeg script for DVD to mp4"
date: 2010-08-31
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2010-08-31
Morning all , I want to convert DVD movie to mp4 using x264 and aac. I'm having some issues with GUI apps.
 
Does anybody have a ffmpeg terminal script to do this ?
I use ffmpeg in terminal for all my single file converts and prefer to use it but don't know how to use it in terminal for a DVD movie to mp4.
 
Thank you

---

### Post by FakeOutdoorsman on 2010-08-31
[Handbrake](http://handbrake.fr/) might be the easiest tool to do this.  It has a GUI.

Or if you prefer FFmpeg.  This example combines two vob files because the movie was split into several vobs.
```
ffmpeg -i concat:"/media/dvd/VIDEO_TS/VTS_01_1.VOB|/media/dvd/VIDEO_TS/VTS_01_2.VOB" \
-acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre slow -crf 24 -threads 0 output.mp4
```
You'll probably need to compile FFmpeg to use that example:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

This example probably won't work on an encrypted DVD.  See vobcopy (and possibly tccat or mplayer) for that additional step.

---

### Post by Ghost_Mazal on 2010-08-31
> **FakeOutdoorsman said:**
> [Handbrake]("http://handbrake.fr/") might be the easiest tool to do this. It has a GUI.
 
Or if you prefer FFmpeg. This example combines two vob files because the movie was split into several vobs.
```
ffmpeg -i concat:"/media/dvd/VIDEO_TS/VTS_01_1.VOB|/media/dvd/VIDEO_TS/VTS_01_2.VOB" \
-acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre slow -crf 24 -threads 0 output.mp4
```
You'll probably need to compile FFmpeg to use that example:
 
[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")
 
This example probably won't work on an encrypted DVD. See vobcopy (and possibly tccat or mplayer) for that additional step.
 
Thanx , that example is exactly what I need :) I knew how to do 1 vob file but didn't know how to combine vob files in ffmpeg.
 
My ffmpeg is already compiled and working using your guide ;)
 
Will give that example a go thank you.

---

### Post by Ghost_Mazal on 2010-08-31
Will this work if I am standing in the folder where the .VOB's are ?
 
```
 
for f in *.VOB; do ffmpeg -i "$f" -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre fast 
-crf 21 -threads 0 moviename.mp4; done

```
 
Or will that just overwrite the output file with each VOB.
 
Just trying to find a way to make the input a bit easier rather than to specify each input file.

---

### Post by Ghost_Mazal on 2010-08-31
Or this maybe :
 
```
 
for f in *.VOB; do ffmpeg -i concat:"$f" -acodec libfaac -ac 2 -ab 128k -vcodec libx264 
-vpre fast -crf 21 -threads 0 moviename.mp4; done

```

---

### Post by Ghost_Mazal on 2010-08-31
Ok all 3 those scripts of mine was flawed. But with some fiddling this straight forward one works perfect for someone like me who always copies the files to a hdd folder first:

```
cat *.VOB > moviename.vob; ffmpeg -i moviename.vob -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre fast -crf 20 -threads 0 moviename.mp4
```

Standing in the folder where the vob files is.

---

### Post by FakeOutdoorsman on 2010-08-31
I didn't know you already had the vobs on hard drive.  To avoid a large intermediate file you could also try:
```
cat *.vob | ffmpeg -i - -acodec ...
```
I believe this is similar to the FFmpeg *concat* protocol as shown in my earlier example.

---

### Post by Ghost_Mazal on 2010-08-31
Will try that also thanx... (what's the difference between the | and ; ) I'm still very new to the scripting thing.

---

### Post by FakeOutdoorsman on 2010-08-31
The | is a pipe, meaning that *cat* is giving it's output to *FFmpeg* instead of outputting to a file. The ; means "do the first command and then do this next command".

---

### Post by Ghost_Mazal on 2010-09-04
And all of a sudden ffmpeg doesn't work anymore :( After doing a lot of converts with no problems , now suddenly the output file's audio and video is out of sync. Still using the same commands. Now what ??????

---

### Post by FakeOutdoorsman on 2010-09-04
Show your command and the complete output.  It will show some useful information.

---

### Post by Ghost_Mazal on 2010-09-04
```
cat *.VOB | ffmpeg -i - -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre fast -crf 20 -threads 0 moviename.mp4

FFmpeg version SVN-r24953, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 28 2010 07:59:27 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.87. 0 / 52.87. 0
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.38. 1 /  1.38. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0x15ca470] max_analyze_duration reached
[mpeg @ 0x15ca470] Estimating duration from bitrate, this may be inaccurate
Input #0, mpeg, from 'pipe:':
  Duration: N/A, start: 0.287267, bitrate: 10568 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 9800 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
[buffer @ 0x1696c00] w:720 h:576 pixfmt:yuv420p
[libx264 @ 0x15cbc70] using SAR=64/45
[libx264 @ 0x15cbc70] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x15cbc70] profile High, level 3.0
[libx264 @ 0x15cbc70] 264 - core 104 r1703 cd21d05 - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=20.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
Output #0, mp4, to 'moviename.mp4':
  Metadata:
    encoder         : Lavf52.78.3
    Stream #0.0: Video: libx264, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=10-51, 200 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, 2 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
^Cframe=  191 fps= 55 q=22.0 Lsize=     918kB time=7.30 bitrate=1030.3kbits/s
```

It aslo happens when I do just 1 file also starting with just ffmpeg -i .......

---

### Post by FakeOutdoorsman on 2010-09-04
> **Ghost_Mazal said:**
> It aslo happens when I do just 1 file also starting with just ffmpeg -i .......

You mean it also de-syncs if you kick the *cat* and just do something like the following?
```
ffmpeg -i input.vob -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre fast -crf 20 \
-threads 0 moviename.mp4
```

Does it de-sync in all players?

---

### Post by Ghost_Mazal on 2010-09-04
Correct , it happens even with just 1 file like that. And yes , in all players.

The only time it works is when it's a small file like 100mb or so.

I don't get it , everything was working fine and suddenly it started.

---

### Post by FakeOutdoorsman on 2010-09-04
I'm not sure why it's not synced, but you can experiment with other encoders, containers, and options.

Try *-aq* instead of *-ab*:
```
ffmpeg -i input.vob -acodec libfaac -ac 2 -aq 100 -vcodec libx264 -vpre fast -crf 20 \
-threads 0 moviename.mp4
```

Try another audio encoder and output container:
```
ffmpeg -i input.vob -acodec libmp3lame -ac 2 -aq 4 -vcodec libx264 -vpre fast -crf 20 \
-threads 0 moviename.mkv
```

Or check out the *-async* option, but unfortunately I haven't used it much myself.

---

### Post by procras on 2010-09-04
Handbrake

[http://www.packtpub.com/article/compiling-and-running-handbrake-in-ubuntu]("http://www.packtpub.com/article/compiling-and-running-handbrake-in-ubuntu")

---

### Post by Ghost_Mazal on 2010-09-05
> **FakeOutdoorsman said:**
> I'm not sure why it's not synced, but you can experiment with other encoders, containers, and options.

Try *-aq* instead of *-ab*:
```
ffmpeg -i input.vob -acodec libfaac -ac 2 -aq 100 -vcodec libx264 -vpre fast -crf 20 \
-threads 0 moviename.mp4
```Try another audio encoder and output container:
```
ffmpeg -i input.vob -acodec libmp3lame -ac 2 -aq 4 -vcodec libx264 -vpre fast -crf 20 \
-threads 0 moviename.mkv
```Or check out the *-async* option, but unfortunately I haven't used it much myself.

Ok when I try the -aq 4 option as in the above example the audio is all messed up. Sounds like a broken mic or kinda like running water.

I can't use other encoders and containers. This project of mine is for converting my movies and music videos for my PS3 that is my media centre and it needs the h264 and aac

procras Handbrake works fine. I guess I will just use handbrake for the movies and ffmpeg for the music videos that is much smaller files.
Just ticks me off that something that was working fine suddenly stops working.

---

### Post by Ghost_Mazal on 2010-09-06
If I want to take a file that is currently 720x576 to 1920 x 1080 so that it displays properly on a HD screen what should I add to: (the 720 x 576 looks pretty bad on a HD display)
 
a) The ffmpeg script and
 
b) In handbrake. Can't find a size setting in handbrake.

---

### Post by FakeOutdoorsman on 2010-09-06
> **Ghost_Mazal said:**
> Ok when I try the -aq 4 option as in the above example the audio is all messed up. Sounds like a broken mic or kinda like running water.
How strange.  I've never experienced that before.  *-aq 4* should go with *-acodec libmp3lame*, while *-aq 100* is for *-acodec libfaac*.

> **Ghost_Mazal said:**
> If I want to take a file that is currently 720x576 to 1920 x 1080 so that it displays properly on a HD screen what should I add to: (the 720 x 576 looks pretty bad on a HD display)
 
a) The ffmpeg script
I doubt upscaling and re-encoding will make it look any better than using a good player to upscale or resize, and 720x576 doesn't scale to 1920x1080 without changing the aspect ratio (or dealing with padding or cropping). But you can always try this:
```
ffmpeg -i input.vob -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre fast -crf 20 \
-threads 0 -vf scale=-1:1080 moviename.mp4
```
or:
```
-vf scale=1920:-1
```
This uses the *scale* filter to automatically determine the appropriate width or height value in relation to the other declared value while keeping the aspect ratio.

---

