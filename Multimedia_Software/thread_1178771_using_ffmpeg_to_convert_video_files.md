---
title: "using ffmpeg to convert video files?"
date: 2009-06-04
forum: Multimedia Software
---

### Post by cptrohn on 2009-06-04
OK... here is my situation.. I have some video's on that ripped using thoggen that I would like to convert to Mpeg4 so that I can encode the video to play on my cowon D2... I've tried all the converters in add/remove, but just have a few questions if somebody here uses ffmpeg to convert video files and knows more about it than I do.. (which wouldn't take much at all;) )

Do I have to convert the audio etc via command line with ffmpeg as well or is it a one shot deal where everything converts with it?

I usually use Avidemux (GTK+) to convert video for this, but it doesn't seem to be able to open the .ovg files to be able to convert them.... I've tried everything I can think of to convert them Handbrake etc.. just won't do it.


Any ideas out there?

---

### Post by cptrohn on 2009-06-04
OR.... is there a way that I could add the .ogv codec to Avidemux (GTK+) so that I could just use it to convert the files?


This is the error I get with Avidemux(GTK) when I try to open the file to convert..
```
Attempt to open /home/user/Videos/filename.ogv Failed
```

Then of course I click on ok and get another ```
could not open the file
``` error...

---

### Post by SuperSonic4 on 2009-06-04
A basic code would be something like

```
ffmpeg -i /home/user/Videos/filename.ogv -s [COLOR="Red"]640x480[/COLOR] -vcodec copy -acodec copy -ab 128 -ac 2 output.mpeg
```

[COLOR="Red"]Insert whichever size your screen is here[/COLOR]

---

### Post by cptrohn on 2009-06-04
> **SuperSonic4 said:**
> A basic code would be something like

```
ffmpeg -i /home/user/Videos/filename.ogv -s [COLOR="Red"]640x480[/COLOR] -vcodec copy -acodec copy -ab 128 -ac 2 output.mpeg
```

[COLOR="Red"]Insert whichever size your screen is here[/COLOR]

OK thank you!  Thats along the lines of what I though it might be from info that I found online...


So I don't need to do anything to the audio then?

---

### Post by SuperSonic4 on 2009-06-04
Audio is included in there

-acodec copy means copy the audio codec
-ab 128 means make the bitrate 128kbps (that can be changed)
-ac 2 means two channel sound

The ffmpeg man page is a good place to look too

---

### Post by cptrohn on 2009-06-04
> **SuperSonic4 said:**
> Audio is included in there

-acodec copy means copy the audio codec
-ab 128 means make the bitrate 128kbps (that can be changed)
-ac 2 means two channel sound

The ffmpeg man page is a good place to look too

Awesome.. Thank you very much for the help!  Printing this page out right now to keep it handy for future reference.

---

### Post by SuperSonic4 on 2009-06-04
does that work ok? Usually I find it best to convert and test file by file xD. For some reason only libfaac works with my ffmpeg

---

### Post by cptrohn on 2009-06-04
> **SuperSonic4 said:**
> does that work ok? Usually I find it best to convert and test file by file xD. For some reason only libfaac works with my ffmpeg

It seems to be working ok.... It's still encoding the file (it's kind of a big one)  So I will post back when it's done.

---

### Post by cptrohn on 2009-06-04
No luck....


When I tried to open the converted file with VLC it just didn't do anything and when I tried to open with Movie Player I get this error..
```
GstMPEG AudioParse: No valid frames found before end of stream
```

---

### Post by andrew.46 on 2009-06-04
Hi cptrohn,

> **cptrohn said:**
> No luck....

Could you identify the file you are trying to convert as follows:

```
ffmpeg -i myfile.ogv
```

and post the full output here? This should allow an exact commandline for you.

And just to get ahead of myself a little here you should ensure that your copy of FFmpeg is able to deal with most video and audio formats:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Andrew

---

### Post by cptrohn on 2009-06-04
> **andrew.46 said:**
> Hi cptrohn,



Could you identify the file you are trying to convert as follows:

```
ffmpeg -i myfile.ogv
```

and post the full output here? This should allow an exact commandline for you.

And just to get ahead of myself a little here you should ensure that your copy of FFmpeg is able to deal with most video and audio formats:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Andrew

user@User:~$ ffmpeg -i /home/cptrohn/smoking_aces-01.ogv
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
[theora @ 0x8554e00]7 bits left in packet 82
Input #0, ogg, from '/home/cptrohn/smoking_aces-01.ogv':
  Duration: 01:48:55.76, start: 0.000000, bitrate: 890 kb/s
    Stream #0.0: Video: theora, yuv420p, 480x320, PAR 8:9 DAR 4:3, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: vorbis, 44100 Hz, stereo, s16, 128 kb/s
At least one output file must be specified


this is what comes up..

---

### Post by andrew.46 on 2009-06-05
Hi cptrohn,

> **cptrohn said:**
> 
Input #0, ogg, from '/home/cptrohn/smoking_aces-01.ogv':
Duration: 01:48:55.76, start: 0.000000, bitrate: 890 kb/s
Stream #0.0: Video: theora, yuv420p, 480x320, PAR 8:9 DAR 4:3, 29.97 tbr, 29.97 tbn, 29.97 tbc
Stream #0.1: Audio: vorbis, 44100 Hz, stereo, s16, 128 kb/s

Well if you like you could try an convert this directly into a format that will keep the Cowon D2 happy. I do not own one of these devices but a quick look on the internet suggests it is a little limited for video playback and you might be better to opt for mpeg4 video + mp3 sound in an avi container, not the most modern choices I will admit.

So a *start* might be:

```
ffmpeg -i $HOME/smoking_aces-01.ogv -vcodec mpeg4 -vtag XVID -sameq \
          -acodec libmp3lame -ab 128k output.avi
```
 
This would be a start only and I would suggest a few embellishments i I actually had one of these devices to test. You will need to visit the FakeOutdoorsman's page to ensure you have mp3 encoding support for your copy of FFmpeg.

Hope this provides you with a start?

Andrew

---

### Post by cptrohn on 2009-06-05
Thanks andrew,  I'll keep trying until I find something that works.. I know with avidemux(GTK+)  I have no trouble at all converting .flv to video that will work in the D2... these .ogv's are just giving me alot of trouble is all for some reason...


But I love linux because if there is a will then there is a way!

---

### Post by FakeOutdoorsman on 2009-06-05
> **SuperSonic4 said:**
> A basic code would be something like

```
ffmpeg -i /home/user/Videos/filename.ogv -s [COLOR="Red"]640x480[/COLOR] -vcodec copy -acodec copy -ab 128 -ac 2 output.mpeg
```

[COLOR="Red"]Insert whichever size your screen is here[/COLOR]

This is an invalid command.  With *-vcodec copy* and *-acodec copy*, you're just copying the corresponding audio or video stream to another file.  Almost like cutting and pasting text from one file to another.  Adding additional options that change the stream will be ignored when using "copy" (at least it ignores them with recent FFmpeg revisions).  Also, ignoring the fact that *-ab* and *-acodec copy* are incompatible, the *-ab* option in this example is wrong because it is missing the "k": -ab 128k.

What this example command ends up creating is Theora video and Vorbis audio in a MPEG container, which is probably not standard.

---

### Post by cptrohn on 2009-06-05
> **FakeOutdoorsman said:**
> This is an invalid command.  With *-vcodec copy* and *-acodec copy*, you're just copying the corresponding audio or video stream to another file.  Almost like cutting and pasting text from one file to another.  Adding additional options that change the stream will be ignored when using "copy" (at least it ignores them with recent FFmpeg revisions).  Also, ignoring the fact that *-ab* and *-acodec copy* are incompatible, the *-ab* option in this example is wrong because it is missing the "k": -ab 128k.

What this example command ends up creating is Theora video and Vorbis audio in a MPEG container, which is probably not standard.

Yes, that is the problem I was having with using thoggen for the ripper... avidemux(GTK+) doesn't support theora at this time from what I was told in their forum... so my solution was to rip the video using DVD Encoder OGM Rip (which puts it in Mpeg4) and then using avidemux (GTK+) to properly resize the video and convert it for use in the cowon D2.....  Seems to be working ok... Although I still want to learn more about ffmpeg and mencoder though... as I hear that they are the best as far as speed and quality goes.

---

### Post by andrew.46 on 2009-06-05
Hi cptrohn,

> **cptrohn said:**
> Yes, that is the problem I was having with using thoggen for the ripper... avidemux(GTK+) doesn't support theora at this time from what I was told in their forum... so my solution was to rip the video using DVD Encoder OGM Rip (which puts it in Mpeg4) and then using avidemux (GTK+) to properly resize the video and convert it for use in the cowon D2.....  Seems to be working ok... Although I still want to learn more about ffmpeg and mencoder though... as I hear that they are the best as far as speed and quality goes. 

Well as long as you are happy and the results are satisfactory sounds like you have the beat solution at the moment. I would definitely encourage an interest in FFmpeg though as the Ubuntu Forums is singularly blessed in the guide that FakeOutdoorsman has put together:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

has earned the official nod from FFmpeg support, I attach a screenshot. But it is also the *best* software available for the job and it generously rewards time spent learning how to effectively use it.

All the best,

Andrew

---

