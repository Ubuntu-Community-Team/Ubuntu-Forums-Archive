---
title: "FFmpeg and x11grab?"
date: 2009-02-06
forum: Multimedia Software
---

### Post by andrew.46 on 2009-02-06
Hi,

Has anyone managed to grab there screen display using FFmpeg and x11grab? I have ransacked the man pages and html docs and the best I have managed is a string of quite varied error messages :(.

I am using the current svn FFmpeg.

Andrew

---

### Post by andrew.46 on 2009-02-18
Well I have made a little headway but the encoding parameters need a little work. The following grabs the entire screen for 30 seconds and encodes to x264:

```
ffmpeg -y -t 30 -f x11grab -qscale 2 -r 15 -s 1024x768 -i :0.0 \
-s 800x600 -vcodec libx264 -vpre hq -crf 22 -threads 0 x11grab.mp4
```

Quality is a little horrible though. Can anybody expand on this a little?

Andrew

---

### Post by FakeOutdoorsman on 2009-02-18
I'm not very familiar with x11grab, although for quite some time I've been thinking it would make a good FFmpeg guide.  Does it look better if you cut out the resizing of the output?  What about using a lossless type of codec: ffv1, huffyuv, ffvhuff; vpre lossless_slow, lossless_medium, lossless_fast, lossless_ultrafast?  I'm just guessing here.

---

### Post by andrew.46 on 2009-02-19
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> I'm not very familiar with x11grab, although for quite some time I've been thinking it would make a good FFmpeg guide.  Does it look better if you cut out the resizing of the output?  What about using a lossless type of codec: ffv1, huffyuv, ffvhuff; vpre lossless_slow, lossless_medium, lossless_fast, lossless_ultrafast?  I'm just guessing here.

I suspect the problem seemed to be that I was a little ambitious trying to grab a whole desktop and then play back a big h264 clip :-). I cut down the size and fiddled the coordinates a little and I have achieved a more acceptable result:

```
ffmpeg -y -t 5 -f x11grab -r 12 -s 800x600 -i :0.0+75,30 \
-vcodec libx264 -vpre hq -crf 22 -threads 0 $HOME/Desktop/x11grab.mp4
```

I look forward to seeing some FFmpeg guides in this format from you and I am sure with your skill the video will look better than my crude effort :-).

Andrew

---

### Post by Gen2ly on 2009-06-27
Not bad, seems to do better than recordmydesktop as far as cpu intensity.  Still like to see a screencast program that can be moved, follow the mouse... on Linux though.

---

### Post by bgiannes on 2009-07-08
i'm trying to use x11grab but just get this...


> FFmpeg version SVN-r19369, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  7 2009 20:59:55, gcc: 4.3.3
Unknown input or output format: x11grab


---

### Post by andrew.46 on 2009-07-08
Hi bgiannes,

> **bgiannes said:**
> i'm trying to use x11grab but just get this...

```
Unknown input or output format: x11grab 
```


Could you post the full terminal output including the actual command that you are using? Could be that your syntax is not quite right.

All the best,

Andrew

---

### Post by mc4man on 2009-07-08
removed - should read more carefully

---

### Post by bgiannes on 2009-07-08
1) i just used the command from your post

ffmpeg -y -t 30 -f x11grab -qscale 2 -r 15 -s 1024x768 -i :0.0 \
-s 800x600 -vcodec libx264 -vpre hq -crf 22 -threads 0 x11grab.mp4
i've tryed change things around a bit but same result

in fact i have two ubuntu installs 8.10 and 9.04 that give me the same result

2) ffmpeg is built with x11grab enabled.

what i'm trying to do here:-
i'd like to use ffmpeg to capture the screen and the sound output.  i know about recordmydesktop but i get sure bad sound, besides i love ffmpeg!

---

### Post by bgiannes on 2009-07-08
once x11grab is working i hope to use:

ffmpeg -f oss -i /dev/dsp -f x11grab -s cif -i :0.0 /tmp/out.mpg




update

[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/59849](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/59849)

?

---

### Post by andrew.46 on 2009-07-08
Hi bgiannes,

> **bgiannes said:**
> 1) i just used the command from your post

```

ffmpeg -y -t 30 -f x11grab -qscale 2 -r 15 -s 1024x768 -i :0.0 \
-s 800x600 -vcodec libx264 -vpre hq -crf 22 -threads 0 x11grab.mp4
```
i've tryed change things around a bit but same result

I hope that I have not introduced confusion *again* by using the '\' character to produce a line break :-). The full command is of course:

```

ffmpeg -y -t 30 -f x11grab -qscale 2 -r 15 -s 1024x768 -i :0.0 -s 800x600 -vcodec libx264 -vpre hq -crf 22 -threads 0 x11grab.mp4

```

all on one line. I don't believe you actually need to place *-qscale 2* for the input file as it uses raw video. Can I suggest another thread that went way beyond my own meagre skills with x11grab as Nixie Pixel develops a much more sophisticated commandline:

gtk-recordmydesktop + compiz cube effects = severe tearing
[http://ubuntuforums.org/showthread.php?t=1179861](http://ubuntuforums.org/showthread.php?t=1179861)

Towards the end of this thread Nixie demonstrates a quite advanced syntax that works quite well. As regards including sound I have consistently failed to add this to the screen capture. Still waiting for the Fakeoutdoorsman to sort it all out and write a guide :-).

Andrew

---

### Post by mc4man on 2009-07-08
> by using the '\' character to produce a line break

Actually the \ seems to always work fine, the exception being in that mplayer command (for whatever reason, maybe because it followed a valid command ...?

---

### Post by bgiannes on 2009-07-09
i had read that thread, but as i can't get x11grab working i havn't really been trying to jazz up the syntax

ffmpeg -y -t 60 -r 25 -s 1920x1200 -f x11grab -i :0.0 out.avi

should work out of the box.


ps recordmydesktop w/ sound does work, but i need to reset the sound source each time i run it.  The problem is that the volume is v low :(

i can convert the ovg file and turn up the vol but the qulity is just pain bad.


i'm sure i can get audio... you guys try somthing like this... (with the "capture" sound selected & un-muted and at max vol in the mixer gui)

arecord -D default -t raw -c 1 -f S16_LE -r 48000 - | ffmpeg -f s16le -ab 128k -ar 48000 -i - -acodec libmp3lame -vn soundtestcapture.avi

then x11 w/ this
arecord -D default -t raw -c 1 -f S16_LE -r 48000 - | ffmpeg -f s16le -ab 128k -ar 48000 -ac 1 -i - -acodec libmp3lame -t 5 -f x11grab -r 25 -s 800x600 -i :0.0 -vcodec libvid capture.avi

ps
i rebuilt ffmpeg but x11grab is still broken, i just saw that there is a nvidia driver update, i'm going to try it tonight, but other capture programs have no problems with x11.  Maybe i'm have a build error with X11grab?

---

### Post by andrew.46 on 2009-07-09
Hi bgiannes,

> **bgiannes said:**
> 

```
ffmpeg -y -t 60 -r 25 -s 1920x1200 -f x11grab -i :0.0 out.avi
```

should work out of the box.

Indeed it should and it certainly *does *on my own system. Are you building FFmpeg from svn? Best way to do this is From Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This guide now incorporates the necessary options for x11grab.

Andrew

---

### Post by bgiannes on 2009-07-09
> **andrew.46 said:**
> Hi bgiannes,



Indeed it should and it certainly *does *on my own system. Are you building FFmpeg from svn? Best way to do this is From Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This guide now incorporates the necessary options for x11grab.

Andrew


i do my builds from there, i had to do a 

sudo aptitude install libice-dev libsm-dev libx11-dev libxext-dev libxi-dev libxmu-dev libxmuu-dev libxpm-dev libxrandr-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev x-dev zlib1g-dev

and then the build and i'm good, now for the syntax....

---

### Post by bgiannes on 2009-07-09
>  ffmpeg -s 1920x1080 -r 25 -f x11grab -i :0.0 -f oss -i /dev/dsp out.avi


works but the sound volume is low a v bad quality, the fram rate is v low as well?

---

### Post by andrew.46 on 2009-07-10
Hi bgiannes,

> **bgiannes said:**
> works but the sound volume is low a v bad quality, the fram rate is v low as well?

I am a little jealous as you have succeeded where I have failed :-). When you use x11grab the default *input* streams will be:

```

Stream #0.0: Video: rawvideo, bgra, 800x600, 384000 kb/s, 25 tbr, 1000k tbn, 25 tbc
Stream #1.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s

```

but the trick is to manipulate the *output*. When you simply specify .avi you will be given the FFmpeg *defaults* of low quality mpeg4 video and low quality mp2 sound, and the results are a little disappointing as you have seen. So the question has always been what are *the best settings* for the output sound and video. Video has been discussed in great depth in Nixie's thread for sound I guess you could try a reasonable mp3 sound to start with:

```
-acodec libmp3lame -ab 128k 
```

and that would at least provide a start although you limit yourself a little with the avi container, possibilities are greater with .mp4 or .mkv.

All the best,

Andrew

Andrew

---

### Post by produnis on 2009-11-27
> **bgiannes said:**
> 
i'm sure i can get audio... you guys try somthing like this... (with the "capture" sound selected & un-muted and at max vol in the mixer gui)

arecord -D default -t raw -c 1 -f S16_LE -r 48000 - | ffmpeg -f s16le -ab 128k -ar 48000 -i - -acodec libmp3lame -vn soundtestcapture.avi

then x11 w/ this
arecord -D default -t raw -c 1 -f S16_LE -r 48000 - | ffmpeg -f s16le -ab 128k -ar 48000 -ac 1 -i - -acodec libmp3lame -t 5 -f x11grab -r 25 -s 800x600 -i :0.0 -vcodec libvid capture.avi

If I type in:
```
ffmpeg -f alsa -i plughw:0 -f x11grab -s 1440x900 -r 24 -b 100k -bf 2 -g 300 -i :0.0 -ar 22050 -ab 128k -acodec libmp3lame -vcodec libxvid -aspect 1.6 -sameq MyScreencast.avi 

```
...it records my Screen and captures sound via built-in microphone.
Possibly, you need to change the screen size (mine is 1440x900) and the alsa device (for me, plughw:0 is good) 


To stop recording,  just hit "q".

---

### Post by Nixie Pixel on 2009-12-05
> **andrew.46 said:**
> Towards the end of this thread Nixie demonstrates a quite advanced syntax that works quite well. As regards including sound I have consistently failed to add this to the screen capture. Still waiting for the Fakeoutdoorsman to sort it all out and write a guide :-).

Andrew
Hah, I never saw this. Thank you for your kind words, but I just pasted together stuff from the suggestions of #ffmpeg members, especially Dark Shikari, based on your original command. You're the expert here! :)

Trust me, I don't have the knowledge to come up with "advanced syntax" on my own!  :D

---

### Post by n3had on 2010-01-20
> **produnis said:**
> If I type in:
```
ffmpeg -f alsa -i plughw:0 -f x11grab -s 1440x900 -r 24 -b 100k -bf 2 -g 300 -i :0.0 -ar 22050 -ab 128k -acodec libmp3lame -vcodec libxvid -aspect 1.6 -sameq MyScreencast.avi 

```
...it records my Screen and captures sound via built-in microphone.
Possibly, you need to change the screen size (mine is 1440x900) and the alsa device (for me, plughw:0 is good) 


To stop recording,  just hit "q".

```
ffmpeg -f alsa -i plughw:0 -f x11grab -s 1920x1080 -r 24 -b 100k -bf 2 -g 300 -i :0.0 -ar 22050 -ab 128k -acodec libmp3lame -vcodec libxvid -aspect 1.77777778 -sameq MyScreencast.avi

```

using the above command gives me very low fps around 5 i guess.

Using the opensource Ati drivers for HD4200

---

### Post by kung fu buntu on 2010-02-01
> **n3had said:**
> ```
ffmpeg -f alsa -i plughw:0 -f x11grab -s 1920x1080 -r 24 -b 100k -bf 2 -g 300 -i :0.0 -ar 22050 -ab 128k -acodec libmp3lame -vcodec libxvid -aspect 1.77777778 -sameq MyScreencast.avi

```

using the above command gives me very low fps around 5 i guess.

Using the opensource Ati drivers for HD4200

Not working for me and this is getting me insane!!!

First of all, I had to adapt that command since it simply didn't work.
ffmpeg didn't knew what "alsa" was :s
> Unknown input or output format: alsa

I'm using ffmpeg SVN-r19468 built on Jul 20 2009 20:26:33, gcc: 4.3.3

I tried the following but only got a black screen and no sound:
> ffmpeg -f oss -i /dev/audio  -f x11grab -s 1280x1024 -r 24 -b 100k -bf 2 -g 300 -i :0.0 -ar 22050 -ab 128k -acodec libmp3lame -vcodec libxvid -aspect 1.6 -sameq MyScreencast.avi

Note that I'm trying to capture output audio.
That is, I want to open a video file and capture what is played to the speakers.
Ideally I would like to record both output and input audio streams.

I have nVidia proprietary drivers.

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 33:        : timer

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3ff8000 irq 22


Any ideas?


gnu/linux makes me :'(

---

### Post by VertexPusher on 2010-02-02
> **kung fu buntu said:**
> First of all, I had to adapt that command since it simply didn't work.
ffmpeg didn't knew what "alsa" was :s
> Unknown input or output format: alsa
You need an ffmpeg binary that was compiled with ALSA support enabled. I don't know where you got yours, but Ubuntu's version of libavdevice depends on libasound so I guess that would work. Unfortunately I can't test it right now.

> Note that I'm trying to capture output audio.
That is, I want to open a video file and capture what is played to the speakers.
Ideally I would like to record both output and input audio streams.
To make this work, you need either a sound card with audio loopback in hardware (most HDA cards don't have that feature) or the ALSA loopback driver (snd-aloop).

The loopback driver basically adds another sound card to your computer which does nothing except loop all output back as input. If you select this as the default sound card, you can route audio from all applications into ffmpeg or any other recording software.

---

### Post by kung fu buntu on 2010-02-07
> **VertexPusher said:**
> You need an ffmpeg binary that was compiled with ALSA support enabled. I don't know where you got yours, but Ubuntu's version of libavdevice depends on libasound so I guess that would work. Unfortunately I can't test it right now.
I found out what I was doing wrong and I can now record video.
But I still don't get any sound recording from alsa.

```
ffmpeg -f x11grab -s 1280x1024 -r 30 -b 100k -bf 2 -g 300 -i $DISPLAY.0 -aspect 1280:1024 -sameq      -ac 2 -ar 22050 -ab 128k     -acodec libmp3lame -vcodec libxvid        MyScreencast.avi
```

When I use
```
ffmpeg -f alsa -i plughw:0 -f x11grab ...
```I get the error:
plughw:0: no such file or directory
But I also found out that I can use **-f oss -i /dev/dsp1** to capture sound from my mic (although I have ugly clicks at every second with my usb webcam mic).
This still doesn't solve my sound problem (of recording both input and output sound streams) because I also use headphones (and no, I can't take them off -- besides the quality wouldn't be the same).

I'm using debian with debian-multimedia packages, this is my ffmpeg:> FFmpeg version SVN-r21450, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Jan 26 2010 14:51:49 with gcc 4.4.3
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --enable-version3 --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
Could you paste yours?


> **VertexPusher said:**
> To make this work, you need either a sound card with audio loopback in hardware (most HDA cards don't have that feature) or the ALSA loopback driver (snd-aloop).

The loopback driver basically adds another sound card to your computer which does nothing except loop all output back as input. If you select this as the default sound card, you can route audio from all applications into ffmpeg or any other recording software.*ahem* and how could I do this?

Would it be possible (and easy, or at least explained in a howto) to capture the (1) video, (2) audio output, and (3) audio input to different files. And then mix them all? This way I could choose 1 audio track or both by mixing them together.

---

### Post by mocha on 2010-03-05
I haven't read all the posts here, but if all you guys want to do is capture sounds from within the computer (like from webpages or media players) when using ffmpeg x11grab, after you execute ffmpeg just go to the pulseaudio volume control, select the recording tab and you should see ffmpeg there.  Then just move it's stream to the monitor of internal audio... or whatever it's called on your system.

---

### Post by mocha on 2010-03-06
I've been playing with x11grab thanks to this thread and [http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026").  It is by far the most superior screen grabbing method.  The only limitation I've seen is that it only "detects" (for lack of better terms) the input audio as mono.

Stream #1.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s

It's simple enough to use the Pulseaudio GUI tools to route whatever audio you want to record, however it seems to make no difference to x11grab how many channels the input has.  Even specifying -ac 2 only give you an output file with 2 channels, but the input still only had 1 channels.  Anyone know a way to force x11grab to have 2 input channels?

---

### Post by Peter Gaivoronski on 2010-03-27
> **kung fu buntu said:**
> I found out what I was doing wrong and I can now record video.
But I still don't get any sound recording from alsa.


Please run ```
sudo aptitude install libasound2-dev
``` and then recompile your ffmpeg to enable ALSA support.

---

### Post by mocha on 2010-03-28
I figured out how to get ffmpeg to see dual channel audio on the input side.  The proper order is:

```
ffmpeg **-f alsa -ac 2 -i pulse -acodec pcm_s16le** -f x11grab -r 30 -s 1280x1024 -i :0.0 -aspect 4:3 -vcodec libx264 -vpre lossless_ultrafast -threads 0 SCREENCAST.mkv
```

The method above allows ffmpeg to "see" 2 audio channels on the incoming side, rather than just 1 channel.  You can also specify an audio bitrate after the "-ac 2" part, if you don't it just defaults to 64 kbps.

These techniques are useful for doing audio/video captures from webpages (for example), not necessarily for pure "screen-casting" uses.

---

