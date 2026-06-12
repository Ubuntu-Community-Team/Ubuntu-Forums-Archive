---
title: "convert wma to avi"
date: 2009-05-31
forum: Multimedia Software
---

### Post by gsingh on 2009-05-31
Hi, 

I'm having problems converting .wma to .avi

I'm using WinFF to convert the file but its giving me the following error:

> FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, asf, from 'cars01.wmv':
  Duration: 00:35:23.24, start: 5.000000, bitrate: 52 kb/s
    Stream #0.0: Audio: 0x000a, 22050 Hz, mono, s16, 20 kb/s
    Stream #0.1: Video: MSS2 / 0x3253534D, 800x600, 30 kb/s, 1k tbr, 1k tbn, 1k tbc
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context





I've tried ffmpeg but not sure exactly the syntax i need to use.
I have searched the forum and used ffmpeg codes but none of them are working.


Any help much appreciated.

Thanks

---

### Post by FakeOutdoorsman on 2009-05-31
I don't think FFmpeg can decode MSS2 inputs.  You'll have to use something else, like MEncoder, but I'm not familiar with the syntax for that.

---

### Post by andrew.46 on 2009-06-01
Hi gsingh,

> **gsingh said:**
> 
```

Input #0, asf, from 'cars01.wmv':
Duration: 00:35:23.24, start: 5.000000, bitrate: 52 kb/s
Stream #0.0: Audio: 0x000a, 22050 Hz, mono, s16, 20 kb/s
Stream #0.1: Video: MSS2 / 0x3253534D, 800x600, 30 kb/s, 1k tbr, 1k tbn, 1k tbc

```


That is an amazingly toxic Microsoft proprietary mix of codecs :-). I believe that Audio 0x000a is actually Windows Media Audio Voice and certainly MPlayer will play this using an external codec:

```

andrew@skamandros~$ mplayer -ac help | grep 'Windows Media Audio'
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
**[COLOR="Purple"]wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll][/COLOR]**
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]

``` 

while the Windows Media Screen Codec is also covered by an external codec:

```

andrew@skamandros~$ mplayer -vc help | grep 'Windows Media Screen'
**[COLOR="Purple"]wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll][/COLOR]**

```

Small wonder FFmpeg choked on this one :-). I cannot test this sort of conversion as I cannot find a similar file but if you really want avi you could start with something like:

```

mencoder cars01.wmv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o cars.avi

```

but you would have to add in quality options for lame (-lameopts) and mpeg4 (further -lavcopts) if you wanted to go that way. 

Andrew

---

### Post by gsingh on 2009-06-02
thanks for your help.

I've tried the following, which worked.  But there is no audio, any ideas?

syntax used:

```
mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac copy -o cars01.avi

```

Thanks

---

### Post by andrew.46 on 2009-06-03
Hi gsingh,

> **gsingh said:**
> 
I've tried the following, which worked.  But there is no audio, any ideas?

```
mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac copy -o cars01.avi

``` 

Could be that the avi container is not happy with that type of audio. Could you run the MEncoder command with 'mencoder -v .....' and post the output here? This will exclude any other encoding problem.

If you wish to experiment a little it might be worth transcoding the sound to mp3 by using '-oac mp3lame'. To see if your version of MEncoder will transcode to mp3 run:

```

andrew@skamandros~$ **[COLOR="Purple"]mencoder -oac help[/COLOR]**
MEncoder SVN-r29340-4.2.4 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
 **[COLOR="Purple"]  mp3lame  - cbr/abr/vbr MP3 using libmp3lame[/COLOR]**
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

and if mp3lame does not appear there see if you can pick you can pick up [the Medibuntu MPlayer]("https://help.ubuntu.com/community/Medibuntu").

All the best,

Andrew

---

### Post by gsingh on 2009-06-04
Sorry andrew.46 i'm not sure what 'mencoder -v..' was.  

But GOOD NEWS - i've cracked it : 

```
mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts abr:br=56 -o cars01.avi
```

Thanks for your help.

---

### Post by gsingh on 2009-06-04
I can't see the file on my tv correctly, cars01.avi doesn't fit on my TV as its too big. Either my tv is rubbish or i encoded the file incorrectly 

I tried the following, but doesn't have made a difference:

```
mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts abr:br=56 -vf scale=800:600 -o cars01.avi
```

Is there an "auto fit"/resize command? Any help appreciated!

---

### Post by andrew.46 on 2009-06-04
Hi gsingh,

> **gsingh said:**
> Is there an "auto fit"/resize command? Any help appreciated!

Good to hear that you are almost there :-). There is an -autoaspect switch which you could try, but I am not sure if this would work on a television. You could alternatively think of rescaling differently with something like the following in your filter chain:

```
-vf -zoom -xy 800
```

This way will maintain aspect ratio for you while setting the width as you desire. I will admit that I have not tried to encode such a movie for television playback in this way so I am keen to see the *real* MEncoder experts jump in here.

Andrew

---

### Post by gsingh on 2009-06-06
I've tried the following, but it's not made a difference, any ideas?

```
mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts abr:br=56 -vf -zoom -xy 800 -o zoom.avi

mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts abr:br=56 -vf scale=640:-2,crop=640:480,expand=640:480 -o scale.avi

mencoder cars01.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts abr:br=56 -autoaspect -o auto.avi

```

---

### Post by andrew.46 on 2009-06-07
Hi gsingh,

I must apologise as I am afraid that I do not know how to transcode this movie to fit well on your tv. You have tried most of the options that I would have suggested except perhaps substitute:

```
-ofps 24000/1001
```

for your own setting of:

```
-ofps 23.976
```

but this is a side-note only. I have never actually transcoded for tv playback believe it or not so my knowledge of this is less than minimal. Hopefully a forum MEncoder guru will step forward soon to help out :-).

Apologies,

Andrew

---

### Post by andrew.46 on 2009-06-09
Hi gsingh,

Hmmmm... perhaps try:

```

mencoder cars01.wmv -ofps **[COLOR="Purple"]24000/1001[/COLOR]** \
         -ovc lavc -oac mp3lame -lameopts abr:br=56 \
         -vf **[COLOR="Purple"]scale[/COLOR]** -zoom -xy 800 -o zoom.avi

```

Andrew

---

