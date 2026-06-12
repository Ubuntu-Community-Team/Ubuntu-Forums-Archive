---
title: "Conver mp3 to ogg with details"
date: 2011-05-02
forum: Multimedia Software
---

### Post by Vishnu V on 2011-05-02
Hi
I would like to convert all my mp3 to ogg file. I got a script by googling.
Script is
```
for fic in *.mp3 
do 
	ffmpeg -i $fic -acodec vorbis -aq 60  ogg/${fic%.mp3}.ogg;
	mv $fic mp3/
done

```
But the problem is the ogg doesn't contains the details like title artist, album art etc. Ogggconvert help me to do that but there is no cli for that.
Is there any script to copy details of mp3 to ogg
Please help 

Thanks
Vishnu V

---

### Post by ChipOManiac on 2011-05-02
This might not really be of much use. But «Audacity» has a «Chain» feature where you can define a conversion (and a fe effects if you want). And it keeps the tags as well.

---

### Post by ron999 on 2011-05-02
> **Vishnu V said:**
> 
Is there any script to copy details of mp3 to ogg


Hi
You can use the same script if you like.
But change one line.
Like this:-
```
ffmpeg -i $fic -acodec vorbis -aq 60 [COLOR="Red"]-map_meta_data 0:0[/COLOR] ogg/${fic%.mp3}.ogg;
```
Or this:-
```
ffmpeg -i $fic -acodec vorbis -aq 60 [COLOR="Red"]-map_metadata 0:0[/COLOR] ogg/${fic%.mp3}.ogg;
```

---

### Post by Vishnu V on 2011-05-02
> **ron999 said:**
> Hi
You can use the same script if you like.
But change one line.
Like this:-
```
ffmpeg -i $fic -acodec vorbis -aq 60 [COLOR="Red"]-map_meta_data 0:0[/COLOR] ogg/${fic%.mp3}.ogg;
```
Or this:-
```
ffmpeg -i $fic -acodec vorbis -aq 60 [COLOR="Red"]-map_metadata 0:0[/COLOR] ogg/${fic%.mp3}.ogg;
```

Thanks for the replay

I installed ubuntu 11.04 today and found that we need to use libvorbis instead of vorbis
But when i tried 
```
ffmpeg -i $fic -acodec libvorbis -aq 60 -map_meta_data 0:0 ${fic%.mp3}.ogg
```
I got an error 
```

[mp3 @ 0x1531920]Header missing

```
The complete output is
```
acodec libvorbis -aq 60 -map_meta_data 0:0 ${fic%.mp3}.ogg;
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mp3 @ 0x1530670]max_analyze_duration reached
[mp3 @ 0x1530670]Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from 'raavana_prabhu_pot.mp3':
  Metadata:
    TMED            : DIG
    TIT2            : Pottu kuthedi
    TRCK            : 6
    TYER            : 2001
    TCON            : Other
    TALB            : Raavana Prabhu
    TPE1            : [Chorus]
  Duration: 00:04:21.42, start: 0.000000, bitrate: 160 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, 2 channels, s16, 160 kb/s
File 'raavana_prabhu_pot.ogg' already exists. Overwrite ? [y/N] y
Output #0, ogg, to 'raavana_prabhu_pot.ogg':
  Metadata:
    TMED            : DIG
    title           : Pottu kuthedi
    TRACKNUMBER     : 6
    TYER            : 2001
    genre           : Other
    album           : Raavana Prabhu
    artist          : [Chorus]
    encoder         : Lavf52.64.2
    Stream #0.0: Audio: libvorbis, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[mp3 @ 0x1531920]Header missingrate= 410.0kbits/s    
Error while decoding stream #0.0
size=   13159kB time=261.34 bitrate= 412.5kbits/s    
video:0kB audio:13086kB global headers:4kB muxing overhead 0.521544%

```
Still mp3 is converted into ogg without details

---

### Post by bashologist on 2011-05-02
That glob could include files with spaces so remember to use double quotes. Also try to redirect the input like below if you're not wanting to use ffmpeg interactively, since it could cause problems in some scenarios.
```
for fic in *.mp3; do 
	ffmpeg -i "$fic" ... "ogg/${fic%.mp3}.ogg" < /dev/null
	mv "$fic" mp3/
done
```

Edit:
Also you can save two bytes by changing your ${fic%.mp3} to ${fic%.*} and you wouldn't have to rewrite that part if you used it on aac or flac files in the future.

---

### Post by ron999 on 2011-05-02
@ Vishnu
Hi
Yes, I agree, use libvorbis instead of vorbis.
What do you see when you enter:-
```
ffprobe raavana_prabhu_pot.ogg
```

---

### Post by Vishnu V on 2011-05-02
> **bashologist said:**
> That glob could include files with spaces so remember to use double quotes. Also try to redirect the input like below if you're not wanting to use ffmpeg interactively, since it could cause problems in some scenarios.
```
for fic in *.mp3; do 
	ffmpeg -i "$fic" ... "ogg/${fic%.mp3}.ogg" < /dev/null
	mv "$fic" mp3/
done
```

Edit:
Also you can save two bytes by changing your ${fic%.mp3} to ${fic%.*} and you wouldn't have to rewrite that part if you used it on aac or flac files in the future.
Thanks for the suggestion
and now i got error 
```

ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM ...
[alsa @ 0x19477c0]cannot open audio device ... (No such file or directory)
Output #0, alsa, to '...':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Output #1, ogg, to 'roja_kadhal_rojave.ogg':
    Stream #1.0: Audio: flac, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.0 -> #1.0
Could not write header for output file #0 (incorrect codec parameters ?)


```
Detailed output is in post4 (Only error changes everything remains same)

---

### Post by Vishnu V on 2011-05-02
> **ron999 said:**
> @ Vishnu
Hi
Yes, I agree, use libvorbis instead of vorbis.
What do you see when you enter:-
```
ffprobe raavana_prabhu_pot.ogg
```

This is the output
```

FFprobe version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2007-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, ogg, from 'raavana_prabhu_pot.ogg':
  Duration: 00:04:21.34, start: 0.000000, bitrate: 412 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 499 kb/s
    Metadata:
      ENCODER         : Lavc52.72.2

```

---

### Post by ron999 on 2011-05-02
> **Vishnu V said:**
> This is the output
```


Input #0, ogg, from 'raavana_prabhu_pot.ogg':
  Duration: 00:04:21.34, start: 0.000000, bitrate: 412 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 499 kb/s
    Metadata:
      ENCODER         : Lavc52.72.2

```


Hmm
I don't know what's wrong.

In post #4 it shows:-
```
Output #0, ogg, to 'raavana_prabhu_pot.ogg':
  Metadata:
    TMED            : DIG
    title           : Pottu kuthedi
    TRACKNUMBER     : 6
    TYER            : 2001
    genre           : Other
    album           : Raavana Prabhu
    artist          : [Chorus]
    encoder         : Lavf52.64.2
    Stream #0.0: Audio: libvorbis, 44100 Hz, 2 channels, s16, 64 kb/s
```

But your ffprobe shows that the metadata did not get copied after all.

---

### Post by Vishnu V on 2011-05-02
> **ron999 said:**
> Hmm
I don't know what's wrong.

In post #4 it shows:-
```
Output #0, ogg, to 'raavana_prabhu_pot.ogg':
  Metadata:
    TMED            : DIG
    title           : Pottu kuthedi
    TRACKNUMBER     : 6
    TYER            : 2001
    genre           : Other
    album           : Raavana Prabhu
    artist          : [Chorus]
    encoder         : Lavf52.64.2
    Stream #0.0: Audio: libvorbis, 44100 Hz, 2 channels, s16, 64 kb/s
```
But your ffprobe shows that the metadata did not get copied after all.

Ok.
Anyway Thank you very much for the help

---

### Post by ron999 on 2011-05-02
> **Vishnu V said:**
> Ok.
Anyway Thank you very much for the help

Just test your command on one file, like this:-

```
ffmpeg -i raavana_prabhu_pot.mp3 -acodec libvorbis -aq 60 -map_meta_data 0:0 raavana_prabhu_pot.ogg

```
Then inspect the result again with ffprobe:-
```
ffprobe raavana_prabhu_pot.ogg
```

---

### Post by FakeOutdoorsman on 2011-05-02
FFmpeg 0.6 release is looking a bit old compared to the high level of activity in FFmpeg development. If you compile FFmpeg then it will automatically copy the metadata:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Example. Note that the values for *-aq* are different for each external encoder. See [Recommended Ogg Vorbis Encoder Settings](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis#Recommended_Encoder_Settings) for a nice chart showing suggested values.
```
$ ffmpeg -i 19\ Yeah\ Yeah\ Yeah\ Yeah\ Yeah.mp3 -acodec libvorbis -aq 6 out.ogg
...
Input #0, mp3, from '19 Yeah Yeah Yeah Yeah Yeah.mp3':
  Metadata:
    album           : Peace and Love
    artist          : The Pogues
    genre           : Rock
    title           : Yeah Yeah Yeah Yeah Yeah
    track           : 19
    date            : 1989
  Duration: 00:03:19.70, start: 0.000000, bitrate: 187 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 187 kb/s
Output #0, ogg, to 'out.ogg':
  Metadata:
    album           : Peace and Love
    artist          : The Pogues
    genre           : Rock
    title           : Yeah Yeah Yeah Yeah Yeah
    TRACKNUMBER     : 19
    date            : 1989
    encoder         : Lavf53.0.3
    Stream #0.0: Audio: libvorbis, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
```

```
$ ffmpeg -i out.ogg 
...
Input #0, ogg, from 'out.ogg':
  Duration: 00:03:19.70, start: 0.000000, bitrate: 187 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 192 kb/s
    Metadata:
      ALBUM           : Peace and Love
      ARTIST          : The Pogues
      GENRE           : Rock
      TITLE           : Yeah Yeah Yeah Yeah Yeah
      track           : 19
      DATE            : 1989
      ENCODER         : Lavf53.0.3
```

---

### Post by ron999 on 2011-05-02
> **FakeOutdoorsman said:**
>  Note that the values for *-aq* are different for each external encoder.

Yes, **aq 60** is being interpreted as **aq 10** (~500Kbps).:( **aq 6** is correct.

---

### Post by Vishnu V on 2011-05-03
> **ron999 said:**
> Just test your command on one file, like this:-

```
ffmpeg -i raavana_prabhu_pot.mp3 -acodec libvorbis -aq 60 -map_meta_data 0:0 raavana_prabhu_pot.ogg

```
Then inspect the result again with ffprobe:-
```
ffprobe raavana_prabhu_pot.ogg
```
Sorry
No change
Result of ffprobe raavana_prabhu_pot.ogg  after running ffmpeg -i raavana_prabhu_pot.mp3 -acodec libvorbis -aq 60 -map_meta_data 0:0 raavana_prabhu_pot.ogg
```

vishnu@vishnu-studio-1555:/media/storage/.multimedia/audio/mp3$ ffprobe raavana_prabhu_pot.ogg 
FFprobe version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2007-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, ogg, from 'raavana_prabhu_pot.ogg':
  Duration: 00:04:21.34, start: 0.000000, bitrate: 412 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 499 kb/s
    Metadata:
      ENCODER         : Lavc52.72.2

```

---

### Post by Vishnu V on 2011-05-03
Hi
I found that if i avoid -acodec libvorbis and run as below

```
ffmpeg -i raavana_prabhu_pot.mp3 -aq 60 -map_meta_data 0:0 raavana_prabhu_pot.ogg
```

Everything works fine. This commands copies details of mp3 to ogg
Result of ffprobe
```

ffprobe raavana_prabhu_pot.ogg 
FFprobe version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2007-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, ogg, from 'raavana_prabhu_pot.ogg':
  Duration: 00:04:21.35, start: 0.000000, bitrate: 824 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, 2 channels, s16
    Metadata:
      TMED            : DIG
      TITLE           : Pottu kuthedi
      TRACKNUMBER     : 6
      TYER            : 2001
      GENRE           : Other
      ALBUM           : Raavana Prabhu
      ARTIST          : [Chorus]
      ENCODER         : Lavf52.64.2


```
But now the size of output file is about 5 times the input file. And details are not shown in banshee

Sorry i cant check any more updates for two days because i need to go to my hostel.
I will surely post the reply for the updates after reached ma home

---

### Post by Vishnu V on 2011-05-06
The problem is due to old ffmpeg as said by FakeOutdoorsman. 
Problem almost solved

Thanks to ron999,FakeOutdoorsman 

Now some problems with cover art of files
This is the code to convert mp3 to ogg
```

for fic in *.mp3 
do 
	
	eyeD3 -1 -i ~/ $fic
	eyeD3 -2 -i ~/ $fic
	if [ -f ~/FRONT_COVER.jpeg ]
	then
		s=`base64 ~/FRONT_COVER.jpeg`
	else
		s=''
	fi
	ffmpeg -i $fic -acodec libvorbis -aq 6  ogg/${fic%.mp3}.ogg;
	vorbiscomment  -t "COVERART=$s" -t "COVERARTMIME=image/jpeg" -a  ogg/${fic%.mp3}.ogg ogg/${fic%.mp3}1.ogg;
	mv ogg/${fic%.mp3}1.ogg ogg/${fic%.mp3}.ogg;
	mv $fic mp3/
	rm ~/FRONT_COVER.jpeg
done

```
i dont have problem for cover art images with size < 50 KB. But cover art images having size > 50 doesn't work properly
i got the error
```

$ vorbiscomment  -t "COVERART=$s" -t "COVERARTMIME=image/jpeg" -a  aarutharum.ogg a.ogg
bash: /usr/bin/vorbiscomment: Argument list too long

```

Do you know why this error?


Thanks

---

### Post by FakeOutdoorsman on 2011-05-06
> **Vishnu V said:**
> The problem is due to old ffmpeg as said by FakeOutdoorsman. 
Problem almost solved

Thanks to ron999,FakeOutdoorsman
Glad we could help.

> **Vishnu V said:**
> i dont have problem for cover art images with size < 50 KB. But cover art images having size > 50 doesn't work properly
i got the error
```

$ vorbiscomment  -t "COVERART=$s" -t "COVERARTMIME=image/jpeg" -a  aarutharum.ogg a.ogg
bash: /usr/bin/vorbiscomment: Argument list too long

```

Do you know why this error?
Sorry, I don't have an answer, but if I were to make an uneducated guess perhaps the images must be below a certain file size.

---

### Post by Vishnu V on 2011-05-07
Problem Solved
Now i use convert to reduce the size of image & embedding it to ogg file solved my problem
here is the full script may be helpful for somebody

```

#!/bin/bash
if [  -f ogg ] 
then 
	j=0
	while [  -f ogg$j ]
	do
		j=`expr $j + 1`
	done
	mv ogg ogg$j 
fi
if [ ! -d ogg ]
then 
	mkdir ogg
fi
if [  -f mp3 ] 
then 
	j=0
	while [  -f mp3$j ]
	do
		j=`expr $j + 1`
	done
	mv mp3 mp3$j 
fi
if [ ! -d mp3 ]
then 
	mkdir mp3
fi
cp *.jp*g mp3/
mkdir ogg
rm ./*.jp*g
for fic in *.mp3 
do 
	eyeD3  -i . "$fic"
	eyeD3 -2 -i . "$fic"
	for i in *.jp*g
	do
		mv "$i" FRONT_COVER.jpeg
	done
	ffmpeg -i "$fic" -acodec libvorbis -aq 6  "ogg/${fic%.mp3}.ogg";
	if [ -f ./FRONT_COVER.jpeg ]
	then
		s=`base64 ./FRONT_COVER.jpeg`
		vorbiscomment  -t "COVERART=$s" -t "COVERARTMIME=image/jpeg" -a  "ogg/${fic%.mp3}.ogg" "ogg/${fic%.mp3}1.ogg";
		if [ $? -gt 0 ]
		then
			convert ./FRONT_COVER.jpeg -quality 80 ./FRONT_COVER.jpeg 
			s=`base64 ./FRONT_COVER.jpeg`
			vorbiscomment  -t "COVERART=$s" -t "COVERARTMIME=image/jpeg" -a  "ogg/${fic%.mp3}.ogg" "ogg/${fic%.mp3}1.ogg";
			while [ $? -gt 0 ]
			do
				convert FRONT_COVER.jpeg -resize 90% FRONT_COVER.jpeg
				s=`base64 ./FRONT_COVER.jpeg`
				vorbiscomment  -t "COVERART=$s" -t "COVERARTMIME=image/jpeg" -a  "ogg/${fic%.mp3}.ogg" "ogg/${fic%.mp3}1.ogg";

			done
		fi
	fi
	
	mv "ogg/${fic%.mp3}1.ogg" "ogg/${fic%.mp3}.ogg";
	mv "$fic" mp3/
	rm ./*.jp*g
done
zenity --info --title "Conversion Status" --text "Convertion of mp3 to ogg finished "

```
Only thing is that  running it as nautilus script wont work
We have to open a terminal in the current window & run this script in that terminal
I don't know nautilus script is not working properly !

Thank you all

---

