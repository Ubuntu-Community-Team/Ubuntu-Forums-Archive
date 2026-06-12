---
title: "QDVDAuthor not working..."
date: 2008-09-30
forum: Multimedia Software
---

### Post by chipyoung on 2008-09-30
When trying to create a DVD composed of JPEG files I get an error message.  It is related to ffmpeg.  I have included my log file.

[dvd-slideshow] Tue Sep 30 12:24:48 EDT 2008
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -p -o /tmp/test/ -n slideshow -f /tmp/test//My Slideshow.in -b /tmp/test/background.jpg -t 5
[dvd-slideshow] dvd-slideshow version 0.7.5
[dvd-slideshow] Linux Newbox 2.6.24-19-386 #1 Wed Aug 20 21:59:50 UTC 2008 i686 GNU/Linux
[dvd-slideshow] Output directory=/tmp/test
[dvd-slideshow] Using /bin/bash version GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.8.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.0.0
[dvd-slideshow] Found ImageMagick version 6.3.7
[dvd-slideshow] Found dvdauthor version 0.6.14.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
[dvd-slideshow] Font=-font /usr/share/fonts/X11/Type1/n019004l.pfb
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input .txt file /tmp/test//My Slideshow.in
[dvd-slideshow]############################################################
[dvd-slideshow] Found 2 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 3 transitions (fadein/fadeout/crossfade).
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Total video length = 0:0:29.000
[dvd-slideshow] Temp dir is /tmp/test/dvd-slideshow_temp_16160
COMMAND         PID   USER   FD   TYPE DEVICE SIZE   NODE NAME
dvd-slideshow 16160 cyoung    3w  FIFO    8,4      104333 /tmp/test/dvd-slideshow_temp_16160/dvdss-pipe-16160
[dvd-slideshow] Creating background using /tmp/test/background.jpg
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:10.000
[dvd-slideshow]         Title=My Slideshow
[dvd-slideshow]############################################################
[dvd-slideshow] Fadein 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] 1/2 /home/cyoung/Desktop/superbowl/DSC00041.JPG 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] 2/2 //tmp/test//DSC00042.png 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=16801
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
16801 ?        S      0:27 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /tmp/test/dvd-slideshow_temp_16160/video_0.mpg
COMMAND         PID   USER   FD   TYPE DEVICE    SIZE   NODE NAME
dvd-slideshow 16160 cyoung    3w  FIFO    8,4         104333 /tmp/test/dvd-slideshow_temp_16160/dvdss-pipe-16160
mpeg2enc      16801 cyoung    3w   REG    8,4 5779456 105068 /tmp/test/dvd-slideshow_temp_16160/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:0:29.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:29.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:29.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
[dvd-slideshow] Creating ac3 audio...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/tmp/test/dvd-slideshow_temp_16160/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /tmp/test/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

Any help would be greatly appreciated.  I have removed and reloaded QDVDAuthor to no avail.

Thank you,
Chip

---

### Post by ajhunt on 2008-10-01
Hi!

I've had something similar before now and found that mpg123 was missing:

> sudo apt-get install mpg123 

If this isn't the case for you, could you post /tmp/test/dvd-slideshow.log as this may give more of a clue as to what the problem is.

---

### Post by chipyoung on 2008-10-01
Ajhunt,

Thanks for your suggestion about adding mpg123.  I did not have that installed.  I added that, but still no luck.  I have included my log file for you to take a look at.  I hope that will help.


[dvd-slideshow] Wed Oct  1 10:43:03 EDT 2008
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -p -o /tmp/jpegtest/ -n slideshow -f /tmp/jpegtest//My Slideshow.in -b  -t 5
[dvd-slideshow] dvd-slideshow version 0.7.5
[dvd-slideshow] Linux Newbox 2.6.24-19-386 #1 Wed Aug 20 21:59:50 UTC 2008 i686 GNU/Linux
[dvd-slideshow] Output directory=/tmp/jpegtest
[dvd-slideshow] Using /bin/bash version GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.8.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.0.0
[dvd-slideshow] Found ImageMagick version 6.3.7
[dvd-slideshow] Found dvdauthor version 0.6.14.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
[dvd-slideshow] Font=-font /usr/share/fonts/X11/Type1/n019004l.pfb
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input .txt file /tmp/jpegtest//My Slideshow.in
[dvd-slideshow]############################################################
[dvd-slideshow] Found 2 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 3 transitions (fadein/fadeout/crossfade).
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Total video length = 0:0:29.000
[dvd-slideshow] Temp dir is /tmp/jpegtest/dvd-slideshow_temp_7854
COMMAND        PID   USER   FD   TYPE DEVICE SIZE   NODE NAME
dvd-slideshow 7854 cyoung    3w  FIFO    8,4      201266 /tmp/jpegtest/dvd-slideshow_temp_7854/dvdss-pipe-7854
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:10.000
[dvd-slideshow]         Title=My Slideshow
[dvd-slideshow]############################################################
[dvd-slideshow] Fadein 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] 1/2 /home/cyoung/Desktop/superbowl/DSC00041.JPG 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] 2/2 //tmp/jpegtest//DSC00042.png 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=8495
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
 8495 ?        S      0:27 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /tmp/jpegtest/dvd-slideshow_temp_7854/video_0.mpg
COMMAND        PID   USER   FD   TYPE DEVICE    SIZE   NODE NAME
dvd-slideshow 7854 cyoung    3w  FIFO    8,4         201266 /tmp/jpegtest/dvd-slideshow_temp_7854/dvdss-pipe-7854
mpeg2enc      8495 cyoung    3w   REG    8,4 5648384 201308 /tmp/jpegtest/dvd-slideshow_temp_7854/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:0:29.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:29.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:29.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
[dvd-slideshow] Creating ac3 audio...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/tmp/jpegtest/dvd-slideshow_temp_7854/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /tmp/jpegtest/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

Just one other thing I should mention.  I get a warning box after the process fails which say's;

WARNING, The slideshow [01] -my slideshow is not finished.  The sourcefileentry will not be stored.

I get one of these warnings about every 2 minutes.

Thanks again,
Chip

---

### Post by shane2peru on 2008-10-10
> **chipyoung said:**
> Ajhunt,

Thanks for your suggestion about adding mpg123.  I did not have that installed.  I added that, but still no luck.  I have included my log file for you to take a look at.  I hope that will help.


[dvd-slideshow] Wed Oct  1 10:43:03 EDT 2008
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -p -o /tmp/jpegtest/ -n slideshow -f /tmp/jpegtest//My Slideshow.in -b  -t 5
[dvd-slideshow] dvd-slideshow version 0.7.5
[dvd-slideshow] Linux Newbox 2.6.24-19-386 #1 Wed Aug 20 21:59:50 UTC 2008 i686 GNU/Linux
[dvd-slideshow] Output directory=/tmp/jpegtest
[dvd-slideshow] Using /bin/bash version GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.8.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.0.0
[dvd-slideshow] Found ImageMagick version 6.3.7
[dvd-slideshow] Found dvdauthor version 0.6.14.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
[dvd-slideshow] Font=-font /usr/share/fonts/X11/Type1/n019004l.pfb
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input .txt file /tmp/jpegtest//My Slideshow.in
[dvd-slideshow]############################################################
[dvd-slideshow] Found 2 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 3 transitions (fadein/fadeout/crossfade).
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Total video length = 0:0:29.000
[dvd-slideshow] Temp dir is /tmp/jpegtest/dvd-slideshow_temp_7854
COMMAND        PID   USER   FD   TYPE DEVICE SIZE   NODE NAME
dvd-slideshow 7854 cyoung    3w  FIFO    8,4      201266 /tmp/jpegtest/dvd-slideshow_temp_7854/dvdss-pipe-7854
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:10.000
[dvd-slideshow]         Title=My Slideshow
[dvd-slideshow]############################################################
[dvd-slideshow] Fadein 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] 1/2 /home/cyoung/Desktop/superbowl/DSC00041.JPG 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] 2/2 //tmp/jpegtest//DSC00042.png 0:0:5.000
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=8495
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
 8495 ?        S      0:27 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /tmp/jpegtest/dvd-slideshow_temp_7854/video_0.mpg
COMMAND        PID   USER   FD   TYPE DEVICE    SIZE   NODE NAME
dvd-slideshow 7854 cyoung    3w  FIFO    8,4         201266 /tmp/jpegtest/dvd-slideshow_temp_7854/dvdss-pipe-7854
mpeg2enc      8495 cyoung    3w   REG    8,4 5648384 201308 /tmp/jpegtest/dvd-slideshow_temp_7854/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:0:29.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:29.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:29.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
[dvd-slideshow] Creating ac3 audio...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/tmp/jpegtest/dvd-slideshow_temp_7854/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /tmp/jpegtest/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

Just one other thing I should mention.  I get a warning box after the process fails which say's;

WARNING, The slideshow [01] -my slideshow is not finished.  The sourcefileentry will not be stored.

I get one of these warnings about every 2 minutes.

Thanks again,
Chip

ffmpeg has problems to fix it you need to run this:

```

sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow

```

Alternately you could edit the file: /usr/bin/dvd-slideshow and everywhere you find "-ab 192" ad the 'k'  to the end of it.  If you search the forums for problems with ffmpeg you will find this solution posted several times.  That is how I stumbled across your thread, looking for the solution ... again. :)  Hope this helps.

Shane

---

### Post by chipyoung on 2008-10-11
Shane,

Thank you for your suggestion.  I executed the code for ffmpeg, but it didn't seem to do anything.  After looking around the forums I found one individual who also installed libsox-fmt-all.  I tried this and now everything is working.

Now it's time to dig deeper to master this program.

Thanks again,
Chip

---

### Post by shane2peru on 2008-10-11
> **chipyoung said:**
> Shane,

Thank you for your suggestion.  I executed the code for ffmpeg, but it didn't seem to do anything.  After looking around the forums I found one individual who also installed libsox-fmt-all.  I tried this and now everything is working.

Now it's time to dig deeper to master this program.

Thanks again,
Chip

Chip,

That command wouldn't give you any response, it would just search through the program and fix the error in the application.  After running that (it only needs run once) it would fix the problem, then running QDvdAuthor should work without a problem.  Sorry if I didn't explain that very clearly.  At any rate, glad you got it working.  

Shane

---

