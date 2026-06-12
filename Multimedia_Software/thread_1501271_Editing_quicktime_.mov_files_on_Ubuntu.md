---
title: "Editing quicktime .mov files on Ubuntu"
date: 2010-06-04
forum: Multimedia Software
---

### Post by NUboon2Age on 2010-06-04
I created a  quicktime .mov movie file in iMovie on a Mac (that is not available anymore) and I want to 1) play & 2) edit the movie.  I'd be happy to use a different format if I can figure out how to change it.  Has anyone else done this?

Edit:  If you skip down to post #16 you'll see **I discovered it actually isn't a matter of editing a .mov file**, but it turns out I don't have a properly exported quicktime .mov file.  Instead I have (I'm not sure but I think its [iMovie ver. 4]("http://en.wikipedia.org/wiki/IMovie#Features_of_iMovie_4").) 1) an .iMovieProj text file that lists the cuts by frame in and frame out, 2) an .mov file that isn't the complete file I thought it was and 3) a folder of all the clips that are in Apple's Quicktime DV format. In this thread people taught me about transcoding from the Apple's Quicktime DV format to liberated formats easier to work with.  Given this knowledge and **since I have a list of the cuts I'm asking if people could recommend a Linux video editor that would be easy to enter the tedious frame in, frame out info so I could reassemble the video.**

---

### Post by Unterseeboot_234 on 2010-06-04
I use ffmpeg. If you don't have that library installed do that first, it is in the repositories. Also, ffmpeg relies on other libs to do audio. ffmpeg is a command-line tool. Here are the options I use to make .avi with a soundtrack.

```
ffmpeg -i inputfile.mov -sameq -vcodec msmpeg4v2 -acodec libmp3lame outputfile.avi
```

Note that I am using lame -- yet another repository install -- for the audio conversion. You may have to google to find other recipes for the option parameters.

I will comment that many people with new cameras have .mov files they cannot convert on Windows products. Folks come to me to convert because I have the Ubuntu that can do it.

---

### Post by NUboon2Age on 2010-06-04
> **Unterseeboot_234 said:**
> I use ffmpeg. If you don't have that library installed do that first, it is in the repositories. Also, ffmpeg relies on other libs to do audio. ffmpeg is a command-line tool. Here are the options I use to make .avi with a soundtrack.

```
ffmpeg -i inputfile.mov -sameq -vcodec msmpeg4v2 -acodec libmp3lame outputfile.avi
```

Note that I am using lame -- yet another repository install -- for the audio conversion. You may have to google to find other recipes for the option parameters.

I will comment that many people with new cameras have .mov files they cannot convert on Windows products. Folks come to me to convert because I have the Ubuntu that can do it.

Many thanks Unterseeboot_234!  I think that really put me on the right track.

Can you help me understand this output and how to fix it when I tried the line you provided.

I guess part of it is for some reason it wants some other clips.  Those I can easily provide, but what are the other errors and how do I remedy them?

The three lines that seem to be errors not related to missing clips are:

```

    Stream #0.3(eng): Data: 0x0000
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
```

Here's the whole thing:
```
$ ffmpeg -i UNVC.mov -sameq -vcodec msmpeg4v2 -acodec libmp3lame UNVC2.avi
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
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9ccba60]sample aspect ratio already set to 10:11, overriding by 'pasp' atom
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9ccba60]stream 0, error opening file /Movies/UNVC/Media/Clip 79: No such file or directory
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9ccba60]multiple edit list entries, a/v desync might occur, patch welcome
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9ccba60]stream 1, error opening file /Movies/UNVC/Media/Clip 78: No such file or directory
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9ccba60]multiple edit list entries, a/v desync might occur, patch welcome
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9ccba60]stream 2, error opening file /Movies/UNVC/Media/Clip 79: No such file or directory
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'UNVC.mov':
  Duration: 02:51:28.82, start: 0.000000, bitrate: 3 kb/s
    Stream #0.0(eng): Video: dvvideo, 720x480, PAR 40:33 DAR 20:11, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
    Stream #0.2(eng): Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.3(eng): Data: 0x0000
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
```

---

### Post by NUboon2Age on 2010-06-04
My major misunderstanding in all this was to think that the .mov file was a complete stand-alone file by itself.  I guess it must be essentially sort of an orchestration file that points to various clips.  Whatever I end up with needs to be a complete standalone video and audio file (actually in the end it will probably need to be a flash video .flv file so that I can put it on YouTube).

Previously VLC had given me an error message:
```
No suitable decoder module:
VLC does not support the audio or video format "vdva". Unfortunately there is no way for you to fix this.
```

It turns out vdva is some sort of audio format with variable volume or something.  I didn't find very much info on that.  But it made me think the basic problem was this missing vdva codec.

But now that I had the output from ffmpeg to analyze I had another error message to hunt for. I googled for "swScaler: Unknown format is not supported as input pixel format" and found a number of things including this; 
[http://www.mediamosa.org/forum/viewtopic.php?f=13&t=76](http://www.mediamosa.org/forum/viewtopic.php?f=13&t=76)

> The last 3 lines are of interest:

    Stream #0.0: Video: IV41 / 0x31345649, 256x240, 30 tbr, 30 tbn, 30 tbc
    swScaler: Unknown format is not supported as input pixel format
    Cannot get re-sampling context

This means that a codec is missing, here IV41(Intel Indeo 4).
Intel Indeo versions 2 and 3 have decoders in FFmpeg. Indeo version 4 and 5 are not supported by any open source decoders. So we cannot trans-code this file.

Your best chance is to re-encode to a codec that is supported by FFMPEG with a commercial package that does support the missing codec.


So I got the clue that if the last three lines might tell me if I  was missing a codec I should look at them.  

 "Stream #0.3(eng): Data: 0x0000"

```
    Stream #0.3(eng): Data: 0x0000
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
```

---

### Post by FakeOutdoorsman on 2010-06-04
> **NUboon2Age said:**
> I created a  quicktime .mov movie file in iMovie on a Mac (that is not available anymore) and I want to 1) play & 2) edit the movie.  I'd be happy to use a different format if I can figure out how to change it.  Has anyone else done this?

Kino is an older editor designed for DV video (which is contained in your input file, *UNVC.mov*, according to the FFmpeg info you provided).  A more recent editor is Kdenlive.  Before converting you should see if either of these editors can handle your input file.  DV is an editor friendly format, but your input container format may be specific to iMovie.

If these editors don't like *UNVC.mov*, then it is time to use FFmpeg.  Since your file contains DV already, you can try to copy the video and audio to a more standard container format:
```
ffmpeg -i UNVC.mov -map 0:0 -map 0:1 -vcodec copy -acodec copy output.dv
```
Notice that this example does not re-encode and therefore is faster and will preserve the quality.  I used the *-map* option to choose which video and audio streams to copy.  This should create an editor friendly file.

After editing, re-export as DV and then use FFmpeg to convert to whatever final format you want.  My personal favorite is the **One-pass CRF** example as shown here:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by FakeOutdoorsman on 2010-06-04
> **NUboon2Age said:**
> 
```
    Stream #0.3(eng): Data: 0x0000
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
```
So I'm thinking this ffmpeg error message is very misleading -- it probably really doesn't have anything to do with an "unknown format".  Again its probably just the missing files.  I'll know soon and post the results of my experiment.

You're getting this error because FFmpeg doesn't know what to do with *Stream #0.3*.  I'm guessing it is some iMovie specific data.  You can use the *-map* option to ignore this stream: [mapping channels with FFmpeg](http://howto-pages.org/ffmpeg/#map).

---

### Post by NUboon2Age on 2010-06-04
> **NUboon2Age said:**
>  My major misunderstanding in all this was to think that the .mov file was a complete stand-alone file by itself.  I guess it must be essentially sort of an orchestration file that points to various clips.  Whatever I end up with needs to be a complete standalone video and audio file (actually in the end it will probably need to be a flash video .flv file so that I can put it on YouTube).


Well... hmmm... I got rid of the error codes, but its still not working right.  ffmpeg does create a new file, but when you try to run it in Totem, it has blank video and audio?

Is it a problem that I'm using a symlink (although all files are located on the same hard disk) to accommodate the  absolute paths seemingly hard-coded into the .mov file.

> **Unterseeboot_234 said:**
> I use ffmpeg. If you don't have that library installed do that first, it is in the repositories. Also, ffmpeg relies on other libs to do audio. ffmpeg is a command-line tool. Here are the options I use to make .avi with a soundtrack.

```
ffmpeg -i inputfile.mov -sameq -vcodec msmpeg4v2 -acodec libmp3lame outputfile.avi
```

Note that I am using lame -- yet another repository install -- for the audio conversion. You may have to google to find other recipes for the option parameters.

I will comment that many people with new cameras have .mov files they cannot convert on Windows products. Folks come to me to convert because I have the Ubuntu that can do it.

Here's another try:

```
$ sudo ffmpeg -i UNVC.mov -map 0:0 -map 0:1 -sameq -vcodec msmpeg4v2 -acodec libmp3lame UNVC2.avi
[sudo] password for glorious: 
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
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8487a60]sample aspect ratio already set to 10:11, overriding by 'pasp' atom
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8487a60]multiple edit list entries, a/v desync might occur, patch welcome

Seems stream 0 codec frame rate differs from container frame rate: 29.97 (30000/1001) -> 29.97 (2997/100)
    Last message repeated 1 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'UNVC.mov':
  Duration: 02:51:28.82, start: 0.000000, bitrate: 3 kb/s
    Stream #0.0(eng): Video: dvvideo, yuv411p, 720x480, PAR 40:33 DAR 20:11, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
    Stream #0.2(eng): Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.3(eng): Data: 0x0000
File 'UNVC2.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'UNVC2.avi':
    Stream #0.0(eng): Video: msmpeg4v2, yuv420p, 720x480 [PAR 40:33 DAR 20:11], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1(eng): Audio: libmp3lame, 32000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   56 fps=  6 q=0.0 Lsize=     717kB time=1.87 bitrate=3144.6kbits/s    
video:429kB audio:256kB global headers:0kB muxing overhead 4.734947%

```

Result:  blank video, no audio, timeline basically seems to be working.

---

### Post by NUboon2Age on 2010-06-04
> **FakeOutdoorsman said:**
> Kino is an older editor designed for DV video (which is contained in your input file, *UNVC.mov*, according to the FFmpeg info you provided).  A more recent editor is Kdenlive.  Before converting you should see if either of these editors can handle your input file.  DV is an editor friendly format, but your input container format may be specific to iMovie.


I moved the files around to assure myself the problems were not caused by having a symlink.  

In Kdenlive (I'm not really sure what I'm doing but I treated the .mov as a "clip" and added it and it says "sdl failed to open audio.  No available audio device".  I don't get any video output either.

In Kino the .mov file gives me some corrupted video, no audio and the timeline is jumping all around.

> 
If these editors don't like *UNVC.mov*, then it is time to use FFmpeg.  Since your file contains DV already, you can try to copy the video and audio to a more standard container format:
```
ffmpeg -i UNVC.mov -map 0:0 -map 0:1 -vcodec copy -acodec copy output.dv
```
Notice that this example does not re-encode and therefore is faster and will preserve the quality.  I used the *-map* option to choose which video and audio streams to copy.  This should create an editor friendly file.

After editing, re-export as DV and then use FFmpeg to convert to whatever final format you want.  My personal favorite is the **One-pass CRF** example as shown here:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Here's my output:

```
$ sudo ffmpeg -i UNVC.mov -map 0:0 -map 0:1 -vcodec copy -acodec copy output.dv
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
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x87bea60]sample aspect ratio already set to 10:11, overriding by 'pasp' atom
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x87bea60]multiple edit list entries, a/v desync might occur, patch welcome

Seems stream 0 codec frame rate differs from container frame rate: 29.97 (30000/1001) -> 29.97 (2997/100)
    Last message repeated 1 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'UNVC.mov':
  Duration: 02:51:28.82, start: 0.000000, bitrate: 3 kb/s
    Stream #0.0(eng): Video: dvvideo, yuv411p, 720x480, PAR 40:33 DAR 20:11, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
    Stream #0.2(eng): Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.3(eng): Data: 0x0000
Output #0, dv, to 'output.dv':
    Stream #0.0(eng): Video: dvvideo, yuv411p, 720x480 [PAR 40:33 DAR 20:11], q=2-31, 90k tbn, 29.97 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   56 fps= 18 q=-1.0 Lsize=    6562kB time=1.87 bitrate=28771.2kbits/s    
video:6562kB audio:6131kB global headers:0kB muxing overhead -48.300518%

```

Hmmm... When I try to run the resulting output.dv file in Totem I'm getting blank video and just white noise for audio. One good thing is the timeline basically seems to work (ie. its not jumping around, it 'plays' and it seems to be about the right length of time.

---

### Post by FakeOutdoorsman on 2010-06-04
Ok, so Kdenlive doesn't like the *.mov* file.  Does it work with *output.dv*?  Can anything play *output.dv*?

---

### Post by NUboon2Age on 2010-06-04
FakeOutdoorsman,

I so appreciate your and Unterseeboot's help on this. After several days of hammering on this. I have to say I'm starting to get discouraged about this file and thinking of alternatives.  I put a lot of work into the original so I hope I can figure this out.

> **FakeOutdoorsman said:**
> Ok, so Kdenlive doesn't like the *.mov* file.  Does it work with *output.dv*?  Can anything play *output.dv*?

I'm checking it with various editors. Realizing that I'm quite unsure of what I'm doing:

Cinelerra: visually it is displaying audio info, but no video and no audible sound.
Avidemux: Can't open file.

---

### Post by FakeOutdoorsman on 2010-06-04
Can ffplay play *output.dv*?  Can ffplay play *UNVC.mov*?  If no, what does ffplay say?
```
ffplay UNVC.mov
```

---

### Post by irv on 2010-06-04
Try this code:
```
mencoder inputfile.mov -o outputfile.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

make sure you have mencoder installed.

---

### Post by NUboon2Age on 2010-06-04
> **FakeOutdoorsman said:**
> Can ffplay play *output.dv*?  Can ffplay play *UNVC.mov*?  If no, what does ffplay say?
```
ffplay UNVC.mov
```

```
$ ffplay UNVC.mov
FFplay version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9a34d20]sample aspect ratio already set to 10:11, overriding by 'pasp' atom
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9a34d20]multiple edit list entries, a/v desync might occur, patch welcome

```

I guess there is some kind of video there, although its dark.  The audio is like white noise.  It goes on for a bit and then stops.  I guess ffplay doesn't have any kind of interactive controls (or at least none come up).

```
$ ffplay output.dv
FFplay version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

```

Similar video as above.  Short audio white noise (maybe a few seconds), then nothing.

---

### Post by NUboon2Age on 2010-06-04
> **irv said:**
> Try this code:
```
mencoder inputfile.mov -o outputfile.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

make sure you have mencoder installed.

Hmmm... similar results as reported above.  Some kind of dark video and white noise for audio.  'plays'

---

### Post by NUboon2Age on 2010-06-04
I was looking in the original project folders and see that there is a text file called a "<projectname>.iMovieProj" .  Maybe this is something I need to incorporate somehow.  It looks like this...

```
iMovie Project File

External Version: 4.0
Version: 0.9

VolumeMarkerVersion: 1
VideoStandard: NTSC
Project
Selection: 1 -1 -1
PlayHead: 151963
TimelineZoom: 1.000000
TimelineRelativePlayHeadPos: 1.000000
AudioTrackMute: 0 0 0
Clip: Clip 02
  File: Clip:02
  Frames: 507 In:0 Out:507 Thumb:1
  Timestamp: 227584128.000000
  RecordDate: -1101494020
Clip: Clip 02/2
  File: Clip:02
  Frames: 1996 In:507 Out:2503 Thumb:0
  Timestamp: 227584128.000000
  RecordDate: -1101494020
Clip: Clip 02/1
  File: Clip:02
  Frames: 79 In:2503 Out:2582 Thumb:0
  Timestamp: 227584128.000000
  RecordDate: -1101494020

{more of the same}

Bookmark:   
  BookmarkLocation: 377
```

---

### Post by NUboon2Age on 2010-06-04
Some info below that seems to correspond to the version of iMovie I was using from
[http://www.animemusicvideos.org/guides/imovieguide/tutorial4.html](http://www.animemusicvideos.org/guides/imovieguide/tutorial4.html)

Hmmm... it doesn't look good for me.  One good thing is that the clips are all playable... and technically I guess I have the frame by frame instructions on how to recreate the movie.  What a thing to contemplate though. There are about 90 cuts in this short project!!! **Is there a Linux video editor that would make it easy for me to use these frame by frame instructions to reassemble the movie?**

> File Hierarchy

When you create a new project in iMovie, it creates a folder, named after the project when you were asked to save the file for the first time, with a bunch of stuff in it. The first four things it creates are two folders, Audio Waveforms and Media, and two files with an .iMovieProj and .mov extensions. The .iMovieProj file is the project file, however, it cannot stand by itself and depends on the files in the Audio Waveforms and Media files. The .mov file can be played in QuickTime however, it is not a self-contained QuickTime file so you can't really email that file to anyone without having them complain why it doesn't work. Like the iMovie project file, it also depends on the files found in the other two folders.

The Audio Waveforms folder contains volume adjustments made to the clips and audio tracks in your movie as well as the waveform images of the audio files (enable "Show audio track waveforms" in the Preferences to see them in the Timeline). The Media folder contains clips that you have imported, both clips in the Timeline and in the Clips pane, and audio files that you used in your project. These are in DV format and can be played in QuickTime. If you used a purchased song from the iTunes Music Store, it will have a .m4p extension as shown on the right. Otherwise, it'll be an .aiff extension as shown in the example below. It also contains Trash Can data in there too like clips you may have deleted because you didn't need them or back-up clips before they had effects applied to them. It is recommended, however, that you use the Empty Trash feature in iMovie to remove the data instead of deleting them manually.

---

### Post by NUboon2Age on 2010-06-05
What it looks like I'll end up doing is to use Transmaggedon to transcode the component clips from Apple's proprietary Quicktime DV format to the open standard ogg, then do a quick assembly with Pitivi, possibly with further tweaking with other tools to get it back to the original video I had created.  Thanks to Unterseeboot_234, FakeOutdoorsman, and irv for their aid in this endeavor!

---

