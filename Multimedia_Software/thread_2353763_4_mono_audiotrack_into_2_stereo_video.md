---
title: "4 mono audiotrack into 2 stereo video"
date: 2017-02-24
forum: Multimedia Software
---

### Post by chalan2 on 2017-02-24
hello, i have video .m4v with 4 mono audio tracks and need to make from it 2 stereo tracks. How to do it? 1 and 2 audio track is mono (L+R) of first language, 3 and 4 audio track is mono (L+R) second (original) language. Was trying with handbrake, but with no luck...thank you...

---

### Post by Autodave on 2017-02-24
Not sure exactly what you have there or how it is written to the file, but you may want to have a look at *Audacity. *It is in the repositories.

---

### Post by SeijiSensei on 2017-02-25
See the mono -> stereo section of [https://trac.ffmpeg.org/wiki/AudioChannelManipulation](https://trac.ffmpeg.org/wiki/AudioChannelManipulation)

ffmpeg can accomplish pretty much anything you might want to do with audio and video.  You just need to get used to using the terminal rather than a GUI.

You'll need to extract the audio and video streams first.  I don't know how to do that with m4v; with Matroska files I use mkvextract from the mkvtoolnix package.  I'd process the two audio streams first, creating one stereo result in each language.  Then you can repackage the video and the two new streams into an .mkv with mkvmerge.  It's probably also possible to do all of this with one ffmpeg command, but that's above my pay grade.

---

### Post by chalan2 on 2017-11-04
i have .gfx and .mxf files with 4 audio tracks... the files are very big... the files contains audiotracks 1+2 SK language, 3+4 original, 7+8 AD with sync... i need to encode it with h264 or better with h265...  handbrake take only the first audio track 1 and copy it to 1+2 so at the end i have .mkv with MONO of the SK language and original is not there. How can i have .mkv h246 or h265 with stereo SK language in first audio track, original in second and ad with sync in third audio track?

---

### Post by shantiq on 2017-11-04
hi chalan


you can very likely strip the audio tracks with ffmpeg and then manipulate mono to stereo with audacity then mux again audio and video with ffmpeg or mkvmerge
so please step &#10122; can you run your file through mediainfo and post results so we see what is in inside and which order it is in

```
 sudo apt install mediainfo
```


then


```
mediainfo yourfile
```

also

```
ffmpeg -i  yourfile
```

---

### Post by chalan2 on 2017-11-04
chalan@chalan-Desktop:~/Desktop/test$ ffmpeg -i  01-Útek.gxf 
```
ffmpeg version 2.8.11-0ubuntu0.16.04.1 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, gxf, from '01-Útek.gxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
  Duration: 00:23:51.16, start: 0.000000, bitrate: 36156 kb/s
    Stream #0:0: Video: mpeg2video (4:2:2), yuv422p(tv), 1920x1080 [SAR 1:1 DAR 16:9], 30000 kb/s, 50 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:2: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:3: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:4: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:5: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:6: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:7: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:8: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:9: Data: none
At least one output file must be specified
```

how can i extract audio tracks without video? just extract no encoding...

---

### Post by shantiq on 2017-11-04
really high quality :]

```
 ffmpeg -i YOURFILE  -vn -c:a copy -map 0:1 audio1.flac
```    and then repeat for each audio track to 0:8 [change the numbers]


I picked flac as it is a high-quality lossless format/ you can pick wav if you prefer but flac loses none of the quality
  -vn means no video



Then I would suggest you manipulate the audio tracks in Audacity it is easier than playing with terminal
load up your mono files and create stereo files with cut and paste or what you need  ...


see here >>


[[IMG]https://s1.postimg.org/50uj77bd1n/Screenshot_from_2017-11-04_09-42-30.png[/IMG]]("https://postimg.org/image/50uj77bd1n/")

---

### Post by chalan2 on 2017-11-04
```
chalan@chalan-Desktop:~/Desktop/test$ ffmpeg -i 01-Útek.gxf  -vn -c:a copy -map 0:1 1L.flac
ffmpeg version 2.8.11-0ubuntu0.16.04.1 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, gxf, from '01-Útek.gxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
  Duration: 00:23:51.16, start: 0.000000, bitrate: 36156 kb/s
    Stream #0:0: Video: mpeg2video (4:2:2), yuv422p(tv), 1920x1080 [SAR 1:1 DAR 16:9], 30000 kb/s, 50 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:2: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:3: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:4: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:5: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:6: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:7: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:8: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:9: Data: none
[flac @ 0x25ef680] unsupported codec
Output #0, flac, to '1L.flac':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
    encoder         : Lavf56.40.101
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, mono, 768 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument
```

---

### Post by shantiq on 2017-11-04
ok use wav instead of flac  [see if it flies]

---

### Post by chalan2 on 2017-11-04
ok now i have

```
chalan@chalan-Desktop:~/Desktop/test$ ls -lh 
total 6,6G
-rwxr-xr-x 1 chalan elson 6,1G nov  4 09:45 01-Útek.gxf
-rw-r--r-- 1 chalan elson 132M nov  4 20:19 1L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 1R.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 2L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 2R.wav

```

isnt there any way to mix 1L+1R as one track stereo with ffmpeg?

---

### Post by chalan2 on 2017-11-04
ok i mix L+R tracks in Audacity... first i have to import both audio files 1L.wav + 1R.wav then switch from MONO the first  to LEFT, second to RIGHT and after that Tracks/Mix and Render... so i have now two Stereo Audio tracks. First SK language, second EN language... what next? and why are the stereo tracks so big? i use 32bit Wav for audio extract... 

```
chalan@chalan-Desktop:~/Desktop/test$ ls -lh 
total 8,1G
-rwxr-xr-x 1 chalan elson 6,1G nov  4 09:45 01-Útek.gxf
-rw-r--r-- 1 chalan elson 132M nov  4 20:19 1L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 1R.wav
-rw-r--r-- 1 chalan elson 525M nov  4 21:00 1stereo.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 2L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 2R.wav
-rw-r--r-- 1 chalan elson 525M nov  4 21:01 2stereo.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:36 5L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:37 6R.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:25 7AD.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:25 8SYNC.wav

```

---

### Post by shantiq on 2017-11-05
they are big as you picked 32-bit   ....    24-bit or even 16-bit would have been enough  ...    you can do it again or keep those



ok so now you have two stereo audio tracks in two languages [SK and ENG]

you now need to:


&#10122;   peel your video from original file 


```
ffmpeg -i YOURORIGINALFILE  -an -b:v copy MUTEVIDEO.mkv
```

now you have a mute video in mkv with original 30000k bitrate kept  


&#10123; mux all 3 files together  ...   you can do it with ffmpeg 


```
ffmpeg -i MUTEVIDEO.mkv  -i  STEREOAUDIO1.wav -i STEREOAUDIO2.wav   -map 0 -map 1 -map 2  -c copy VIDEO-WITH-SK-AND-ENG.mkv
```



HOPE  this is all ok your side :]
PS: if you want to reduce the overall size ...  you can do that but I would keep the very high specs myself  ...  30000k is huge quality but really hidef
But if you want that ::

```
ffmpeg -i VIDEO-WITH-SK-AND-ENG.mkv -b:a 768k -b:v 7000k SMALLER-VIDEO-WITH-SK-AND-ENG.mkv
```
still will be high-grade but &#8776; ¼-sized

---

### Post by chalan2 on 2017-11-05
```
chalan@chalan-Desktop:~/Desktop/test$ ffmpeg -i 01-Útek.gxf -an -b:v copy 01-Útek.gxf-no_audio.mkv
ffmpeg version 2.8.11-0ubuntu0.16.04.1 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, gxf, from '01-Útek.gxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
  Duration: 00:23:51.16, start: 0.000000, bitrate: 36156 kb/s
    Stream #0:0: Video: mpeg2video (4:2:2), yuv422p(tv), 1920x1080 [SAR 1:1 DAR 16:9], 30000 kb/s, 50 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:2: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:3: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:4: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:5: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:6: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:7: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:8: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:9: Data: none
No pixel format specified, yuv422p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x10a0520] [Eval @ 0x7fff6a97f550] Undefined constant or missing '(' in 'copy'
[libx264 @ 0x10a0520] Unable to parse option value "copy"
[libx264 @ 0x10a0520] Error setting option b to value copy.
Output #0, matroska, to '01-Útek.gxf-no_audio.mkv':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
    Stream #0:0: Video: h264, none, q=2-31, 128 kb/s, SAR 1:1 DAR 0:0, 25 fps
    Metadata:
      encoder         : Lavc56.60.100 libx264
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video (native) -> h264 (libx264))
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height


```

---

### Post by shantiq on 2017-11-06
try:   (encoding here so takes longer)

```
 ffmpeg -i YOURORIGINALFILE  -an -b:v 30000k -r 50 MUTEVIDEO.mkv
```

or since you mentioned h265

```
 ffmpeg -i YOURORIGINALFILE  -an -b:v 30000k -r 50 -c:v libx265  MUTEVIDEO.mkv
```

---

### Post by chalan2 on 2017-11-10
isn't there any way to copy original .gfx (or .mxf) video with no audio without encoding it? the goal is to have full quality video with audio tracks first SK mixed L + R in stereo and second EN mixed L+R in stereo... after that i will encde it to h264 or h265....

---

### Post by shantiq on 2017-11-10
Yes try peeling the video to .gfx
See if ffmpeg accepts it
I have no such file to test
If it does use rest of the commands as above replacing .mkv for .gfx ...   see if it works :]

...  what i suggested leaves you with h265  anyway...

---

### Post by chalan2 on 2017-11-10
ffmpeg probably dont know .gfx or .mxf this errors ocures

```
chalan@chalan-Desktop:~/Desktop/test$ ffmpeg -i 01-Útek.gxf -an -b:v copy 01-Útek_noa_audio.gxf
ffmpeg version 2.8.11-0ubuntu0.16.04.1 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, gxf, from '01-Útek.gxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
  Duration: 00:23:51.16, start: 0.000000, bitrate: 36156 kb/s
    Stream #0:0: Video: mpeg2video (4:2:2), yuv422p(tv), 1920x1080 [SAR 1:1 DAR 16:9], 30000 kb/s, 50 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:2: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:3: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:4: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:5: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:6: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:7: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:8: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:9: Data: none
No pixel format specified, yuv422p for MPEG-2 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[mpeg2video @ 0xbc0620] [Eval @ 0x7ffd44abeb00] Undefined constant or missing '(' in 'copy'
[mpeg2video @ 0xbc0620] Unable to parse option value "copy"
[mpeg2video @ 0xbc0620] Error setting option b to value copy.
Output #0, gxf, to '01-Útek_noa_audio.gxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
    Stream #0:0: Video: mpeg2video, none, q=2-31, 128 kb/s, SAR 1:1 DAR 0:0, 25 fps
    Metadata:
      encoder         : Lavc56.60.100 mpeg2video
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video (native) -> mpeg2video (native))
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height

``````
chalan@chalan-Desktop:~/Desktop/test$ ffmpeg -i 01-Útek.gxf -an -b:v copy 01-Útek_noa_audio.mxf
ffmpeg version 2.8.11-0ubuntu0.16.04.1 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, gxf, from '01-Útek.gxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
  Duration: 00:23:51.16, start: 0.000000, bitrate: 36156 kb/s
    Stream #0:0: Video: mpeg2video (4:2:2), yuv422p(tv), 1920x1080 [SAR 1:1 DAR 16:9], 30000 kb/s, 50 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:2: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:3: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:4: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:5: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:6: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:7: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:8: Audio: pcm_s16le, 48000 Hz, mono, s16, 768 kb/s
    Stream #0:9: Data: none
No pixel format specified, yuv422p for MPEG-2 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[mpeg2video @ 0x233e620] [Eval @ 0x7ffd48ab74c0] Undefined constant or missing '(' in 'copy'
[mpeg2video @ 0x233e620] Unable to parse option value "copy"
[mpeg2video @ 0x233e620] Error setting option b to value copy.
Output #0, mxf, to '01-Útek_noa_audio.mxf':
  Metadata:
    timecode        : 00:00:00:00
    timecode_at_mark_in: 00:00:00:00
    timecode_at_mark_out: 00:23:51:08
    Stream #0:0: Video: mpeg2video, none, q=2-31, 128 kb/s, SAR 1:1 DAR 0:0, 25 fps
    Metadata:
      encoder         : Lavc56.60.100 mpeg2video
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video (native) -> mpeg2video (native))
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height



```

---

### Post by shantiq on 2017-11-10
so  use .mkv as mentioned before see if that works ...  :]



&#10122;   ```
  ffmpeg -i YOURORIGINALFILE  -an -b:v 30000k -r 50 -c:v libx265  MUTEVIDEO.mkv
```    to get mute video file

then muxing all 3 new files  >>


&#10123;  ```
ffmpeg -i MUTEVIDEO.mkv  -i  STEREOAUDIO1.wav -i STEREOAUDIO2.wav   -map 0 -map 1 -map 2  -c copy VIDEO-WITH-SK-AND-ENG.mkv
```



and you will have a h265 video file with 2 stereo audio files and the original specs  [30000k on video and high quality audio] in mkv wrapper

---

### Post by chalan2 on 2017-11-10
ok, thank you... what is the optimum settings to encode it to a good home use quality? audio and video... h265 or h264...

---

### Post by shantiq on 2017-11-10
I have written everything now please read info :]

---

### Post by chalan2 on 2017-11-11
ok its working thank you very much, now i need to reduce the size of the file for home use. I have FullHD 65" TV. I try to lower the bitrate to 10mbps but the file is still big as 2GB. 2GB h264 for 23min video is imho too much... so im asking you how to encode to have good quality and reasonable size... thank you, what i did:

1.) grab 1,2,3,4 audio streams from original .gxf file to 1L, 1R, 2L, 2R **ffmpeg -i 01-Útek.gxf  -vn -c:a copy -map 0:1 1L.wav** and **ffmpeg -i 01-Útek.gxf  -vn -c:a copy -map 0:2 1R.wav** and so on...
2.) import **1L.wav** and **1R.wav** to audacity, set 1L as LEFT and 1R as RIGHT after that mix and render it to one stereo track and export as .m4a (aac) **1stereo.m4a** the same with **2L.wav** and **2R.wav** to **2stereo.m4a**
3.) export video without audio from original .gxf file **ffmpeg -i 01-Útek.gxf -an -b:v 10000k -r 25 01-Útek.gxf_no_audio.mkv**
4.) join 1 and second stereo tracks to video without audio **ffmpeg -i 01-Útek.gxf_no_audio.mkv -i 1stereo.m4a -i 2stereo.m4a -map 0 -map 1 -map 2 -c copy 01-Útek_10mbps_m4a.mkv**

sizes:
```

chalan@chalan-Desktop:~/Desktop/test$ ls -lh
total 18G
-rw-r--r-- 1 chalan elson 1,9G nov 11 09:15 01-Útek_10mbps_m4a_h264.mkv
-rwxr-xr-x 1 chalan elson 6,1G nov  4 09:45 01-Útek.gxf
-rw-r--r-- 1 chalan elson 1,7G nov 11 01:13 01-Útek.gxf_no_audio.mkv
-rw-r--r-- 1 chalan elson 6,1G nov 10 20:44 01-Útek.mkv
-rw-r--r-- 1 chalan elson 132M nov  4 20:19 1L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 1R.wav
-rw-r--r-- 1 chalan elson  82M nov 10 23:08 1stereo.m4a
-rw-r--r-- 1 chalan elson 525M nov  4 21:00 1stereo.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 2L.wav
-rw-r--r-- 1 chalan elson 132M nov  4 20:20 2R.wav
-rw-r--r-- 1 chalan elson  85M nov 10 23:16 2stereo.m4a
-rw-r--r-- 1 chalan elson 525M nov  4 21:01 2stereo.wav

```

---

### Post by shantiq on 2017-11-11
&#9679; a reasonable size for video is 2500k or 3000k    that is plenty    maybe go to 4000k    and that is excellent for a computer

&#9679; for 65" screen let us say   5000k or up to 7000k

&#9679; you can also reduce the frame rate/s     by entering 
```
-r 30
```  instead of ```
-r 50
```     that also reduces size A LOT 

&#9679; you can also reduce the audio to say 192k but I would leave it as you have it

those are fairly standard sizes


Glad you got there.

---

### Post by chalan2 on 2017-11-11
thank you very much... is it possible to set variable bit rate from 5000k to 7000k? that file was with -r 25 isnt it to less? -r means fields per seconds or frames per seconds? 50frames=25fields=1sec? or 50fields=25frames=1sec?

---

### Post by shantiq on 2017-11-11
hmmm   never tried it myself but read [here]("https://trac.ffmpeg.org/wiki/Encode/MPEG-4") about -qscale:v n  ...   looks doable


maybe try ```
-qscale:v 20
```



PS :   i see you did not use

```
  ffmpeg -i YOURORIGINALFILE  -an -b:v 30000k [COLOR=#800000]*-r 50 -c:v libx265*[/COLOR]  MUTEVIDEO.mkv
```   when you made the mute video


[COLOR=#ff0000]-c:v libx265  [/COLOR][COLOR=#000000]would give you the h265 you wanted[/COLOR] ...  of course if you are now on default -r 25   do not go back up ///   just use [COLOR=#ff0000]-qscale:v n[/COLOR]    it looks useful

---

### Post by chalan2 on 2017-11-17
hello, thank you for your help, i was trying h265 and h264 with different profiles and this is the result:

```
-rwxr-xr-x 1 chalan elson 6,1G nov  4 09:45 01-Útek.gxf
-rw-r--r-- 1 chalan elson 671M nov 14 01:00 01-Útek.gxf_no_audio_ffmpeg_animation.mkv
-rw-r--r-- 1 chalan elson 525M nov 16 03:19 01-Útek.gxf_no_audio_ffmpeg_animation_veryslow.mkv
-rw-r--r-- 1 chalan elson 151M nov 17 01:12 01-Útek.gxf_no_audio_ffmpeg_h265.mkv
-rw-r--r-- 1 chalan elson 760M nov 14 09:28 01-Útek.gxf_no_audio_ffmpeg.mkv
-rw-r--r-- 1 chalan elson 1,7G nov 11 01:13 01-Útek.gxf_no_audio.mkv
```

i have chosen h265. but i have more than hundred of such files, is there a way to make automation script? first to extract audio streams from every file one after another and then another script to encode every file withou audio one by one with h265 and trhid script to join stereo streams into encoded video?

---

### Post by shantiq on 2017-11-17
No doubt it can be done
You have to find someone who can write a bullet-proof script ... :)
Maybe someone will see this thread and help you with it

---

### Post by chalan2 on 2017-11-17
i found out that ffmpeg is able to mix two mono tracks to one stereo... the command is ```
ffmpeg -i 1.L.wav -i 1.R.wav -filter_complex "[0:a][1:a]amerge=inputs=2[aout]" -map "[aout]" 1.STEREO.mkv
```

but isnt it possible to encode the .gxf with ffmpeg so that first and second audio track will be mixed to one stereo track with only one step (one command)? its too complicated to do it in these 4 steps...

1. grab only audio tracks
2. mix the tracks in audacity or sox or ffmpeg to one stereo track
3. encode video without audio
4. insert the stereo track to encoded video...

with one file its ok but with more that 100 its a nightmare, please help...

---

### Post by chalan2 on 2017-11-17
ok i make my first scripts

chalan@chalan-Desktop:~/Desktop/test1$ cat extractaudio.sh 
```
for file1 in ./*.gxf; do 
  file2=`echo $file1 | sed 's/.gxf/.1.L.wav/g'`;
  file3=`echo $file1 | sed 's/.gxf/.1.R.wav/g'`;
  file4=`echo $file1 | sed 's/.gxf/.2.L.wav/g'`;
  file5=`echo $file1 | sed 's/.gxf/.2.R.wav/g'`;
ffmpeg -i "$file1" -vn -c:a copy -map 0:1 "$file2";
ffmpeg -i "$file1" -vn -c:a copy -map 0:2 "$file3";
ffmpeg -i "$file1" -vn -c:a copy -map 0:3 "$file4";
ffmpeg -i "$file1" -vn -c:a copy -map 0:4 "$file5";
done
```

chalan@chalan-Desktop:~/Desktop/test1$ cat mixaudio.sh 
```
for file1 in ./*.L.wav; do 
  file2=`echo $file1 | sed 's_\(.*\).L.wav_\1.R.wav_'`;
  out=`echo $file1 | sed 's_\(.*\).L.wav_\1.STEREO.wav_'`;
  out1=`echo $file1 | sed 's_\(.*\).L.wav_\1.STEREO.mkv_'`;
  out2=`echo $file1 | sed 's_\(.*\).L.wav_\1.STEREO.m4a_'`;
#  sox -MS "$file1" "$file2" "$out";
#  ffmpeg -i "$file1" -i "$file2" -filter_complex "[0:a][1:a]amerge=inputs=2[aout]" -map "[aout]" "$out1"
  ffmpeg -i "$file1" -i "$file2" -filter_complex "[0:a][1:a]amerge=inputs=2[aout]" -map "[aout]" -strict -2 "$out2"
done
```

chalan@chalan-Desktop:~/Desktop/test1$ cat noaudio.sh 
```
for file1 in ./*.gxf; do 
  file2=`echo $file1 | sed 's/.gxf/_no_audio.mkv/g'`;
ffmpeg -i "$file1" -an -c libx265 "$file2"
done
```

chalan@chalan-Desktop:~/Desktop/test1$ cat insert_stereo.sh 
```
for file1 in ./*_no_audio.mkv; do 
  file2=`echo $file1 | sed 's/_no_audio.mkv/.1.STEREO.m4a/g'`;
  file3=`echo $file1 | sed 's/_no_audio.mkv/.2.STEREO.m4a/g'`;
  out=`echo $file1 | sed 's/_no_audio.mkv/.mkv/g'`;
ffmpeg -i "$file1" -i "$file2" -i "$file3" -map 0 -map 1 -map 2 -c copy "$out"
done
```

chalan@chalan-Desktop:~$ cat /media/public-merkur/rtvs_raw/Tao_Tao\ \(komplet\)/clean.sh 
```
#vymazeme .gxf .wav a stereo file (skontroluj ci je vsetko OK)!!!
rm *.wav
rm *STEREO.m4a
rm *_no_audio.mkv
#rm *.gxf

done

```

will see if they works

---

### Post by evilsoup on 2017-11-30
Right, I'm mostly going off memory here so let me know whether the commands work or not.

You can actually do the entire process for each file with a single ffmpeg command, no need for any intermediate files. This produces two output MKV files, one with the first two audio tracks mixed into a single stereo track, and one with the third and fourth audio tracks mixed into a single audio track:

```
ffmpeg -i input.gfx -filter_complex '[0:a:0][0:a:1]amerge[langa];[0:a:2][0:a:3]amerge[langb]' -map v -map '[langa]' -codec:v copy -codec:a pcm_s16le out1.mkv -map v -map '[langb]' -codec:v copy -codec:a pcm_s16le out2.mkv
```

As for compressing the video, I would recommend having a look at the [H.264 encoding guide]("https://trac.ffmpeg.org/wiki/Encode/H.264") and the [AAC encoding guide]("https://trac.ffmpeg.org/wiki/Encode/AAC") on the ffmpeg wiki. You'll probably want to use MP4 rather than MKV, since your TV is more likely to support that (this is also why I'm recommending H.264 rather than H.265, even though the latter would give you roughly half the filesize). It might be worthwhile compiling your own version of ffmpeg ([it's not hard]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu")) to get fdk_aac -- I used to do this when I was regularly using ffmpeg, but that was a few years ago & so I don't know the current quality of the native AAC encoder. I'd suggest testing on one video and seeing if the audio quality is good enough.

Here's a potential command to give you two MP4 files (you have to put the output options for each output file seperately):

```
ffmpeg -i input.gfx -filter_complex '[0:a:0][0:a:1]amerge[langa];[0:a:2][0:a:3]amerge[langb]' -map v -map '[langa]' -codec:v libx264 -preset slow -crf 18  codec:a aac -b:a 160k out1.mp4 -map v -map '[langb]' -codec:v libx264 -preset slow -crf 18  codec:a aac -b:a 160k out2.mkv
```

Once you've tested it out you can put the whole thing in a for loop.

---

