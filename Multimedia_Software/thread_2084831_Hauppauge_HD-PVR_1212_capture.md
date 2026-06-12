---
title: "Hauppauge HD-PVR 1212 capture"
date: 2012-11-16
forum: Multimedia Software
---

### Post by two4two on 2012-11-16
OK, I guess this has been covered somewhere already, but my question is short for those in the know (which I'm not one of).  I use the following command to capture from either SVHS tapes or from live TV:

ffmpeg -i /dev/videoN -vcodec copy -acodec ac3 -ab 448k ~/capture.mp4


I like ffmpeg better than cat because I can set acodec and ab.  But when the capture is commencing I can't view it on my computer.  

How can I also view on my computer whatever the ffmpeg is capturing?  

Thanks for letting me post one more HD-PVR and vid-cap thread.

---

### Post by dannyboy79 on 2013-01-03
couldn't you opena second terminal window and use a command like this?
```
mplayer ~/capture.mp4
```
there would obviously be a little lag but that should work. or is there someway to use all one command where it not only captures the output of /dev/videoX but also displays it using a pipe and exec somehow?

---

### Post by Bucky Ball on 2013-01-03
*Thread moved to **Multimedia & Video***

---

### Post by evilsoup on 2013-01-03
FFmpeg can have multiple outputs, and it can output to stdout; any player that can take input from stdin (vlc, totem, mplayer can all do this) can play that through a pipe. I've also updated the syntax to be in line with current correct ffmpeg usage (see [here](http://ubuntuforums.org/showthread.php?p=12419508) for more info):

```

ffmpeg -i /dev/videoN -c:v copy -c:a ac3 -b:a 448k ~/capture.mp4 \
-c:v copy -c:a ac3 -b:a 448k -f mp4 - | vlc -

```Dannyboy's solution will also probably work.

---

### Post by FakeOutdoorsman on 2013-01-03
Eventually a tee pseudo-muxer should make its way into ffmpeg which would be useful for this sort of thing since it can create several outputs from encoding just once.

---

### Post by two4two on 2013-01-08
> **evilsoup said:**
> FFmpeg can have multiple outputs, and it can output to stdout; any player that can take input from stdin (vlc, totem, mplayer can all do this) can play that through a pipe. I've also updated the syntax to be in line with current correct ffmpeg usage (see [here](http://ubuntuforums.org/showthread.php?p=12419508) for more info):

```

ffmpeg -i /dev/videoN -c:v copy -c:a ac3 -b:a 448k ~/capture.mp4 \
-c:v copy -c:a ac3 -b:a 448k -f mp4 - | vlc -

```Dannyboy's solution will also probably work.



I entered as you specified (using correct device#, output path/file name, of course) and get errors.  I'll post results later tonight.  Maybe someone can help with the problem.

---

### Post by dannyboy79 on 2013-01-08
i've successfully used 2 different terminal windows to show what is being captured from HD PVR. these are the following commands I use

```
cat /dev/video0 > /home/username/video/video.ts
```

```
vlc /home/username/video/video.ts
```

Then you just use ctrl-c in the terminal window that has the cat command to quit the recording.

---

### Post by two4two on 2013-01-08
> **dannyboy79 said:**
> i've successfully used 2 different terminal windows to show what is being captured from HD PVR. these are the following commands I use

```
cat /dev/video0 > /home/username/video/video.ts
```

```
vlc /home/username/video/video.ts
```

Then you just use ctrl-c in the terminal window that has the cat command to quit the recording.

Thank you Danny.  I've done this one and it works, but I don't like the quality that cat gives.  Also, I want to monitor it real-time on my computer monitor as it's being recorded.  I tried VLC, using the hd-pvr as the capture device, but it too gives a strange-looking image (with the same lines in it that cat gives).  If I knew better how to send ffmpeg output to 2 different outputs (my file, and stdout), and then pipe stdin into vlc, as evilsoup showed, I think that'd be what I'm looking for, but even when I translate his command into the old (my Natty) syntax it gives me an error.  I'll post that error later tonight.

---

### Post by two4two on 2013-01-08
PS:  Do you think setting ffmpeg's output to stdout by specifying - as the output file, and then use tee and use ffmpeg with stdin and my file as the output, and followed by the vlc command with stdin would work?

---

### Post by evilsoup on 2013-01-08
I would *strongly* recommend updating to a newer version of ffmpeg. Use [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg).

---

### Post by dannyboy79 on 2013-01-08
> **two4two said:**
> Thank you Danny.  I've done this one and it works, but I don't like the quality that cat gives.  Also, I want to monitor it real-time on my computer monitor as it's being recorded.  I tried VLC, using the hd-pvr as the capture device, but it too gives a strange-looking image (with the same lines in it that cat gives).  If I knew better how to send ffmpeg output to 2 different outputs (my file, and stdout), and then pipe stdin into vlc, as evilsoup showed, I think that'd be what I'm looking for, but even when I translate his command into the old (my Natty) syntax it gives me an error.  I'll post that error later tonight.
you're getting lines in your recordings? sounds like you have either a capture issue or a playback problem. I don't have any lines when I capture with cat or vlc using hd pvr as a capture device. are you sure your computer is up to playing back 720p h264 content?

---

### Post by two4two on 2013-01-08
> **dannyboy79 said:**
> you're getting lines in your recordings? sounds like you have either a capture issue or a playback problem. I don't have any lines when I capture with cat or vlc using hd pvr as a capture device. are you sure your computer is up to playing back 720p h264 content?

My computer should be up to the task.  AMD 1100T 6-core 3.3G processor, on an ASUS/AMD reference graphics Mobo with HDMI out, 16G DDR3, etc.  Less than a year old, fairly modern and quick.  I am capturing 1080p, 60fps h264/ac3 mp4 from the hd-pvr.  This gives great quality when captured with ffmpeg.  I'd just like to monitor it while I record it.  

I'm going to try:

"ffmpeg -i /dev/video0 -vcodec copy -acodec ac3 -ab 448k ~/capture.mp4 -vcodec copy -acodec ac3 -ab 448k –f mp4 - | vlc -"


tonight.  I'll post the results.

---

### Post by dannyboy79 on 2013-01-08
the hd-pvr can't capture 1080p, max is 1080i. i've also read some articles that states 720p is actually better then 1080i because it's progressive versus interlaced but that's your choice of what you want to capture. it definitely can't capture 1080p though

---

### Post by two4two on 2013-01-08
I tried the pipe and VLC:

dad@Dad-Stubuntu:~$ ffmpeg -i /dev/video0 -vcodec copy -acodec ac3 -ab 448k ~/capture.mp4 -vcodec copy -acodec ac3 -ab 448k -f mp4 - | vlc -
VLC media player 1.1.9 The Luggage (revision exported)
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x2597120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1357693810)
Warning: call to rand()
Warning: call to srand(1357693810)
Warning: call to rand()
Warning: call to srand(1357693810)
Warning: call to rand()
Warning: call to srand(1357693810)
Warning: call to rand()
Warning: call to srand(1357693810)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:15075): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[mpegts @ 0x1394670]max_analyze_duration reached
[mpegts @ 0x1394670]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 59.94 (60000/1001)
Input #0, mpegts, from '/dev/video0':
  Duration: N/A, start: 0.387044, bitrate: 384 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 59.96 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s
[mp4 @ 0x139c230]muxer does not support non seekable output
Output #0, mp4, to '/home/dad/capture.mp4':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: libx264, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 60k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s
Output #1, mp4, to 'pipe:':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #1.0: Video: libx264, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 90k tbn, 29.97 tbc
    Stream #1.1: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.0 -> #1.0
  Stream #0.1 -> #1.1
Could not write header for output file #1 (incorrect codec parameters ?)
[0x28a0a70] main stream error: cannot pre fill buffer





So, any suggestions (besides upgrading my ffmpeg, I'll do that next week, maybe)?

---

### Post by two4two on 2013-01-08
> **dannyboy79 said:**
> the hd-pvr can't capture 1080p, max is 1080i. i've also read some articles that states 720p is actually better then 1080i because it's progressive versus interlaced but that's your choice of what you want to capture. it definitely can't capture 1080p though

Yes, the specs say 1080i.  But it captures 60 fps, in both 480p and 1080i.  Better remember the 1080i thing when building a Blu-ray disc.  If not, you'll get a surprise.

---

### Post by dannyboy79 on 2013-01-09
it appears like you're only capturing 720x480 per vlc. I am not sure why you're having such difficulty. Just last night I was using the cat command and the separate vlc command to monitor in real time what I was capturing from my xbox 360. My xbox 360 is set to output 1280x720p@59.94fps.

---

### Post by two4two on 2013-01-09
> **dannyboy79 said:**
> it appears like you're only capturing 720x480 per vlc. I am not sure why you're having such difficulty. Just last night I was using the cat command and the separate vlc command to monitor in real time what I was capturing from my xbox 360. My xbox 360 is set to output 1280x720p@59.94fps.


Yes in this instance the input was 720 X 480.  I have done the 2 seperate windows now and that works, but the mplayer (or VLC) window is a bit behind the recorder window.

I found that the problem with the bad quality and the lines seems to be an issue with the player.  I'll post a snapshot to show you what I mean by "lines".  mplayer command line and Totem movie player do a better job than SMplayer, Gnome Mplayer or VLC, and don't have the lines.  Also, if I capture in TS container, playback in those two looks good. I didn't try xine for any of this yet.

I opened the hd-pvr in VLC as a PVR capture device and recorded.  Playing it back in VLC has the problems with the lines, but I didn't try to play that back with the two good players to see if the lines are there.  If not, then VLC for record is my solution.

---

### Post by two4two on 2013-02-13
Addendum:  the problem with the lines?  I think I know what that's all about:  This HD-PVR records supposedly at 60FPS.  When you look at the properties of the file it says 60FPS.  But it's 1080i, not 1080p.  So the recording software thinks it's 1080p and it's recording fields as frames?  When I look at a frame grab what I see looks like every other line of the frame is missing -- the very definition of a field, right?  :-s

---

### Post by two4two on 2014-01-24
I have resolved to use VLC to view when capturing.

---

