---
title: "AAC to AC3 in linux"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by survient on 2008-03-12
just as the title says. I have a video file with a 5.1 aac audio stream I'm trying to burn to a dvd, but my dvd player doesn't support aac(hmmm I wonder why? :P). So yes, in order go 5.1 I need to get it to 5.1 ac3. What I don't know is how to get from aac to ac3 in linux, and still keep all 6 channels. Any help on this would be appreciated. Btw, I tried vlc, it not only downmixes to a stereo ac3 even when told to use 6 channels, but it also somehow makes the play speed get cut in half.

---

### Post by phiphedog on 2008-03-12
Not 100% sure as I can't test for you but you should be able to do this with ffmpeg with a command similar to this. Just play around with it and read the man page.

```
ffmpeg -i /folder/inputfile.avi -vcodec copy -acodec aac -ab 384k -y /folder/outputfile.avi

```

---

### Post by survient on 2008-03-12
Ok, I run it, but everytime I specify the bitrate, it gives me this error:

```

$ ffmpeg -i /home/user/Desktop/stuff/test.aac -acodec ac3 -ab 384k /home/user/Desktop/stuff/test.ac3
FFmpeg version SVN-r12420, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-libvorbis --enable-liba52 --enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264 --enable-libtheora
  libavutil version: 49.6.0
  libavcodec version: 51.51.0
  libavformat version: 52.9.0
  libavdevice version: 52.0.0
  built on Mar 12 2008 02:22:56, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, aac, from '/home/user/Desktop/stuff/test.aac':
  Duration: 00:23:49.9, bitrate: 144 kb/s
    Stream #0.0: Audio: mpeg4aac, 24000 Hz, 5:1, 144 kb/s
Output #0, ac3, to '/home/user/Desktop/stuff/test.ac3':
    Stream #0.0: Audio: ac3, 24000 Hz, 5:1, 384 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

any way to fix this? BTW this version of ffmpeg is latest off the svn(needed aac support).

---

### Post by phiphedog on 2008-03-12
Try to match the output to the input so use -144k instead of -386k

---

### Post by survient on 2008-03-12
I did, nogo

---

### Post by phiphedog on 2008-03-12
try this thread

[http://forum.doom9.org/showthread.php?t=75222](http://forum.doom9.org/showthread.php?t=75222)

---

### Post by survient on 2008-03-12
Thanks for the help, but that's to go from AC3 to AAC, and there isn't a way using those directions to do it in reverse.

---

### Post by eye208 on 2008-03-12
Use MEncoder.

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-audio-lavc](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-audio-lavc)


.

---

### Post by survient on 2008-03-12
Mencoder only works for video files, and it's giving me errors all the way.

---

### Post by phiphedog on 2008-03-12
Sorry I can't help more, I'm at work on a windows machine and I cant test and play around for you. You're on the right track with ffmpeg. Just read the man page and have a play around with it like so.

ffmpeg -i /home/user/Desktop/stuff/test.aac -acodec ac3 /home/user/Desktop/stuff/test.ac3
ffmpeg -i /home/user/Desktop/stuff/test.aac -acodec ac3 -ab 384k -ar 24000 /home/user/Desktop/stuff/test.ac3


you'll get there in the end and learn something

---

### Post by eye208 on 2008-03-12
> **survient said:**
> Mencoder only works for video files, and it's giving me errors all the way.
If your standalone DVD player is capable of playing back raw AC3 audio streams without video, I would like to know the brand and model.

---

### Post by survient on 2008-03-12
yes that ffmpeg doesn't like multiaudio aac streams. I gave up and left it at 64k bitrate, and the result was just static. Every time I try to specify a flag it gives me an error.

---

### Post by survient on 2008-03-12
The issue is that the ac3 stream is an additional audio stream to be burned on the DVD. The primary audio is going to be stereo, with the secondary as 5.1, so I need the ac3 by itself.

---

### Post by eye208 on 2008-03-12
> **survient said:**
> I need the ac3 by itself.
The option "-of rawaudio" will give you the AC3 by itself.

---

### Post by survient on 2008-03-12
Apparently it wants to save the video as well, which, considering I'm just adding audio... and also given that ffmpeg gives me garbled output, and that mencoder is related, I have my doubts on the results of the audio.
```

$ mencoder -of rawaudio /home/user/Desktop/stuff/test.mkv -channels 6 -oac lavc -lavcopts acodec=ac3:abitrate=384 -o /home/user/Desktop/stuff/test.ac3
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 4000+ (Family: 15, Model: 55, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xdd10888
[mkv] Track ID 1: video (V_MS/VFW/FOURCC) "Video", -vid 0
[mkv] Track ID 2: audio (A_MPEG/L3), -aid 0, -alang jpn
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [XVID]  640x480  16bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x44495658  size:640x480  fps:29.97  ftime:=0.0334

No video encoder (-ovc) selected. Select one (see -ovc help).

Exiting...

```

---

### Post by eye208 on 2008-03-12
> **survient said:**
> Apparently it wants to save the video as well
MEncoder is a modular application. The video encoding stage does not know that you intend to throw away the video stream at the muxing stage, so you have to specify a codec here.

Just add "-ovc raw". The result will be discarded anyway.

---

