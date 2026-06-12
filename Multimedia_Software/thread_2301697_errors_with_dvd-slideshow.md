---
title: "errors with dvd-slideshow"
date: 2015-11-04
forum: Multimedia Software
---

### Post by George Heine on 2015-11-04
Hello - Installed dvd-slideshow in attempt to begin creating a slideshow with several hundred images.
This will be a silent slideshow.

I have worked with ffmpeg and dvdauthor in the past, and could probably (with a lot of work) create the slideshow manually, but am hoping that there is some simple error in my execution of dvd-slideshow.  Any suggestions would be appreciated

Created a very simple file "Test.txt" :
```
title:4:Volume 3 \n Test Slideshow
Vol3_20151029_0001.jpg:4:Slide 1
Vol3_20151029_0002.jpg:4:Slide 2
```

My first attempt:
```
dvd-slideshow -n Test -f Test.txt
```
seemed to generate a lot of errors about "no audio file found".  To avoid this, created a silent audio file with
```
ffmpeg -f s16le  -ac 2 -ar 48000 -i /dev/zero -t 40 -y 40sec.mp3
```
and then
```
 dvd-slideshow -n Test -f Test.txt -a 40sec.mp3 
```
also tried with an "-mp2" switch at the end, and creating/using a silent audio in "wav" format

All these attempts failed.  There were numerous errors in reading the audio file:
```
soxi FAIL formats: can't open input file `-D': No such file or directory
(standard_in) 2: syntax error
(standard_in) 2: illegal character: I
(standard_in) 2: illegal character: : 
(standard_in) 2: illegal character: '
(standard_in) 2: illegal character: S
(standard_in) 2: illegal character: N
(standard_in) 2: syntax error
...
/usr/bin/dvd-slideshow: line 4775: 0 +  : syntax error: operand expected (error token is "+  ")
soxi FAIL formats: can't open input file `-D': No such file or directory
...
(standard_in) 9: illegal character: M
/usr/bin/dvd-slideshow: line 6822: [: : integer expression expected
/usr/bin/dvd-slideshow: line 6828: 0 +  : syntax error: operand expected (error token is "+  ")
sox WARN sox: Option `-s' is deprecated, use `-e signed-integer' instead.
sox WARN sox: Option `-2' is deprecated, use `-b 16' instead.
sox WARN sox: Option `-2' is deprecated, use `-b 16' instead.
sox WARN sox: Option `-s' is deprecated, use `-e signed-integer' instead.

```
and then dvd-nav failed with
```
[dvd-slideshow] ERROR: no output .mpg file found!
[dvd-slideshow] This usually happens when avconv screws up something

```

Here is the complete log file:
```

[dvd-slideshow] Wed Nov  4 10:50:15 MST 2015
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -n Test -f Test.txt -a 40sec.wav
[dvd-slideshow] dvd-slideshow version 0.8.4-1
[dvd-slideshow] Linux athena 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:12:08 UTC 2015 i686 i686 i686 GNU/Linux
[dvd-slideshow] Output directory=/media/gheine/SAN16Linux/Vol3
[dvd-slideshow] Locale:
LANG=POSIX
LANGUAGE=en_US
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
[dvd-slideshow] Using /bin/bash version GNU bash, version 4.3.11(1)-release (i686-pc-linux-gnu)
[dvd-slideshow] Found findutils version 4.4.2
[dvd-slideshow] Found mjpegtools version 2.1.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.4.1
[dvd-slideshow] using sox options -2 -n
[dvd-slideshow] Found ImageMagick version 6.7.7-10
[dvd-slideshow] Found dvdauthor version 0.7.0.
[dvd-slideshow] avconv version 9.18-6:9.18-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input file Test.txt
[dvd-slideshow]############################################################
[dvd-slideshow] Title font is /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle font is /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Found 2 images.
[dvd-slideshow] Found 1 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 0 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 256k
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Title_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Running initial error check...
[dvd-slideshow]############################################################
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Processing wav audio 40sec.wav
[dvd-slideshow] Error in hms function: no input
[dvd-slideshow] Total audio length =
[dvd-slideshow] Total video length = 0:0:12.000
[dvd-slideshow] Temp dir is ...SAN16Linux/Vol3/dvd-slideshow_temp_14660
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:4.000
[dvd-slideshow]         Title=Volume 3 \n Test Slideshow
[dvd-slideshow] Found \n in title
[dvd-slideshow]############################################################
[dvd-slideshow] 1/2 Vol3_20151029_0001.jpg 0:0:4.000
[dvd-slideshow] Subtitle= Slide 1
[dvd-slideshow]############################################################
[dvd-slideshow] 2/2 Vol3_20151029_0002.jpg 0:0:4.000
[dvd-slideshow] Subtitle= Slide 2
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc/avconv process=15207
[dvd-slideshow] output from ps:
  PID TTY      STAT   TIME COMMAND
15207 pts/4    S+     0:00 avconv -threads 1 -f yuv4mpegpipe -i /media/gheine/SAN16Linux/Vol3/dvd-slideshow_temp_14660/dvdss-pipe-14660 -target ntsc-dvd -r 29.97 -an -aspect 4:3 -s 720x480 -y -bf 2 -f mpeg2video /media/gheine/SAN16Linux/Vol3/dvd-slideshow_temp_14660/video.mpg
[dvd-slideshow] waiting for encoder to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 1
[dvd-slideshow] 40sec.wav
[dvd-slideshow] Error in hms function: no input
[dvd-slideshow] fade_in_time=0:0:2.000 fade_out_time=0:0:2.000
[dvd-slideshow] No audio files passed. Using 0:0:12.000 silence.
[dvd-slideshow] Working on track 1 audio file 1
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:12.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:12.000
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR: no output .mpg file found!
[dvd-slideshow] This usually happens when avconv screws up something
[dvd-slideshow] or one image is messed up and the resulting video can't be created
[dvd-slideshow]############################################################
[dvd-slideshow] Multiplexing audio and video...
[dvd-slideshow] Some sequence marker warnings here are normal
**ERROR: [mplex] Unable to open file /media/gheine/SAN16Linux/Vol3/dvd-slideshow_temp_14660/video.mpg for reading.
[dvd-slideshow] ERROR during mplex execution!
[dvd-slideshow] see Test.log for details
[dvd-slideshow] cleanup...

```

And here is my ffmpeg information:
```

ffmpeg version git-2015-06-03-7495e72 Copyright (c) 2000-2015 the FFmpeg developers
built with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
configuration: --prefix=/home/gheine/ffmpeg_build --extra-cflags=-I/home/gheine/ffmpeg_build/include --extra-ldflags=-L/home/gheine/ffmpeg_build/lib --bindir=/home/gheine/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
libavutil      54. 26.101 / 54. 26.101
libavcodec     56. 41.101 / 56. 41.101
libavformat    56. 34.100 / 56. 34.100 
libavdevice    56.  4.100 / 56.  4.100
libavfilter     5. 16.101 /  5. 16.101
libswscale      3.  1.101 /  3.  1.101
libswresample   1.  1.100 /  1.  1.100
libpostproc    53.  3.100 / 53.  3.100

```

Again, any input would be much appreciated.

---

