---
title: "dvd-slideshow ffmpeg error"
date: 2013-08-20
forum: Multimedia Software
---

### Post by bill-lancaster on 2013-08-20
~$ dvd-slideshow -n 'Cruise' -f Documents/CruiseDVD.txt

produces:-  ERROR during ffmpeg execution!

Note: No audio file was specified as I'm not interested in background sound for this project but I get the same error using .mp3 or .ogg audio files.

There are several posts regarding this but seem to have very complex solutions.

Surely there is some simple solution to this!

Any help would be appreciated.

Kubuntu 12.10
dvd-slideshow 0.8.2
ffmpeg version 0.8.5-6:0.8.5

---

### Post by bill-lancaster on 2013-08-20
Have read that removing ffmpeg and re-installing solved the problem - not for me though!

This code follows what seems to a lot of routine output when dvd-slideshow eas run:-


bin/dvd-slideshow: line 6641: 23922 Aborted                 (core dumped) ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab "$audio_bitrate"k -acodec ac3 -vol "100" -ar $audio_sample_rate -ac 6 "$tmpdir/audio1.ac3" >> "$ffmpeg_out" 2>&1
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/bill/Cruise.log for details
[dvd-slideshow] cleanup...

---

### Post by FakeOutdoorsman on 2013-08-20
> ```
[dvd-slideshow] see /home/bill/Cruise.log for details
```
The contents of "/home/bill/Cruise.log" may provide useful details.

Usage of the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) will help deliniate between your comments and the information displayed in your term

---

### Post by bill-lancaster on 2013-08-20
Thanks,
Here is content of cruise.log

[dvd-slideshow] Tue Aug 20 14:52:53 BST 2013
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -n Cruise -f Documents/CruiseDVD.txt -a audio.mp3
[dvd-slideshow] dvd-slideshow version 0.8.2
[dvd-slideshow] Linux bill-CQ2960EA 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[dvd-slideshow] Output directory=/home/bill
[dvd-slideshow] Locale: 
LANG=POSIX
LANGUAGE=en_GB:en
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
[dvd-slideshow] Using /bin/bash version GNU bash, version 4.2.37(1)-release (x86_64-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.9.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.4.0
[dvd-slideshow] Found ImageMagick version 6.7.7-10
[dvd-slideshow] Found dvdauthor version 0.7.0.
ffmpeg version 0.8.6-6:0.8.6-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:16 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
ffmpeg 0.8.6-6:0.8.6-0ubuntu0.12.10.1
libavutil    51. 22. 1 / 51. 22. 1
libavcodec   53. 35. 0 / 53. 35. 0
libavformat  53. 21. 1 / 53. 21. 1
libavdevice  53.  2. 0 / 53.  2. 0
libavfilter   2. 15. 0 /  2. 15. 0
libswscale    2.  1. 0 /  2.  1. 0
libpostproc  52.  0. 0 / 52.  0. 0
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input file Documents/CruiseDVD.txt
[dvd-slideshow]############################################################
[dvd-slideshow] Title font is /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle font is /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Found 3 images.
[dvd-slideshow] Found 1 audio files.
[dvd-slideshow] Found 2 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 3 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 192k
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Using SMP optimizations for multi-processor machines
[dvd-slideshow] Title_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Running initial error check...
[dvd-slideshow]############################################################
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Decoding mp3 audio: audio.mp3
[dvd-slideshow] Total audio length = 0:3:10.406
[dvd-slideshow] Total video length = 0:0:22.000
[dvd-slideshow] Temp dir is /home/bill/dvd-slideshow_temp_20689
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:5.000
[dvd-slideshow]         Title=Channel Island Cruise
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadein to next image 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] 1/3 Pictures/temp3/P1010004.JPG 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] 2/3 Pictures/temp3/P1010005.JPG 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] 3/3 Pictures/temp3/P1010006.JPG 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=22054
[dvd-slideshow] output from ps:
  PID TTY      STAT   TIME COMMAND
22054 pts/2    S+     0:03 ffmpeg -f yuv4mpegpipe -i /home/bill/dvd-slideshow_temp_20689/dvdss-pipe-20689 -target ntsc-dvd -r 29.97 -an -aspect 4:3 -s 720x480 -y -bf 2 -f mpeg2video /home/bill/dvd-slideshow_temp_20689/video.mpg
[dvd-slideshow] waiting for encoder to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 1
[dvd-slideshow] audio.mp3
[dvd-slideshow] fade_in_time=0:0:2.000 fade_out_time=0:0:2.000
[dvd-slideshow] total_audio_length=0:3:10.406
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio for audio.mp3...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/bill/Cruise.log for details
[dvd-slideshow] cleanup...

---

### Post by FakeOutdoorsman on 2013-08-20
Please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code).

---

### Post by bill-lancaster on 2013-08-21
Is this what is meant by code tag?
```
[dvd-slideshow] Tue Aug 20 14:52:53 BST 2013
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -n Cruise -f Documents/CruiseDVD.txt -a audio.mp3
[dvd-slideshow] dvd-slideshow version 0.8.2
[dvd-slideshow] Linux bill-CQ2960EA 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[dvd-slideshow] Output directory=/home/bill
[dvd-slideshow] Locale: 
LANG=POSIX
LANGUAGE=en_GB:en
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
[dvd-slideshow] Using /bin/bash version GNU bash, version 4.2.37(1)-release (x86_64-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.9.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.4.0
[dvd-slideshow] Found ImageMagick version 6.7.7-10
[dvd-slideshow] Found dvdauthor version 0.7.0.
ffmpeg version 0.8.6-6:0.8.6-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
built on Apr 2 2013 17:02:16 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
ffmpeg 0.8.6-6:0.8.6-0ubuntu0.12.10.1
libavutil 51. 22. 1 / 51. 22. 1
libavcodec 53. 35. 0 / 53. 35. 0
libavformat 53. 21. 1 / 53. 21. 1
libavdevice 53. 2. 0 / 53. 2. 0
libavfilter 2. 15. 0 / 2. 15. 0
libswscale 2. 1. 0 / 2. 1. 0
libpostproc 52. 0. 0 / 52. 0. 0
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input file Documents/CruiseDVD.txt
[dvd-slideshow]################################################## ##########
[dvd-slideshow] Title font is /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle font is /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Found 3 images.
[dvd-slideshow] Found 1 audio files.
[dvd-slideshow] Found 2 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 3 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 192k
[dvd-slideshow] Debug=0 Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Using SMP optimizations for multi-processor machines
[dvd-slideshow] Title_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Running initial error check...
[dvd-slideshow]################################################## ##########
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Decoding mp3 audio: audio.mp3
[dvd-slideshow] Total audio length = 0:3:10.406
[dvd-slideshow] Total video length = 0:0:22.000
[dvd-slideshow] Temp dir is /home/bill/dvd-slideshow_temp_20689
[dvd-slideshow] Creating black background
[dvd-slideshow]################################################## ##########
[dvd-slideshow] Title 0:0:5.000
[dvd-slideshow] Title=Channel Island Cruise
[dvd-slideshow]################################################## ##########
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]################################################## ##########
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]################################################## ##########
[dvd-slideshow] Applying Fadein to next image 0:0:1.000
[dvd-slideshow]################################################## ##########
[dvd-slideshow] 1/3 Pictures/temp3/P1010004.JPG 0:0:5.000
[dvd-slideshow]################################################## ##########
[dvd-slideshow] 2/3 Pictures/temp3/P1010005.JPG 0:0:5.000
[dvd-slideshow]################################################## ##########
[dvd-slideshow] 3/3 Pictures/temp3/P1010006.JPG 0:0:5.000
[dvd-slideshow]################################################## ##########
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]################################################## ##########
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]################################################## ##########
[dvd-slideshow] mpeg2enc process=22054
[dvd-slideshow] output from ps:
PID TTY STAT TIME COMMAND
22054 pts/2 S+ 0:03 ffmpeg -f yuv4mpegpipe -i /home/bill/dvd-slideshow_temp_20689/dvdss-pipe-20689 -target ntsc-dvd -r 29.97 -an -aspect 4:3 -s 720x480 -y -bf 2 -f mpeg2video /home/bill/dvd-slideshow_temp_20689/video.mpg
[dvd-slideshow] waiting for encoder to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 1
[dvd-slideshow] audio.mp3
[dvd-slideshow] fade_in_time=0:0:2.000 fade_out_time=0:0:2.000
[dvd-slideshow] total_audio_length=0:3:10.406
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio for audio.mp3...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/bill/Cruise.log for details
[dvd-slideshow] cleanup...
```

---

### Post by FakeOutdoorsman on 2013-08-21
Yes, thanks, but unfortunately it does not seem to actually show the "ERROR" that the log refers to so I have no other ideas.

---

