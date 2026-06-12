---
title: "best &amp; fastest way to convert audio files?"
date: 2009-10-12
forum: Multimedia Software
---

### Post by HarmonicaGoldfish on 2009-10-12
I am trying to convert a podcast I downloaded from ram to mp3. I tried using perl audio converter (pacpl) but it seemed to be hanging. 40 minutes after starting the conversion it still had not completed. So then I installed Nautilus convert audio file, but when I went to use it on the ram file was told that the format was not supported.

any clean and easy solutions?

thanks

---

### Post by Charybdisz on 2009-10-12
I use SoundConverter, it works fine. [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)
Use Synaptic to install it.

---

### Post by SuperSonic4 on 2009-10-12
Command Line ffmpeg is fastest

---

### Post by HarmonicaGoldfish on 2009-10-12
> **SuperSonic4 said:**
> Command Line ffmpeg is fastest

What is the code for that?

---

### Post by HarmonicaGoldfish on 2009-10-12
I'm guessing that soundconverter doesn't work with ram. When I select the file it does not add to the program.

---

### Post by SuperSonic4 on 2009-10-12
At it's most basic

```
ffmpeg -i input.ram -acodec libvorbis output.ogg
```

Insert **libmp3lame** instead of libvorbis if you want mp3

```
man ffmpeg
```

---

### Post by HarmonicaGoldfish on 2009-10-12
this was what happened:
```
tracy@tracy-mini:~/Music$ ffmpeg -i shallownesscrisistapestry.ram libmp3lame shallownesscrisistapestry.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
Input #0, rtsp, from 'shallownesscrisistapestry.ram':
  Duration: 00:54:03.34, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Audio: cook, 44100 Hz, mono, s16, 64 kb/s
Unable to find a suitable output format for 'libmp3lame'
tracy@tracy-mini:~/Music$
```

---

### Post by SuperSonic4 on 2009-10-12
You didn't pass the -acodec flag. What it tried to do what to write libmp3lame as the output

```
ffmpeg -i shallownesscrisistapestry.ram -acodec libmp3lame shallownesscrisistapestry.mp3
```

If that doesn't work can you post the output of ```
ffmpeg -formats | grep mp3
```

---

### Post by HarmonicaGoldfish on 2009-10-12
oops!

Though, when I tried that I was met with:

```
tracy@tracy-mini:~/Music$ ffmpeg -i shallownesscrisistapestry.ram -acodec libmp3lame shallownesscrisistapestry.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
Input #0, rtsp, from 'shallownesscrisistapestry.ram':
  Duration: 00:54:03.34, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Audio: cook, 44100 Hz, mono, s16, 64 kb/s
Unknown encoder 'libmp3lame'
```

---

### Post by SuperSonic4 on 2009-10-12
It could be that ubuntu has a different naming scheme to arch

OK, what is the output of ```
ffmpeg -formats | grep mp3
```

---

### Post by HarmonicaGoldfish on 2009-10-12
```
tracy@tracy-mini:~/Music$ ffmpeg -formats | grep mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
 DE mp3             MPEG audio layer 3
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 text2movsub remove_extra noise mov2textsub mp3decomp mp3comp mjpegadump imxdump h264_mp4toannexb dump_extra
tracy@tracy-mini:~/Music$ 
```

---

### Post by SuperSonic4 on 2009-10-12
It looks like it's simply mp3:

```
ffmpeg -i shallownesscrisistapestry.ram -acodec mp3 shallownesscrisistapestry.mp3
```

If that doesn't work what does ```
ffmpeg -i | grep ram
``` come up with? You may not be able to decode it but who knows

---

### Post by HarmonicaGoldfish on 2009-10-12
mp3 brought me another unknown encoder message. 

Here is the output from ```
ffmpeg -i | grep ram
```
```

tracy@tracy-mini:~/Music$ ffmpeg -i | grep ram
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
ffmpeg: missing argument for option '-i'
tracy@tracy-mini:~/Music$ 
```

---

### Post by SuperSonic4 on 2009-10-12
My bad, that was a typo ```
ffmpeg -formats | grep ram
```

Can you convert to anything else but mp3?

---

### Post by HarmonicaGoldfish on 2009-10-12
output:

```
tracy@tracy-mini:~/Music$ ffmpeg -formats | grep ram
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
  E framecrc        framecrc testing format
Frame size, frame rate abbreviations:
tracy@tracy-mini:~/Music$ 
```

I haven't tried anything but mp3, I need mp3 for it to work on my phone I believe.

---

### Post by SuperSonic4 on 2009-10-12
It doesn't look like you can decode ram. Is the podcast in any other format?

edit: do you have a link to the podcast (or any [preferably small] ram file) so that I can test it

---

### Post by HarmonicaGoldfish on 2009-10-12
No, it is only offered in ram. The most recent podcasts are in mp3. I guess cbc archives their shows in ram. [http://www.cbc.ca/tapestry/archives/2009/052409.html]("http://www.cbc.ca/tapestry/archives/2009/052409.html")

How annoying. There must be a way to convert ram files, at least I would hope so!

---

### Post by SuperSonic4 on 2009-10-12
I've done it on mine. Did you install the medibuntu version of ffmpeg

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

For information I used ```
ffmpeg -i *****.ra -acodec libmp3lame *****.mp3
```

edit: haha, rammstein's new song title is censored xD. No doubt you get the point

---

### Post by HarmonicaGoldfish on 2009-10-12
I notice that in your code you have .ra not .ram. Is that a typo or are we talking about 2 different file extensions?

I didn't install ffmeg, it was already in place in my system. I am using karmic netbook remix beta.

---

### Post by SuperSonic4 on 2009-10-12
I believe they are two different ones but I couldn't find one for .ram

---

### Post by ron999 on 2009-10-12
Excuse me butting in.
@ HarmonicaGoldfish
I think that you've downloaded the wrong file. It shouldn't be a ram file, it needs to be a ra file.
I can download that podcast using mplayer with this command:-
```
mplayer -playlist http://www.cbc.ca/tapestry/media/2008/060808.ram -bandwidth 999999999999 -ao null -dumpstream -dumpfile podcast.ra
```
This gives you a file named 'podcast.ra'.
I can then convert it to mp3 using ffmpeg with this command:-
```
ffmpeg -i podcast.ra podcast.mp3
```
So for other podcasts in the series just change the date in the url   **..../2008/060808**.ram to a different date.

---

### Post by FakeOutdoorsman on 2009-10-12
> **SuperSonic4 said:**
> I've done it on mine. Did you install the medibuntu version of ffmpeg

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

For information I used ```
ffmpeg -i *****.ra -acodec libmp3lame *****.mp3
```

edit: haha, rammstein's new song title is censored xD. No doubt you get the point

Medibuntu only offers a FFmpeg package for Ubuntu Hardy Heron.  The original poster is using Ubuntu Karmic Koala, and needs to install the **libavcodec-extra-52** package to enable restricted encoders in FFmpeg.  Then simply:
```
ffmpeg -i input.ram output.mp3
```

---

### Post by HarmonicaGoldfish on 2009-10-12
Well, I installed the unstripped package and it seems to be working. Though it started about an hour ago and seems to have hung...

edit: I am going to stop this process and try the mplayer solution that was offered, over an hour for conversion is too long!

---

### Post by ron999 on 2009-10-12
> **HarmonicaGoldfish said:**
> 

edit: I am going to stop this process and try the mplayer solution that was offered, over an hour for conversion is too long!

Yeah, go for it.
The ra file that you download is 25.2MB and takes approx 10 minutes to convert to mp3.

---

### Post by HarmonicaGoldfish on 2009-10-12
> **ron999 said:**
> Yeah, go for it.
The ra file that you download is 25.2MB and takes approx 10 minutes to convert to mp3.

It seems to have worked! I've skimmed through the podcast and all 54 minutes of it seem to be there even though I received this message:
```

tracy@tracy-mini:~$ mplayer -playlist http://www.cbc.ca/tapestry/media/2008/060808.ram -bandwidth 999999999999 -ao null -dumpstream -dumpfile podcast.ra
Creating config file: /home/tracy/.mplayer/config
Resolving www.cbc.ca for AF_INET6...
Couldn't resolve name for AF_INET6: www.cbc.ca
Resolving www.cbc.ca for AF_INET...
Connecting to server www.cbc.ca[67.69.247.25]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://media.cbc.ca/cbc.ca/tapestry/media/2008/060808.rm.
Resolving media.cbc.ca for AF_INET6...
Couldn't resolve name for AF_INET6: media.cbc.ca
Resolving media.cbc.ca for AF_INET...
Connecting to server media.cbc.ca[159.33.4.223]: 554...
Cache size set to 320 KBytes
realrtsp: Stream EOF detected
Core dumped ;)

Exiting... (End of file)
tracy@tracy-mini:~$ ffmpeg -i podcast.ra podcast.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
Input #0, rm, from 'podcast.ra':
  Duration: 00:54:03.34, start: 0.000000, bitrate: 65 kb/s
    Stream #0.0: Audio: cook, 44100 Hz, mono, s16, 64 kb/s
Output #0, mp3, to 'podcast.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[libmp3lame @ 0x978a3b0]lame: output buffer too small (buffer index: 9404, free bytes: 388)
Audio encoding failed
tracy@tracy-mini:~$ 
```

Thanks for your help everyone :)

---

### Post by ron999 on 2009-10-12
.....................

---

### Post by HarmonicaGoldfish on 2009-10-12
> **FakeOutdoorsman said:**
> Medibuntu only offers a FFmpeg package for Ubuntu Hardy Heron.  The original poster is using Ubuntu Karmic Koala, and needs to install the **libavcodec-extra-52** package to enable restricted encoders in FFmpeg.  Then simply:
```
ffmpeg -i input.ram output.mp3
```

@Ron999 - Earlier I had installed the libavcodec-extra-52 package and tried that same code. It didn't work for me. 

Even though I received the audio failure message with your instructions, the mp3 works. It is now on my phone and I will be listening to it this evening as I clean up after dinner :)

Thanks again to everyone who has helped me with this. Whenever anyone asks me why I choose ubuntu my list of whys always starts with how helpful the community is. Here is another example of just that.

---

### Post by ron999 on 2009-10-12
> **HarmonicaGoldfish said:**
>  

Even though I received the audio failure message with your instructions, the mp3 works. 
Phew!:o

Glad it works ok.
:guitar:

---

### Post by Lorin Ricker on 2010-02-01
Thanks to all who contributed to this thread... solved my problem even before I got to ask: I needed a way to convert a whole dir-tree full of .wav files to .mp3.  Ffmpeg would work for the file-conversion, but it looks like I'd need to write bash-script to traverse the tree and work out the output filenames, e.g., foo.wav -> foo.mp3, bar.wav -> bar.mp3, etc.

SoundConverter does that all for me, with a GUI to-boot.  Seems to choke on a rather large dir-tree, but quickly doable sub-dir by sub-dir.  Also seems to have trouble with "overwrite existing output file...", so manual clean-up before a pass through was necessary.  Regardless, I got over 80 .wav's converted in under 15 minutes, even with a Synaptic app-install and then all the learning and fooling-around.

Many thanks, all!
  -- Lorin

---

### Post by FakeOutdoorsman on 2010-02-01
> **Lorin Ricker said:**
> Thanks to all who contributed to this thread... solved my problem even before I got to ask: I needed a way to convert a whole dir-tree full of .wav files to .mp3.  Ffmpeg would work for the file-conversion, but it looks like I'd need to write bash-script to traverse the tree and work out the output filenames, e.g., foo.wav -> foo.mp3, bar.wav -> bar.mp3, etc.

SoundConverter does that all for me, with a GUI to-boot.  Seems to choke on a rather large dir-tree, but quickly doable sub-dir by sub-dir.  Also seems to have trouble with "overwrite existing output file...", so manual clean-up before a pass through was necessary.  Regardless, I got over 80 .wav's converted in under 15 minutes, even with a Synaptic app-install and then all the learning and fooling-around.

Many thanks, all!
  -- Lorin

You can use the *find* command to make just about anything work in a batch fashion.  Here's a great guide with examples written by forum member andrew.46:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

---

### Post by Lorin Ricker on 2010-02-01
> **FakeOutdoorsman said:**
> You can use the *find* command to make just about anything work in a batch fashion.  Here's a great guide with examples written by forum member andrew.46:

[Linux Basics: A gentle introduction to 'find']("http://ubuntuforums.org/showthread.php?t=1128937")

Again, many thanks -- This "gentle intro" is very welcome, just what I've needed.  -- L

---

