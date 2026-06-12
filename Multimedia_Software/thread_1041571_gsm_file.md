---
title: "gsm file"
date: 2009-01-16
forum: Multimedia Software
---

### Post by boondocks on 2009-01-16
[LIST=1]
[*]How do I play a GSM audio file?
[*]How do I convert a WAVE audio file to a GSM audio file?
[/LIST]

---

### Post by andrew.46 on 2009-01-17
Hi boondocks,

> **boondocks said:**
> [LIST=1]
[*]How do I play a GSM audio file?
[*]How do I convert a WAVE audio file to a GSM audio file?
[/LIST]

Not such an easy question as it turns and I am afraid that I cannot give you a complete answer but maybe a starting point. If you can compile ffmpeg with gsm support ffplay will play a file with the .gsm suffix and also wav files encoded with libgsm, which will have a .wav suffix. MPlayer can also play these wavs. Encoding from wav to libgsm wav can be done with a suitable configured ffmpeg, and the settings I give are what I believe to be the requirements for a 'classic' gsm file:

```
andrew@skamandros~/Desktop$ [B][COLOR="red"]ffmpeg -i test.wav -acodec libgsm_ms \
 -ar 8000 -ab 13000 -ac 1 -f gsm sample.wav[/COLOR][/B]
FFmpeg version SVN-r16649, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
--prefix=/usr --mandir=/usr/man --disable-debug --enable-shared 
--disable-static --enable-postproc --enable-avfilter --enable-pthreads 
--enable-libtheora --enable-libvorbis --enable-swscale --enable-x11grab 
--enable-libmp3lame --enable-libxvid --enable-libx264 
--enable-libschroedinger --enable-libfaac --enable-libamr-wb 
--enable-libamr-nb --enable-libgsm --enable-nonfree --enable-gpl
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52.10. 0 / 52.10. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 2. 0 /  0. 2. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 17 2009 13:43:37, gcc: 4.2.4
Input #0, wav, from 'test.wav':
  Duration: 00:21:50.34, bitrate: 1411 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Output #0, wav, to 'sample.wav':
    Stream #0.0: Audio: libgsm_ms, 8000 Hz, mono, s16, 13 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    2079kB time=1310.32 bitrate=  13.0kbits/s    
video:0kB audio:2079kB global headers:0kB muxing overhead 0.002818%

```

which produces the following file:

```

Input #0, wav, from 'sample.wav':
Duration: 00:21:50.35, bitrate: 13 kb/s
Stream #0.0: Audio: libgsm_ms, 8000 Hz, mono, s16, 13 kb/s

```

But I had all sorts of trouble producing a straight gsm file with ffmpeg. However the utility 'toast' that comes with libgsm seems to be able to do this:

```
$ toast -p test.wav
```

and the resulting file shows:

```

Input #0, gsm, from 'test.wav.gsm':
Duration: N/A, bitrate: N/A
Stream #0.0: Audio: libgsm, 8000 Hz, mono, s16

```

I am sorry that seems to be needlessly complicated but there is very little information available online concerning gsm encoding and decoding, so this represents me just working through a few options :-). Hopefully somebody clever can help out here?

All the best,

Andrew

---

### Post by boondocks on 2009-01-17
Thanks Andrew.

---

### Post by nikkkko on 2009-02-27
I have the same problem but the solution above is way too complicated for me.

However, Sox apparently supports .gsm, but the version in the Intrepid repository, v14.0.1, has no gsm support, whereas the latest version v14.2.0 which came out on Nov 08 does.  I really don't want to compile stuff myself as this computer has been totally stock for over 3 years so that means no gsm for me until the latest Sox makes it into the repository.

Boring.

---

