---
title: "ffmpeg - Concatenating mpg + ac3 files into one"
date: 2011-02-25
forum: Multimedia Software
---

### Post by havok1977 on 2011-02-25
Hello,

I'm doing some more experimenting with ffmpeg, this time to merge a number of video files into one, they are mpg with ac3 audio and after looking around a bit I found this way of doing it:

```
cat PART1.mpg PART2.mpg PART3.mpg PART4.mpg PART5.mpg | ffmpeg -f mpeg -i - -vcodec copy -acodec copy Joined.mpg
```\

And well, it does concatenate the files and merges it into one, but the audio is lost and I have no idea why..., by using -acodec copy it shouldn't do anything other than a plain transcription of the ac3 bits yet for some reason it doesn't.

Anyone has any ideas?

---

### Post by FakeOutdoorsman on 2011-02-26
Can you show the complete FFmpeg output of your command?

---

### Post by havok1977 on 2011-02-28
> **FakeOutdoorsman said:**
> Can you show the complete FFmpeg of your command?

Sure thing, heres the whole shebang:

```
cat PART1.mpg PART2.mpg PART3.mpg PART4.mpg PART5.mpg | ffmpeg -f mpeg -i - -vcodec copy -acodec copy Joined.mpg
FFmpeg version SVN-r25838, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jan 21 2011 08:21:58 with gcc 4.4.5
  configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-libvpx --enable-librtmp --extra-libs=-lgcrypt --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50.33. 0 / 50.33. 0
  libavcore      0.14. 0 /  0.14. 0
  libavcodec    52.97. 2 / 52.97. 2
  libavformat   52.87. 1 / 52.87. 1
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.65. 0 /  1.65. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0x1ffe760] max_analyze_duration reached
[mpeg @ 0x1ffe760] Estimating duration from bitrate, this may be inaccurate
Input #0, mpeg, from 'pipe:':
  Duration: N/A, start: 1.000000, bitrate: 9448 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 221:150 DAR 221:100], 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, mpeg, to 'Joined.mpg':                                                            
  Metadata:                                                                                  
    encoder         : Lavf52.87.1                                                            
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 221:150 DAR 221:100], q=2-31, 9000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
frame=207861 fps=780 q=-1.0 Lsize= 3251114kB time=6935.60 bitrate=3840.1kbits/s    
video:2854074kB audio:379232kB global headers:0kB muxing overhead 0.550771%

```

And well, the resulting file appears to include the audio track, but on playback it is completely mute.

```
Input #0, mpeg, from 'Joined.mpg':                                                           
  Duration: 01:55:35.63, start: 1.000000, bitrate: 3840 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 221:150 DAR 221:100], 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
At least one output file must be specified

```

---

### Post by Jose Catre-Vandis on 2011-02-28
Well, there's the ffmpeg way of joining files together [here]("http://ffmpeg.org/faq.html#TOC27"), but its a bit long winded, you could try with the -sameq setting though You might need to make the intermediate file before running the ffmpeg line? 

or

Assuming all the files are encoded in the same way, try mencoder:
```
mencoder file1.mpg file2.mpg file3.mpg -ovc copy -oac copy -o joined.mpg
```

---

### Post by havok1977 on 2011-03-01
> **Jose Catre-Vandis said:**
> Assuming all the files are encoded in the same way, try mencoder:
```
mencoder file1.mpg file2.mpg file3.mpg -ovc copy -oac copy -o joined.mpg
```

That worked, thanks

---

