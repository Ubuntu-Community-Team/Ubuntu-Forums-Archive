---
title: "Error Converting video's audio from acc to mp3"
date: 2008-12-07
forum: Multimedia Software
---

### Post by enriqueaf on 2008-12-07
Hello!!

I am having a problem converting a video's audio from ac3 to mp3. I have installed ffmpeg from the mediubuntu.com testing repositories. I have been using the follow code:

```
$ ffmpeg -i '/home/enrique/Escritorio/El gran Lebowski.avi' -ab 448K -acodec libmp3lame -y ElGranLewski.avi

```

And this is the output is:
```
FFmpeg version SVN-r13582, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-x11grab --enable-libgsm --enable-libx264 --enable-liba52 --enable-libtheora --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --enable-swscale --enable-libdc1394 --enable-nonfree --disable-mmx --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil version: 49.7.0
  libavcodec version: 51.58.0
  libavformat version: 52.16.0
  libavdevice version: 52.0.0
  libavfilter version: 0.0.0
  built on Oct 22 2008 13:31:17, gcc: 4.3.2
Input #0, avi, from '/home/enrique/Escritorio/El gran Lebowski.avi':
  Duration: 01:52:13.64, start: 0.000000, bitrate: 1744 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 604x330 [PAR 1:1 DAR 302:165], 25.00 tb(r)
    Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Output #0, avi, to 'ElGranLewski.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 604x330 [PAR 1:1 DAR 302:165], q=2-31, 200 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: libmp3lame, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Does anyone know what I am doing wrong?

Thank you 
Enrique

---

### Post by mc4man on 2008-12-07
Well I'd change the -ab 448k to -ab 320k.

---

### Post by FakeOutdoorsman on 2008-12-08
FFmpeg can't create a MP3 stream with 5.1 channel surround sound.  Also, you may not need to re-encode the video.  This example will copy the video stream and force two channel (stereo) audio:
```
ffmpeg -y -i '/home/enrique/Escritorio/El gran Lebowski.avi' -vcodec copy -acodec libmp3lame -ab 448K -ac 2 ElGranLewski.avi
```
Forcing to stereo may cause some problems as explained by Stochastic in this thread: [downmix 5.1-channel .wav file to stereo]("http://ubuntuforums.org/showthread.php?t=963341").

---

### Post by enriqueaf on 2008-12-08
> **FakeOutdoorsman said:**
> FFmpeg can't create a MP3 stream with 5.1 channel surround sound.  Also, you may not need to re-encode the video.  This example will copy the video stream and force two channel (stereo) audio:
```
ffmpeg -y -i '/home/enrique/Escritorio/El gran Lebowski.avi' -vcodec copy -acodec libmp3lame -ab 448K -ac 2 ElGranLewski.avi
```
Forcing to stereo may cause some problems as explained by Stochastic in this thread: [downmix 5.1-channel .wav file to stereo]("http://ubuntuforums.org/showthread.php?t=963341").

Thank you for your answer, It works! I have read the post that you linked me and I will try with **Ardour**.

Thanks
Enrique

---

### Post by enriqueaf on 2008-12-08
Only one question, is there any way to convert an audio from a six channels ac3 to a **six channels mp3**??

Enrique

---

### Post by FakeOutdoorsman on 2008-12-08
If it sounds good enough to you then you may not have to deal with Ardour.  Just a suggestion if you do hear problems.  I don't think standard mp3 can handle more than two channels.  I you want six channels, then I think you can use wav, aac, or ac3.

---

