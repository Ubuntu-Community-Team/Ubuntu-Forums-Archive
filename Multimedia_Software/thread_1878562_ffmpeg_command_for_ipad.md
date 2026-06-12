---
title: "ffmpeg command for ipad"
date: 2011-11-10
forum: Multimedia Software
---

### Post by shashanksingh on 2011-11-10
I had a .mkv file I needed to convert for an ipad. I found a complicated command on the net, and when I tried the simple command:

ffmpeg -i input.mkv -o output.mp4

it gave me this error in the end:

Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)


I couldn't understand much of it. I tried winff but I just couldn't find the actual output container for an ipad, I found something in the RockBox for a ipad nano.

Please help

---

### Post by andrew.46 on 2011-11-10
Can you give the command plus full, uncut terminal output? This should give an idea about what is missing from your conversion.

---

### Post by shashanksingh on 2011-11-10
> **andrew.46 said:**
> Can you give the command plus full, uncut terminal output? This should give an idea about what is missing from your conversion.

```

ffmpeg -i /media/Warehouse/Movies/input.mkv ~/output.mp4
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[matroska,webm @ 0xbb7340] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '/media/Warehouse/Movies/input.mkv':
  Metadata:
    title           : Movie Title
  Duration: 01:57:27.08, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264 (High), yuv420p, 1280x528 [PAR 1:1 DAR 80:33], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0.1(eng): Audio: aac, 96000 Hz, stereo, s16 (default)
[buffer @ 0xbfa0c0] w:1280 h:528 pixfmt:yuv420p
[mp4 @ 0xbf41c0] track 1: output format does not support sample rate 96000hz
Output #0, mp4, to '/home/shashank/output.mp4':
  Metadata:
    title           : Movie Title
    encoder         : Lavf53.2.0
    Stream #0.0: Video: mpeg4, yuv420p, 1280x528 [PAR 1:1 DAR 80:33], q=2-31, 200 kb/s, 24k tbn, 23.98 tbc (default)
    Stream #0.1(eng): Audio: aac, 96000 Hz, stereo, s16, 64 kb/s (default)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)


```

---

### Post by andrew.46 on 2011-11-10
FFmpeg does not like the frequency (96000) of the aac stream in the output mp4 container. So perhaps to simply exchange containers (from matroska to mp4) you could try:
```

ffmpeg -i /media/Warehouse/Movies/input.mkv \
        -vcodec copy \
        -acodec libfaac **[COLOR="Red"]-ar 44100[/COLOR]** -ab 128k \
        ~/output.mp4
```

For this to succeed you will need to follow [Option C of FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=1117283") to allow aac encoding with libfaac.

---

### Post by FakeOutdoorsman on 2011-11-10
I should update that guide again for Natty. There are some easier methods for AAC encoding other than dealing with libfaac and Medibuntu.

"Native" FFmpeg/libav AAC encoder:
```
-acodec aac -strict experimental
```

vo-aacenc:
```
-acodec libvo_aacenc
```

However, there seems to be various options on what encoder sounds best at a given bitrate. vo-aacenc requires the **libavcodec-extra-53** package...I think.

---

### Post by shashanksingh on 2011-11-11
> **andrew.46 said:**
> FFmpeg does not like the frequency (96000) of the aac stream in the output mp4 container. So perhaps to simply exchange containers (from matroska to mp4) you could try:
```

ffmpeg -i /media/Warehouse/Movies/input.mkv \
        -vcodec copy \
        -acodec libfaac **[COLOR="Red"]-ar 44100[/COLOR]** -ab 128k \
        ~/output.mp4
```

For this to succeed you will need to follow [Option C of FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=1117283") to allow aac encoding with libfaac.

Thank you. That Worked, along with Medibuntu. :-)

Just curious, coud you tell me why that number 44100 intead of 96000?
Why not some power of 2 or something? Like 64000?

---

### Post by andrew.46 on 2011-11-11
I am no expert on sampling frequency with different codecs but I do know that aac sound does support 96000 sample rate and this is one of its [advantages over mp3]("http://en.wikipedia.org/wiki/Advanced_Audio_Coding#AAC.27s_improvements_over_MP3"). I think FFmpeg is actually complaining that 96000 aac sample frequency is not supported *in an mp4 container*, but I have not tested this at all. Would be an interesting trial and might support my own feeling that matroska is a far superior container with some great tools to manipulate it, I am thinking of mkvtoolnix especially.

Don't forget FakeOutdoorsman's suggestion of some alternative aac encoders which have the added benefit of no encumbrance with licensing issues and no futzing about with external repositories. And perhaps experiment with own personal favourite, and defiantly closed source offering, neroAacEnc...

---

