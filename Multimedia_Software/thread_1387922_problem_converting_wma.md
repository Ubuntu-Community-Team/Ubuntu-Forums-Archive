---
title: "problem converting wma"
date: 2010-01-22
forum: Multimedia Software
---

### Post by Duncan7221 on 2010-01-22
I tried converting wma to mp3 with vlc, but an error comes up this is what it says.
 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG Audio layer 1/2/3.[/COLOR]

either how can i get that encoder for vlc or what else can i use to convert wma to mp3?

---

### Post by LuridCinema on 2010-01-22
Audacity can do that.. It's in the repositories

---

### Post by teresaejunior on 2010-01-22
What is the output of 'ffmpeg -formats D E' ???
Also make sure you have ffmpeg installed!

---

### Post by teresaejunior on 2010-01-22
double posted!

---

### Post by FakeOutdoorsman on 2010-01-22
> **Duncan7221 said:**
> I tried converting wma to mp3 with vlc, but an error comes up this is what it says.
 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG Audio layer 1/2/3.[/COLOR]

either how can i get that encoder for vlc or what else can i use to convert wma to mp3?
I believe VLC uses *libavcodec* to encode.  There are two versions of this package.  Assuming you are using Karmic, install the **libavcodec-extra-52** package.  It may make VLC able to encode to MP3, but I'm not very familiar with VLC (I like MPlayer myself).

---

### Post by Duncan7221 on 2010-01-22
Audacity won't import wma because it is a proprietary format. I installed that extra 52 thing for VLC and then it wouldn't do anything. Is there any program that can convert wma?

---

### Post by LuridCinema on 2010-01-22
> **Duncan7221 said:**
> Audacity won't import wma because it is a proprietary format. I installed that extra 52 thing for VLC and then it wouldn't do anything. Is there any program that can convert wma?
Crazy.. I am able to import .wma in **Audacity 1.3.10 beta**  and convert to .mp3 on my koala distro.... although I vaguely remember not being able to do it on a previous install... WHAT VERSION AUDACITY YOU HAVE ???..  I have read somewhere that if the .wma file has DRM it won't work

---

### Post by andrew.46 on 2010-01-22
Hi Duncan,

> **Duncan7221 said:**
>  Is there any program that can convert wma?

An appropriately configured vlc can do this, but I realise you are having some trouble with this one :). Perhaps try the commandline FFmpeg, best installed by following [FakeOutdoormsman's guide]("http://ubuntuforums.org/showthread.php?t=786095") and something like the following:

```

$ **[COLOR="Red"]ffmpeg -i Bangles.wma -acodec libmp3lame -ab 80k Bangles.mp3[/COLOR]**
FFmpeg version SVN-r21347, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Jan 20 2010 22:25:48 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-shared 
--disable-static --enable-postproc --enable-avfilter --enable-pthreads 
--enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libspeex
 --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.48. 0 / 52.48. 0
  libavformat   52.47. 0 / 52.47. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.17. 0 /  1.17. 0
  libswscale     0. 8. 0 /  0. 8. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, asf, from 'Bangles.wma':
  Metadata:
    WMFSDKVersion   : 7.01.00.3055
    WMFSDKNeeded    : 0.0.0.0000
[B][COLOR="Red"]Duration: 00:03:25.03, start: 2.600000, bitrate: 80 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 80 kb/s
Output #0, mp3, to 'Bangles.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 80 kb/s[/COLOR][/B]
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    2003kB time=205.14 bitrate=  80.0kbits/s    
video:0kB audio:2003kB global headers:0kB muxing overhead 0.001609%
```

Bear in mind that [wma audio]("http://en.wikipedia.org/wiki/Windows_Media_Audio") can come in 4 different flavours and this might create a challenge depending on where your copy of FFmpeg actually comes from...

All the best,

Andrew

---

### Post by mc4man on 2010-01-22
As Andrew mentioned there are several types of wma which becomes a factor in what you can and can't do. (and can sometimes account for why someone can and another can't

Almost everything can handle wma2
For wma3 , while gstreamer apps technically can handle, you may find since karmic that's not so.

For a gui for wma3 that will transfer tags soundkonverter will work fine and offers full mp3 options.
(though the gui can initially be a bit unclear.

As mentioned a more recent than ubuntu repo ffmpeg will work, though it's mp3 encoding parameters are limited.

wmal can be converted by vlc one file at a time if it's built with dmo loader enabled

mplayer can convert wmal to wav, it's pretty easy to do a batch convert of wmal's  with -  mplayer to wav to lame thru a script.

---

### Post by andrew.46 on 2010-01-22
Hi mc4man,

> **mc4man said:**
> mplayer can convert wmal to wav, it's pretty easy to do a batch convert of wmal's  with -  mplayer to wav to lame thru a script.

And a small addition: transcode can convert wmal by virtue of its mplayer import module and then export with whatever modules are available to transcode... An example using my all time favourite wmal clip:

```

[B][COLOR="Red"]$ transcode -H 0 -x null,mplayer -i luckynight.wma -y null,ogg \
>           -b 192 -E 44100,16,2 -o luckynight.ogg [/COLOR][/B]
transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | disabled
[transcode] V: bits/pixel       | 0.000 (unknown)
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG ES Layer 3 [44100,16,2]  192 kbps
[transcode] V: export format    | unknown (module dependant)
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 0x0 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_mplayer.so] v0.1.2 (2007-11-01) (video) rendered by mplayer | (audio) rendered by mplayer
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[export_ogg.so] v0.0.5 (2003-08-31) (video) null | (audio) ogg
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
**[COLOR="Red"][import_mplayer.so] mplayer -slave -hardframedrop -vo null -ao pcm:nowaveheader:file="/tmp/mplayer2transcode-audio.0pSNQa"  "luckynight.wma" > /dev/null 2>&1[/COLOR]**
[import_mplayer.so] tcextract -i /tmp/mplayer2transcode-audio.0pSNQa -x pcm -t raw
[export_ogg.so] Writing audio to "/dev/null" (no -m option)
**[COLOR="Red"][export_ogg.so] oggenc -r -B 16 -C 2 -b 192 --resample 44100 -R 48000 -Q -o "luckynight.ogg" [/COLOR]** -
[export_ogg.so] Hint: Now merge the files with0:55,  ( 8| 0|12) 
[export_ogg.so] Hint: ogmmerge -o complete.ogg luckynight.ogg luckynight.ogg
[decoder.c] cancelling the import threads

[transcode] encoded 1386 frames (0 dropped, 0 cloned), clip length  55.44 s

```

but of course when you look closely at the output you can see MPlayer at work converting to pcm and then oggenc creating the ogg file. Even so it is a very *tidy* way of doing it :).

Andrew

---

