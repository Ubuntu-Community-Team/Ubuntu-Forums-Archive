---
title: "Flash videos lag on fullscreen"
date: 2009-01-29
forum: Multimedia Software
---

### Post by tegnoto89 on 2009-01-29
I've been having problems watching flash videos fullscreen - the videos lag badly; it's like a half second in between frames.  Can anyone help me with this?  I did some searching but nobody seems to have solved it (at least that I could find).

Thanks!

---

### Post by tegnoto89 on 2009-02-01
3 day bump

---

### Post by andrew.46 on 2009-02-03
Hi,

Some flash videos might contain high quality h264 video which could account for your difficulty in playback full screen. Can you identify the contents of the file with ffmpeg perhaps? The command would be:

```
ffmpeg -i filename.flv
```

Andrew

---

### Post by Crafty Kisses on 2009-02-03
> **tegnoto89 said:**
> I've been having problems watching flash videos fullscreen - the videos lag badly; it's like a half second in between frames.  Can anyone help me with this?  I did some searching but nobody seems to have solved it (at least that I could find).

Thanks!

What are your system specs? Do you have desktop effects enabled?

---

### Post by GSI on 2009-02-03
I have same problem not in full screen but only in some sites

---

### Post by tegnoto89 on 2009-02-03
> What are your system specs? Do you have desktop effects enabled?



I'm running 2GB memory, 160GB hard drive.  What do I type to find out what my graphics card and processor are?

Also, yes I'm running desktop effects, but I've tried disabling them and the problem remains.

---

### Post by tegnoto89 on 2009-02-07
Anyone else?

---

### Post by travmon69 on 2009-02-07
in the terminal try
```
 glxgears
```
 to see how many FPS you are getting

---

### Post by tegnoto89 on 2009-02-07
> in the terminal try
Code:

 glxgears

to see how many FPS you are getting


Here's what I've got:

```
14739 frames in 5.0 seconds = 2947.693 FPS
16677 frames in 5.0 seconds = 3335.317 FPS
15543 frames in 5.0 seconds = 3108.586 FPS
13543 frames in 5.0 seconds = 2708.557 FPS
11950 frames in 5.0 seconds = 2389.850 FPS
16327 frames in 5.0 seconds = 3265.377 FPS
14203 frames in 5.0 seconds = 2840.503 FPS
15890 frames in 5.0 seconds = 3177.882 FPS
17080 frames in 5.0 seconds = 3415.957 FPS
17115 frames in 5.0 seconds = 3422.771 FPS
16940 frames in 5.0 seconds = 3387.985 FPS
16802 frames in 5.0 seconds = 3360.400 FPS
16714 frames in 5.0 seconds = 3342.268 FPS
7070 frames in 5.0 seconds = 1413.956 FPS
4900 frames in 5.0 seconds = 979.413 FPS
3205 frames in 5.0 seconds = 640.968 FPS
5324 frames in 5.0 seconds = 1064.795 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 153 requests (153 known processed) with 0 events remaining.


```

---

### Post by OutOfReach on 2009-02-07
-EDIT- I see you figured it out, nevermind.

---

### Post by travmon69 on 2009-02-07
you may need to drag the gears window aside to see the output

---

### Post by travmon69 on 2009-02-07
> **tegnoto89 said:**
> Here's what I've got:

```
14739 frames in 5.0 seconds = 2947.693 FPS
16677 frames in 5.0 seconds = 3335.317 FPS
15543 frames in 5.0 seconds = 3108.586 FPS
13543 frames in 5.0 seconds = 2708.557 FPS
11950 frames in 5.0 seconds = 2389.850 FPS
16327 frames in 5.0 seconds = 3265.377 FPS
14203 frames in 5.0 seconds = 2840.503 FPS
15890 frames in 5.0 seconds = 3177.882 FPS
17080 frames in 5.0 seconds = 3415.957 FPS
17115 frames in 5.0 seconds = 3422.771 FPS
16940 frames in 5.0 seconds = 3387.985 FPS
16802 frames in 5.0 seconds = 3360.400 FPS
16714 frames in 5.0 seconds = 3342.268 FPS
7070 frames in 5.0 seconds = 1413.956 FPS
4900 frames in 5.0 seconds = 979.413 FPS
3205 frames in 5.0 seconds = 640.968 FPS
5324 frames in 5.0 seconds = 1064.795 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 153 requests (153 known processed) with 0 events remaining.


```

wow that is good!  i only get like 500 fps.  i think it's a problem with flash cause every system i try to watch flash on (linux and windows) it lags,  even with youtube.

---

### Post by andrew.46 on 2009-02-07
Hi,

You have not been able to identify the audio and video elements of the flash container?

Andrew

---

### Post by tegnoto89 on 2009-02-07
> You have not been able to identify the audio and video elements of the flash container?



I'm not sure I understand what you mean by that...

---

### Post by andrew.46 on 2009-02-07
Hi,

Sorry to speak around the subject a little :-). Your flash video could contain one of a small number of video formats. I suspect that you may have one with quite a high quality h264 video and this might account for the difficulty in playback, a common problem with high quality h264 video.

This can be confirmed by analysing one of the flash files with, for example, FFmpeg:

```
ffmpeg -i myfile.flv
```

This will show the contents o the file and also reveal the bitrate of the video and either confirm or disprove my neat little theory :-).

Andrew

---

### Post by tegnoto89 on 2009-02-07
Okay, I put the command in, and this is what I get:


Command:

```
ffmpeg -i Out Cold 2 - The Induction of Jason and Kelley.flv
```

```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Out: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```

---

### Post by andrew.46 on 2009-02-07
Hi,

Hmmm.... either the file is broken or more likely you need to hide the spaces as follows:

```
ffmpeg -i 'Out Cold 2 - The Induction of Jason and Kelley.flv'
```

Andrew

---

### Post by tegnoto89 on 2009-02-07
Weird, I tried quoting the file name as your suggested, and it's giving me the same error for all the files I'm trying.  Maybe the program I use to download the vids (fast video download firefox extension) does something to them that keeps ffmpeg from reading them?

---

### Post by chrisolof on 2009-02-07
Same problem here - I'm on 8.10 64-bit - and in my opinion the 64-bit flash plugin is to blame.  My system sports a 9800GT with proprietary nvidia drivers and flash videos still get really laggy on full-screen.  I also get that fun gray-out problem where flash content just randomly turns off and the place where flash content should be is represented by a gray block.  It's really a shame that Adobe can't get their act together on that- it's been quite some time - at least the flash sound issues seem to be resolved now.

---

### Post by andrew.46 on 2009-02-07
Hi tegnoto89,

> **tegnoto89 said:**
> Weird, I tried quoting the file name as your suggested, and it's giving me the same error for all the files I'm trying.  Maybe the program I use to download the vids (fast video download firefox extension) does something to them that keeps ffmpeg from reading them?

I suspect that the files have been damaged in some fashion. Do you have an address for one of these files? This might be helpful to see if the file itself is damaged or there is another reason. And BTW what software are you using for playback?

Sorry this is becoming something of a saga :-).

Andrew

---

