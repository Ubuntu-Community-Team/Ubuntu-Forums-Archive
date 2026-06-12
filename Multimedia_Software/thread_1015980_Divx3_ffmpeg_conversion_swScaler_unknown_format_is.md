---
title: "Divx3 ffmpeg conversion: swScaler unknown format is not supported as input format"
date: 2008-12-19
forum: Multimedia Software
---

### Post by hachel on 2008-12-19
hello,
i tried to convert an avi encoded with, according to ffmpeg, the msmpeg4-codec (vlc told me it was encoded with a DIV3-codec)
upon conversion ffmpeg states the following and aborts:
```
~$ ffmpeg -y -i /home/hachel/1.avi -b 768 -s 640x352 -vcodec libxvid -ab 127 -acodec libfaac -ac 2 -ab 64 -f mp4 /home/hachel/1.mp4

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from '/home/hachel/1.avi':
  Duration: 02:07:13.6, start: 0.000000, bitrate: 764 kb/s
    Stream #0.0: Video: msmpeg4, 640x352 [PAR 0:1 DAR 0:1], 29.97 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
swScaler: Unknown format is not supported as input format
Cannot get resampling context
```
if tested it with xvid and Divx5 codecs and there were no problems

any help?

---

### Post by FakeOutdoorsman on 2008-12-19
You're telling ffmpeg to encode at 768 bits/s, which is an incredibly low bitrate.  You need to add a "k" to your bitrates:
```
ffmpeg -y -i /home/hachel/1.avi -b 768k -vcodec libxvid -ab 128k -acodec libfaac -ac 2 -f mp4 /home/hachel/1.mp4
```
Also, you have "-ab" listed twice.  The standard ffmpeg from the Ubuntu Intrepid repository does not support libxvid or libfaac.  You can get those extra encoders with the unstripped ffmpeg library:
```
sudo apt-get install libavcodec-unstripped-51
```
This will give you similiar (but not as feature rich) as the Medibuntu ffmpeg for Ubuntu Hardy.

---

### Post by hachel on 2008-12-19
thanks with the bitrates

but it's still not working as there seems to be an error with the input-format encoded with msmpeg4 (other videos with different codecs like mpeg4 were working with the same settings (and low bitrates) without that swSacler error).

I probably need that particular codec, msmpeg4, don't I?

PS: the libavcodec-package was already installed, anyway, it doesn't seem to have a problem with my outputformat but rather with the inputformat of msmpeg4

thanks, hachel

---

### Post by FakeOutdoorsman on 2008-12-19
Show the output of:
```
ffmpeg -formats | grep msmpeg4
```
Should output:
```
DEVSD  msmpeg4
DEVSD  msmpeg4v1
DEVSD  msmpeg4v2
```
You could also try installing the unstripped libswscale and see if that helps:
```
sudo apt-get install libswscale-unstripped-0
```

---

### Post by hachel on 2008-12-19
it does output exactly that. And the libswscale didn't help either.

I just tried and was able to convert that video using mencoder, which I always thought was very similar to ffmpeg, somehow sharing that libavcodec 

Anyway, any more ideas, hopefully?

---

### Post by FakeOutdoorsman on 2008-12-19
I'm not sure why it's not working.  I was able to convert a msmpeg4/mp3 with no issues using the same ffmpeg.  However, ffmpeg from the repos is old and you might have better luck compiling the most recent ffmpeg since development is active:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

---

