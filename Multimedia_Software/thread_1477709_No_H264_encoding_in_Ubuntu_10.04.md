---
title: "No H264 encoding in Ubuntu 10.04"
date: 2010-05-09
forum: Multimedia Software
---

### Post by skatebiker on 2010-05-09
After installing Ubuntu 10.04 no mp4 encoding works anymore.
After googling around I tried installing h264enc, x264 and libx264-85 but with no result.
In synaptics all these codecs are marked as installed.
Playback of H.264 worked out-of-the-box.

ffmpeg -i movie.avi -ar 22050 -ab 32000 -f mov -b 200k -s 320x240 $2 ipod.mov

issues an error 

Unsupported codec for output stream #0.1

Previously, on Crunchbang 9.04 and Kubuntu 8.10 H.264 encoding worked fine.

Where can I find a suitable encoder for H.264 ?

---

### Post by skatebiker on 2010-05-09
Really NOBODY who knows thia ??

---

### Post by Judo on 2010-05-09
I tried this and found what appears to be the problem:

Stream #0.1(eng): Audio: 0x0000, 22050 Hz, stereo, s16, 32 kb/s

Notice how the audio format is "0x0000?"  That means no audio format was chosen. In other words, ffmpeg doesn't know which audio format to use, so you'll need to specify it manually with -acodec.  Past versions would have worked fine without that, but the version in 10.04 had it removed.

I should also mention that your command does not output h.264.  In fact, it outputs MPEG-4 SP which is significantly worse, but supported by iPods.

---

### Post by FakeOutdoorsman on 2010-05-09
FFmpeg from the Ubutnu repository is missing some encoders, so you will have to manually enable them:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

Now you can encode to an iPod usable format:
```
ffmpeg -i input.foo -acodec libfaac -vcodec libx264 -ac 2 -ab 128k -vpre hq -vpre ipod320 -crf 26 -s 320x240 -threads 0 output.mp4
```

**Update:** I fixed my example.  The *-vcodec libx264* was missing.

---

### Post by skatebiker on 2010-05-10
I tried setting the Medibuntu repostitory in sources.list, removing ffmpeg and reinstalling help aand also installing libdvdcss2 but with no luck:
still no aac and h264 encoding in ffmpeg.

It it an option to get the binaries from a 9.04 installation (which I also have) ?

---

### Post by FakeOutdoorsman on 2010-05-10
> **skatebiker said:**
> I tried setting the Medibuntu repostitory in sources.list, removing ffmpeg and reinstalling help aand also installing libdvdcss2 but with no luck:
still no aac and h264 encoding in ffmpeg.

It it an option to get the binaries from a 9.04 installation (which I also have) ?

Did you follow **Option C: Medibuntu** from the link I provided in my last post in this thread?  Did you attempt to use the example FFmpeg command from my last post?  Can you clarify "still no aac and h264 encoding in ffmpeg" (your command, errors, messages, etc)?

The link also works for 9.04.

---

### Post by skatebiker on 2010-05-10
@Fakeoutdoorsman:

Thanks, this worked AFTER I installed the restricted packages.
Yesterday I tried your suggestiom already but without success.

Now it works .

I still have to find out the proper command lines for KDEnlive.

Thanks.

---

### Post by pi.boy.travis on 2010-05-10
> **skatebiker said:**
> @Fakeoutdoorsman:

Thanks, this worked AFTER I installed the restricted packages.
Yesterday I tried your suggestiom already but without success.

Now it works .

I still have to find out the proper command lines for KDEnlive.

Thanks.

Hi.  I've also tried Fakeoutdoorsman's guide, section C, Medibuntu, but after installing the libav packages I still can't get encoding to work.  Could you please clarify exactly which packages you had to install?

Thanks in advance!

---

### Post by FakeOutdoorsman on 2010-05-10
> **pi.boy.travis said:**
> Hi.  I've also tried Fakeoutdoorsman's guide, section C, Medibuntu, but after installing the libav packages I still can't get encoding to work.  Could you please clarify exactly which packages you had to install?

Thanks in advance!

You mentioned that you still can't get encoding to work.  Can you show your FFmpeg command and the complete output?  This might provide some info that can help determine why your encoding is failing.

---

### Post by pi.boy.travis on 2010-05-10
> **FakeOutdoorsman said:**
> You mentioned that you still can't get encoding to work.  Can you show your FFmpeg command and the complete output?  This might provide some info that can help determine why your encoding is failing.

```
travis@travis-laptop:~/Desktop$ ffmpeg -i 1.avi -acodec libfaac -ac 2 -ab 128k -vpre veryslow -crf 26 -s 320x240 -threads 0 output.mp4
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
Input #0, avi, from '1.avi':
  Duration: 00:21:14.61, start: 0.000000, bitrate: 1150 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
File for preset 'veryslow' not found

```

This is actually the first time I've tried using the command line, usually I use Avidimux or PiTiVi. . .  I'm not exactly sure what the 'preset' is for, I'm not exactly a video expert.

Thanks for all the effort you've put into helping us here with this issue.

P.S. I've tried all the different preset options, all give the same error.

---

### Post by FakeOutdoorsman on 2010-05-10
> **pi.boy.travis said:**
> ```
travis@travis-laptop:~/Desktop$ ffmpeg -i 1.avi -acodec libfaac -ac 2 -ab 128k -vpre veryslow -crf 26 -s 320x240 -threads 0 output.mp4
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
Input #0, avi, from '1.avi':
  Duration: 00:21:14.61, start: 0.000000, bitrate: 1150 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
File for preset 'veryslow' not found

```

This is actually the first time I've tried using the command line, usually I use Avidimux of PiTiVi. . .  I'm not exactly sure what the 'preset' is for, I'm not exactly a video expert.

Thanks for all the effort you've put into helping us here with this issue.

P.S. I've tried all the different preset options, all give the same error.

FFmpeg from the Ubuntu repository uses the old preset system.  Try *-vpre hq* instead of *-vpre veryslow*.  The presets are collections of encoding settings.  Before presets were around a whole bunch of confusing options had to be manually entered and random examples on the net were often out of date.

---

### Post by pi.boy.travis on 2010-05-10
> **FakeOutdoorsman said:**
> FFmpeg from the Ubuntu repository uses the old preset system.  Try *-vpre hq* instead of *-vpre veryslow*.  The presets are collections of encoding settings.  Before presets were around a whole bunch of confusing options had to be manually entered and random examples on the net were often out of date.

```
 ffmpeg -i 1.avi -acodec libfaac -ac 2 -ab 128k -vpre hq -crf 26 -s 320x240 -threads 0 output.mp4
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
Input #0, avi, from '1.avi':
  Duration: 00:21:14.61, start: 0.000000, bitrate: 1150 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
File for preset 'hq' not found

```

Hmm. . .  I tried reinstalling the Medibuntu packages after an apt-get purge, and I still get the same error. . .

---

### Post by FakeOutdoorsman on 2010-05-11
That error was my fault.  I forgot to add *-vcodec libx264* to my [example](http://ubuntuforums.org/showpost.php?p=9270409&postcount=4) from a few posts ago.  I must have typed *-vcodec libx264* several hundred times by now and I still forget it sometimes.

I fixed the example.

---

### Post by pi.boy.travis on 2010-05-11
> **FakeOutdoorsman said:**
> That error was my fault.  I forgot to add *-vcodec libx264* to my [example](http://ubuntuforums.org/showpost.php?p=9270409&postcount=4) from a few posts ago.  I must have typed *-vcodec libx264* several hundred times by now and I still forget it sometimes.

I fixed the example.

Fantastic!  Thank you!  Is there any way I can get this working in my video editors?

---

### Post by guneza on 2010-05-19
* Distro: Ubuntu 10.04
* I have installed medibuntu repositories, following the [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

Without the "-ar 44100" set, I got the following cryptic message:

```
[libfaac @ 0x11b6850]libfaac doesn't support this output format!
```

This is what worked for me:

```
ffmpeg -i 00012.MTS -acodec libfaac -ar 44100 -vcodec libx264 -ac 2 -ab 128k \
-vpre hq -vpre ipod320 -crf 26 -s 320x240 -threads 4 output.mp4
```

---

### Post by pi.boy.travis on 2010-06-09
Still looking for a way to get this working in the video editors, Pitivi, etx. . . Anyone know anything about this?

---

