---
title: "FFMPEG commands"
date: 2013-01-02
forum: Multimedia Software
---

### Post by Hari5g900 on 2013-01-02
Hi,
   I want to swap the audio of a video I have with another audio file with the help of FFmpeg. Will the length of the audio affect it? I am a beginner with FFmpeg and I need guidance.
Thank you

---

### Post by Hari5g900 on 2013-01-02
Is there anyway to record screen using FFmpeg capturing both the microphone audio and the system audio?

---

### Post by Hari5g900 on 2013-01-02
I would also like to know how to add audio to a video which has no audio with FFmpeg

---

### Post by evilsoup on 2013-01-02
```

ffmpeg -i input1.mp4 -i input2.mp4 -map 0:v -map 1:a -c copy output.mp4

```

will take the video only from the first input, and the audio only from the second input, and copy everything (so it won't re-encode). I'm using MP4 here because it's a fairly common format, this should work with most multimedia stuff. If the audio is shorter than the video, the video will continue without sound when it's played, and the opposite if the audio is longer.

There is a tutorial somewhere on this forum about how to record your screen etc with ffmpeg, but I can't remember what it's called exactly.

---

### Post by raja.genupula on 2013-01-02
well I have got a home link for you 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by FakeOutdoorsman on 2013-01-02
> **Hari5g900]I want to swap the audio of a video I have with another audio file with the help of FFmpeg. Will the length of the audio affect it?[/QUOTE]

Not necessarily. You can add the "-shortest" option to your command to make the output duration be the same as the shortest input duration.

[QUOTE=Hari5g900 said:**
> Is there anyway to record screen using FFmpeg capturing both the microphone audio and the system audio?

See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719). To capture both the mic and the system you can create two audio streams (one per input), or if your sound card supports "Stereo Mix / Wave Out Mix / Mono Mix / What U Hear" you may be able to use that as the input, or you can try to use PulseAudio as shown in the link. Unfortunately, "Stereo Mix" is less common these days apparently; possibly due to pressure from RIAA, but that is a rumor and I don't know if it is true.

Also see [Capturing audio with FFmpeg and ALSA](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSA).

---

### Post by Hari5g900 on 2013-01-05
I just need the script for adding an audio file with a video-only file with ffmpeg

---

### Post by evilsoup on 2013-01-05
> **evilsoup said:**
> ```

ffmpeg -i input1.mp4 -i input2.mp4 -map 0:v -map 1:a -c copy output.mp4

```will take the video only from the first input, and the audio only from the second input, and copy everything (so it won't re-encode). I'm using MP4 here because it's a fairly common format, this should work with most multimedia stuff. If the audio is shorter than the video, the video will continue without sound when it's played, and the opposite if the audio is longer.

This will work, just change 'input2.mp4' to 'input2.mp3' or whatever.

As FakeOutdoorsman wrote, you can use -shortest to end the output file when the shortest input stream ends, which may be helpful to you.

---

### Post by Hari5g900 on 2013-01-05
where should i add the -shortest?

---

### Post by Hari5g900 on 2013-01-05
I get this error:
```
ubuntu@ubuntu-linux:~/Desktop$ ffmpeg -i Input1.wmv -i Input2.mp3 -map 0:v -map 1:a -c copy output.mp4
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 18 2012 18:02:54, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Input1.wmv':
  Duration: 00:13:25.78, start: 3.100000, bitrate: 1212 kb/s
    Stream #0.0: Video: wmv2, yuv420p, 800x600, 25 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: wmav2, 44100 Hz, stereo, s16, 160 kb/s
Input #1, mp3, from 'Input2.mp3':
  Duration: 00:12:34.52, start: 0.000000, bitrate: 320 kb/s
    Stream #1.0: Audio: mp3, 44100 Hz, stereo, s16, 320 kb/s
ffmpeg: unrecognized option '-c'
```

---

### Post by evilsoup on 2013-01-05
You put -shortest anywhere between the last input file and output.mp4.

You're using a really old version of ffmpeg; there's been a syntax change recently. You'll have to use

```

ffmpeg -i Input1.wmv -i Input2.mp3 -map 0:0 -map 1:0 -vcodec copy -acodec copy -shortest output.mp4

``` 

I can't guarantee that -shortest will work with such an old version. You'd be much better off upgrading to a new version of ffmpeg; [here](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) is a good PPA. Or you can compile the very latest version by following the instructions in [this](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) guide.

---

### Post by Hari5g900 on 2013-01-06
-shortest worked. Thanks
I added the PPA.
What do I have to do now? Remove FFmpeg and reinstall it or upgrade via sudo apt-get upgrade?

---

### Post by evilsoup on 2013-01-06
```

sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get upgrade

```

Or you can use the Update Manager. Since you already have ffmpeg installed, you shouldn't need to install it again.

---

### Post by Hari5g900 on 2013-01-06
I did it.
But It only upgraded libmp3lame. It did not upgrade FFmpeg

---

