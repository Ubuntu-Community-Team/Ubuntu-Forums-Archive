---
title: "Trim Video with Multiple Audio Tracks using AVCONV"
date: 2016-09-09
forum: Multimedia Software
---

### Post by pumrum on 2016-09-09
I have a bunch of MKV videos that have two audio tracks (English and commentary). I am trimming the first several seconds off each video using AVCONV, but when I do, it's dropping the second audio track. The output file seems perfect in every way, except for the missing second audio track. Any ideas how to trim a video file using AVCONV while preserving both audio tracks?

Here is the command I am  using to trim (log output attached):
```
avconv -i input.mkv -ss 00:00:25 -codec copy output.mkv
```

I also tried to manually specify the number of audio tracks, but this resulted in the same output:
```
avconv -i input.mkv -ss 00:00:25 -ac 2 -codec copy output.mkv
```

Here's version info:
```

Ubuntu MATE 16.04
Linux hostname 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

ffmpeg version 2.8.6-1ubuntu2 Copyright (c) 2000-2016 the FFmpeg developers
built with gcc 5.3.1 (Ubuntu 5.3.1-11ubuntu1) 20160311
configuration: --prefix=/usr --extra-version=1ubuntu2 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
libavutil      54. 31.100 / 54. 31.100
libavcodec     56. 60.100 / 56. 60.100
libavformat    56. 40.101 / 56. 40.101
libavdevice    56.  4.100 / 56.  4.100
libavfilter     5. 40.101 /  5. 40.101
libavresample   2.  1.  0 /  2.  1.  0
libswscale      3.  1.101 /  3.  1.101
libswresample   1.  2.101 /  1.  2.101
libpostproc    53.  3.100 / 53.  3.100

```

I can provide a sample video file if needed (approx 250mb). Thanks!

**[SIZE=4]UPDATE:[/SIZE]**
Apparently if you have more than one audio track, the default copy command will only copy one track. I haven't had time to look into if this is intended behavior (is it?) but the command I was able to use to copy the video and both audio tracks was:
```
avconv -i input.mkv -ss 00:00:25 **-map 0:0 -map 0:1 -map 0:2** -codec copy output.mkv
```

I also haven't played around with if you need to specify the video (0:0) and first audio (0:1) streams, or if just specifying the 2nd audio track (0:2) will copy both the default, plus the additional track. If I do try that, I'll update this post. Hope this helps someone!

---

### Post by TheFu on 2016-09-10
Or use mkvmerge with the --split parts: option.  This won't transcode anything and works as fast as a file copy.

$ mkvmerge -o output.mkv --split parts:0:00:02.0-  input.mkv

That will keep all tracks (video, audio, srts, subs, text, whatever) and remove _about_ the first 2 seconds.  mkvmerge only cuts at key frames.

---

### Post by FakeOutdoorsman on 2016-09-10
avconv is gone. It appears you are actually using ffmpeg which is better anyway.

As you noticed the default [stream selection](https://ffmpeg.org/ffmpeg.html#Stream-selection) behavior is to select only one stream per type. Once you use the -map option the default stream selection behavior is disabled. To include all streams from the first input, and your only input in this case, use "-map 0" (the ffmpeg file index starts counting from 0). This will allow you to copy everything without having to explicitly map each desired stream. Your resulting command would be:

```
ffmpeg -i input.mkv -ss 25 -map 0 -c copy output.mkv
```

---

### Post by ltrtiger2 on 2016-09-16
> **TheFu said:**
> Or use mkvmerge with the --split parts: option.  This won't transcode anything and works as fast as a file copy.

$ mkvmerge -o output.mkv --split parts:0:00:02.0-  input.mkv

That will keep all tracks (video, audio, srts, subs, text, whatever) and remove _about_ the first 2 seconds.  mkvmerge only cuts at key frames.

Thank you for this. I'd also been looking for a solution to this sort of issue. Appreciate the advice.

---

