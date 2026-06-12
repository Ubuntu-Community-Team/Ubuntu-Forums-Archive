---
title: "ffmpeg problem: Unsupported codec for output stream #0.0"
date: 2010-08-19
forum: Multimedia Software
---

### Post by MadnessRed on 2010-08-19
I have a problem, when I try and convert a file to mp3, I am getting the following error:
> Unsupported codec for output stream #0.0 

```
anthony@Anthony-Acer:~$ ./.to_mp3.py '/home/anthony/Videos' 'Video'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from '/home/anthony/Videos/Video':
  Duration: 00:04:04.20, start: 0.000000, bitrate: 629 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 629 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
Output #0, mp3, to '/home/anthony/Videos/Video.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
```

And .to_mp3.py gives the commands
```
path = os.path.join(sys.argv[1], sys.argv[2])
os.system('ffmpeg -i "' + path + '" "' + path + '_converting.mp3"')
```

So the actual command being sent is:
```
ffmpeg -i "/home/anthony/Videos/Video" "/home/anthony/Videos/Video.mp3"
```m

I can play the original file in rhythm box, and I can play mp3 files in rhythm box.

Any help would be great. Thanks.

---

### Post by ron999 on 2010-08-19
Hi
Please try entering a command without the py script.
Something like this:-
```
ffmpeg -i /home/anthony/Videos/Video output.mp3
```
See if it still gives you an error.

---

### Post by MadnessRed on 2010-08-19
> **ron999 said:**
> Hi
Please try entering a command without the py script.
Something like this:-
```
ffmpeg -i /home/anthony/Videos/Video output.mp3
```
See if it still gives you an error.

Still the same:

```
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from '/home/anthony/Videos/Video':
  Duration: 00:03:34.48, start: 0.000000, bitrate: 810 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 810 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
Output #0, mp3, to 'output.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0

```

It's virtually a fresh install of Ubuntu if that helps.

---

### Post by ron999 on 2010-08-19
Which version of Ubuntu are you using?
Lucid Lynx?

---

### Post by MadnessRed on 2010-08-19
> **ron999 said:**
> Which version of Ubuntu are you using?
Lucid Lynx?

Yep, lucid.

---

### Post by ron999 on 2010-08-19
OK
Read the information here and choose option **C Medibuntu** [http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

Then try your command again.

---

### Post by MadnessRed on 2010-08-19
> **ron999 said:**
> OK
Read the information here and choose option **C Medibuntu** [http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

Then try your command again.

Perfect, thanks :)

I'm sure ffmpeg used to be able to convert to mp3 before though? Without needing a special version being installed.

---

