---
title: "convert vids for Ipod"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Shugs81 on 2009-01-10
Hi Chaps...

Tried following the guides but for the life of me cannot get it working!:confused::confused::confused:

not the most frequent of users and still getting used to the terminal windows but it looked like i had everything installed... but when i try anything i get this output :

> 0.00% | FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from 'Ultimate Effects Pedals - 1st Pedal Board.avi':
  Duration: 00:11:53.1, start: 0.000000, bitrate: 1698 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 64 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'xvid'
0.00% | FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from 'Ultimate Effects Pedals - 1st Pedal Board.avi':
  Duration: 00:11:53.1, start: 0.000000, bitrate: 1698 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 64 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'libxvid'
0.00% | FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from 'Ultimate Effects Pedals - 1st Pedal Board.avi':
  Duration: 00:11:53.1, start: 0.000000, bitrate: 1698 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 64 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'libxvid'


I'm using mp4ize... thing is I can't even manage to get virtualbox set up right to try an use windows!!! if i could get stuff like this working windows would just be a dirty word... is there a graphical interface out there or is it all command line?

---

### Post by Shugs81 on 2009-01-10
not to mention i've istalled a lot of sh1t onto my system trying to get it to work!!!

---

### Post by tech0007 on 2009-01-10
I use avidemux from the repo.  It's gui and a few clicks can convert your videos suited for Ipod.

```

sudo apt-get update
sudo apt-get avidemux

```

---

### Post by andrew.46 on 2009-01-11
Hi Shugs81,

> **Shugs81 said:**
> 
```
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'xvid'
```

Two errors that should be easily corrected. You have probably given your bitrate as a simple number which ffmpeg interprets as bits/s not kbits/s. Simply add the letter 'k' after the number with no space. It would be easier to see this if you gave your commandline as well :-).

Your version of ffmpeg has been 'modified' by Ubuntu. To see if you have an xvid encoder try the following, I give an example from my own svn ffmpeg:

```
andrew@skamandros:~$ ffmpeg -formats | grep xvid
FFmpeg version SVN-r16495, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --disable-debug --enable-shared --disable-static --enable-postproc 
--enable-avfilter --enable-pthreads --enable-libtheora --enable-libvorbis 
--enable-swscale --enable-x11grab --enable-libmp3lame --enable-libxvid 
--enable-libx264 --enable-libschroedinger --enable-libfaac 
--enable-libamr-wb --enable-libamr-nb --enable-libspeex --enable-libgsm 
--enable-nonfree --enable-gpl
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52.10. 0 / 52.10. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 1. 0 /  0. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan  9 2009 01:00:12, gcc: 4.3.2
**[COLOR="Red"]  EV    libxvid         libxvidcore MPEG-4 part 2[/COLOR]**

```

And you can see down the bottom that I have compiled against xvid and can use 'libxvid' as an E(ncoder) V(ideo).

Andrew

---

### Post by FakeOutdoorsman on 2009-01-11
mp4ize is a little dated, but I believe it will work once you do two things:
[list][*] Install **libavcodec-unstripped-51**.  This package will enable some restricted encoders such as libxvid.
[*] Edit the mp4ize script as Andrew mentioned.  Either add a "k" to the appropriate area, or change:
```
DEFAULT_AUDIO_BITRATE = 128
DEFAULT_VIDEO_BITRATE = 400
```
to
```
DEFAULT_AUDIO_BITRATE = 128000
DEFAULT_VIDEO_BITRATE = 400000
```
[/list]

---

### Post by andrew.46 on 2009-01-11
Oops!! The mention of the 'mp4ize' script went straight over my head :(.  I should perhaps sleep more and post less!

Andrew

---

### Post by Shugs81 on 2009-01-11
cheers guys.... decided to give avidemux a try for now... I'll try t'other one cause it seems slow is and i'd like to compare the two!

---

