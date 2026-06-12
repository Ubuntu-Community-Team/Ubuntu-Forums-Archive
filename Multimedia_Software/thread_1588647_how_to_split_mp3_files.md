---
title: "how to split mp3 files"
date: 2010-10-05
forum: Multimedia Software
---

### Post by bill-lancaster on 2010-10-05
Can anyone give me an example?

I want to split audio files at cirtain point in time.

Thanks

---

### Post by sanderd17 on 2010-10-05
Audacity can do the trick.

```

sudo aptitude install audacity
audacity

```

You do need the mp3 codecs to edit mp3's. If you can play mp3, you have the codecs.

---

### Post by viralmeme on 2010-10-05
> **bill-lancaster said:**
> I want to split audio files at cirtain point in time.

[split an audio file using ffmpeg]("http://www.qc4blog.com/?p=870")

[About Cinelerra]("http://cinelerra.org/")

---

### Post by bill-lancaster on 2010-10-05
Thanks for the suggestion.

I'm looking for a command line to do the job

Bill Lancaster

---

### Post by bill-lancaster on 2010-10-05
OK, ffmpeg looks interesting, here is what I got


bill@ubuntu:~$  ffmpeg -f mp3 -i /home/bill/classic.mp3 -t  00:10:00 -ss 00:20:00 - o /home/bill/save.mp3

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
Input #0, mp3, from '/home/bill/classic.mp3':
  Duration: 02:52:16.05, start: 0.000000, bitrate: 127 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
Unable to find a suitable output format for 'pipe:'

Any ideas?

Bill Lancaster

---

### Post by ron999 on 2010-10-05
This command should be OK:-
```
ffmpeg -i /home/bill/classic.mp3 -t 00:10:00 -ss 00:20:00 -acodec copy /home/bill/save.mp3
```

Edit
The above command should start 20 minutes in with 10 minutes duration.

---

### Post by bill-lancaster on 2010-10-05
Ron999 - it works a treat.
Many thanks

---

### Post by bill-lancaster on 2010-10-06
I spoke too soon!
The split file has no sound.
Here is what happened:-

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
Input #0, mp3, from '/home/bill/classic.mp3':
  Duration: 02:52:16.05, start: 0.000000, bitrate: 127 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
Output #0, mp3, to '/home/bill/save.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=1200.03 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead 7.673861%

Any ideas?

---

### Post by ron999 on 2010-10-06
Hi
Make sure that the encoders are enabled.
Use method B or C in the tutorial.
**HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg ** 

Here:- [http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

---

### Post by andrew.46 on 2010-10-06
Hi Bill,

Have you had a look at [mp3splt]("http://packages.ubuntu.com/lucid/mp3splt")?

Andrew

---

### Post by bill-lancaster on 2010-10-06
Thanks for the suggestion Andrew.  I've looked at mp3splt and mencoder.

Same problem - so many options and so little documentation!

Bill

---

### Post by nothingspecial on 2010-10-06
ffmpeg should work, did you enable mp3 encoding?

The reason I`m posting though is I`v always thought mencoder/mplayer had too much documentation. The man pages are huge.

When searching man pages press the / key

Then type the word you are looking for, whatever it is mp3 for example, then press Enter.

This will perform a search of the man page for that string, If you press the N key it will go to the next place that string appears. Makes reading man pages a lot easier.


This is actually a feature of less, which opens the man pages. You can search any text file with less in this way.

---

### Post by andrew.46 on 2010-10-06
Hi bill,

> **bill-lancaster said:**
> Thanks for the suggestion Andrew.  I've looked at mp3splt and mencoder.

Same problem - so many options and so little documentation!

In defense of mp3splt the documentation in the man pages is actually pretty comprehensive, in particular at the bottom you will see some examples given which spell out the basic usage. To follow Ron's example you could start 10 minutes into a file and extract 20 minutes as follows:

```

andrew@skamandros~/music/ftgws$ **[COLOR="Red"]mp3splt ftgws_03102010.mp3 10.00 30.00[/COLOR]**
mp3splt 2.2.6a (30/07/09) - using libmp3splt 0.5.7a
	Matteo Trotta <mtrotta AT users.sourceforge.net>
	Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'ftgws_03102010.mp3' ...
 info: file matches the plugin 'mp3 (libmad)'
 info: MPEG 1 Layer 3 - 44100 Hz - Joint Stereo - FRAME MODE - Total time: 131m.57s
 info: starting normal split
   File "ftgws_03102010_10m_00s__30m_00s.mp3" created                    
 Processed 68907 frames - Sync errors: 0
 file split


```

Another usage would be to split the file into 20 minute lengths:

```

andrew@skamandros~/music/ftgws$ **[COLOR="Red"]mp3splt -t  20.00 ftgws_03102010.mp3[/COLOR]**
mp3splt 2.2.6a (30/07/09) - using libmp3splt 0.5.7a
	Matteo Trotta <mtrotta AT users.sourceforge.net>
	Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'ftgws_03102010.mp3' ...
 info: file matches the plugin 'mp3 (libmad)'
 info: MPEG 1 Layer 3 - 44100 Hz - Joint Stereo - FRAME MODE - Total time: 131m.57s
 info: starting time mode split
   File "ftgws_03102010_00m_00s__20m_00s.mp3" created                   
   File "ftgws_03102010_20m_00s__40m_00s.mp3" created                   
   File "ftgws_03102010_40m_00s__60m_00s.mp3" created                   
   File "ftgws_03102010_60m_00s__80m_00s.mp3" created                   
   File "ftgws_03102010_80m_00s__100m_00s.mp3" created                   
   File "ftgws_03102010_100m_00s__120m_00s.mp3" created                   
   File "ftgws_03102010_120m_00s__131m_57s_08h.mp3" created                 
 Processed 303077 frames - Sync errors: 0
 time split ok

```

Plus a lot more options carefully explained in the man pages :).

Andrew

---

