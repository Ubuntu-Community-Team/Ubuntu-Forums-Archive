---
title: "ffmpeg options and dependencies"
date: 2010-03-27
forum: Multimedia Software
---

### Post by Mia1990 on 2010-03-27
I was reading on the internet and was wondering what these options do in ffmpeg and what there dependencies are?
> --enable-version3
> --enable-libopencore-amrnb 
> --enable-libopencore-amrwb
> --enable-liba52 

also is there a site were i can read about the dependencies
Thank you

---

### Post by andrew.46 on 2010-03-27
Hi Mia1990,

The opencore amr options are a very exciting feature of recent FFmpeg IMHO. Previously to get amr decoding and encoding it was necessary to compile against [some libraries]("http://www.penguin.cz/~utx/amr") with precarious distribution rights in some countries. libopencoreamr does not have this problem with distribution and usage and can be compiled into FFmpeg and used while native encoders/decoders are being developed. ALso legally packaged with Linux distributions. Its licensing requires [the version3 option]("http://lists.mplayerhq.hu/pipermail/ffmpeg-cvslog/2009-June/023133.html"):

```

+The OpenCORE external libraries are under the Apache License 2.0. That license
+is incompatible with the LGPL v2.1 and the GPL v2, but not with version 3 of
+those licenses. So to combine the OpenCORE libraries with FFmpeg, the license
+version needs to be upgraded by passing --enable-version3 to configure.


```

As far as I know there is no single website or forum that contains details of all the options :(.

All the best,

Andrew

---

### Post by Mia1990 on 2010-03-27
When i compiled ffmpeg i did pass --enable-version3 off but i did not know to take out --enable-gpl or maybe it's --enable-nonfree i think that is what i did wrong just knot sure.I don't think i am going to compile again unless i can get a svn copy of ffmpeg before they replaced vhooks.I did compile with the current svn ffmpeg and ever time i made a movie
i always had a error and it took all night to do.Don't guess you would know were i could download a copy of the source to svn ffmpeg would you? Thanks

---

### Post by mc4man on 2010-03-27
ffmpeg 0.5.1 has vhooks (is enabled by default
Both karmic and lucid use that version (but disable vhooks), though you could use the source 
```

 wget http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/ffmpeg_0.5+svn20090706.orig.tar.gz
```

or just get directly
```
wget http://ffmpeg.org/releases/ffmpeg-0.5.1.tar.bz2
```

I believe --enable-nonfree is for libfaac support (--enable-libfaac

--enable-gpl and --enable-version3 don't conflict

---

### Post by Mia1990 on 2010-03-27
Ok i recompiled svn ffmpeg when i run tovid it say something about vhook's not found and when i run winff it gives me this.Any idea what i did wrong or how to fix it?Thank you

> Seems stream 0 codec frame rate differs from container frame rate: 59.94 (7492/125) -> 29.92 (359/12)
Input #0, flv, from '/home/me/Videos/V first 8 min':
  Duration: 00:09:30.80, start: 0.000000, bitrate: 610 kb/s
    Stream #0.0: Video: h264, yuv420p, 528x296 [PAR 1:1 DAR 66:37], 610 kb/s, 29.92 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
File '/home/me/Documents/temp/V first 8 min.mpg' already exists. Overwrite ? [y/N] y
Output #0, dvd, to '/home/me/Documents/temp/V first 8 min.mpg':
    Stream #0.0: Video: mpeg2video (hq), yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 8000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
/usr/local/bin/ffmpeg: symbol lookup error: /usr/local/bin/ffmpeg: undefined symbol: frame_hook_process
Press Enter to Continue

---

### Post by andrew.46 on 2010-03-27
Hi Mia,

I left out:

```
--enable-liba52 
```

which was removed from FFmpeg quite some time ago. Previously it served as FFmpeg's ac3 decoder but a native implementation now exists:

```

andrew@skamandros~$ ffmpeg -codecs | grep ac3
FFmpeg version SVN-r22704, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 28 2010 10:30:45 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libfaad 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 
--enable-zlib --enable-nonfree --enable-gpl
  libavutil     50.13. 0 / 50.13. 0
  libavcodec    52.61. 0 / 52.61. 0
  libavformat   52.57. 1 / 52.57. 1
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.18. 0 /  1.18. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**[COLOR="Red"] DEA    ac3             ATSC A/52A (AC-3)[/COLOR]**
 D A    atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
**[COLOR="Red"] D A    eac3            ATSC A/52B (AC-3, E-AC-3)[/COLOR]**

```

Note that ac3 *encodes* as well. I guess this shows the danger of finding old guides on the Internet that have not kept up with FFmpeg's changes :).

All the best,

Andrew

---

### Post by mc4man on 2010-03-27
> Ok i recompiled svn ffmpeg when i run tovid it say something about vhook's not found 

That seems the same as a couple of months ago - I gather you did build a 0.5 static ffmpeg w/ vhooks then to use with tovid, since then you've ..? (and that build was unsuitable?

Even then I wondered why you need vhooks, from what I've seen of tovid it's not required.

> /usr/local/bin/ffmpeg: symbol lookup error: /usr/local/bin/ffmpeg: undefined symbol: frame_hook_process


Would seem to indicate you have more than 1 ffmpeg install, though that was also an issue with some debian builds a year or so ago.

What source did you just build? ( you could post the terminal output of 
ffmpeg

I saw you mention recently that you were having issues when your 'svn ffmpeg' updated.
Ubuntu repo ffmpeg and libs almost never update, a self built ffmpeg will never update itself, so...

Have you added and are using/used a ppa or other repo for ffmpeg?, debian-multimedia comes to mind.

---

### Post by Mia1990 on 2010-03-27
> **mc4man said:**
> That seems the same as a couple of months ago - I gather you did build a 0.5 static ffmpeg w/ vhooks then to use with tovid, since then you've ..? (and that build was unsuitable?

Even then I wondered why you need vhooks, from what I've seen of tovid it's not required.



Would seem to indicate you have more than 1 ffmpeg install, though that was also an issue with some debian builds a year or so ago.

What source did you just build? ( you could post the terminal output of 
ffmpeg

I saw you mention recently that you were having issues when your 'svn ffmpeg' updated.
Ubuntu repo ffmpeg and libs almost never update, a self built ffmpeg will never update itself, so...

Have you added and are using/used a ppa or other repo for ffmpeg?, debian-multimedia comes to mind.
here is were i downloaded the source from
> wget [http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/ffmpeg_0.5+svn20090706.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/ffmpeg_0.5+svn20090706.orig.tar.gz)a while back i did build a ffmpeg with vhooks i am just blonde i am always looking for new features and stuff and it get's me into trouble every time.
vhooks are not required by tovid but they make the quick menu option run 50% faster.
I think i am going to put the 0.5 build back it worked fine i was just seeing what new features they have put in i have to stop doing that.There is just 1 ffmpeg on my system or if there is another i don't even know about it i build almost everything with checkinstall the only one i don't is tovid for some reason it don't work on it.But just to be sure is there a way i can purge anything to do with ffmpeg from my pc?ffmpeg did update when i installed the new svn version but i made it stop with the lock current version option.Thank you

---

