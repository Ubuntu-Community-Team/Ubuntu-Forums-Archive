---
title: "errors using transcode, what is /dev/dvd?"
date: 2009-07-21
forum: Multimedia Software
---

### Post by raymondvillain on 2009-07-21
Using transcode.  Examples give /dev/dvd in the command line, but my optical drive is in directory /media/cdrom0.

Is this the reason for the following errors?

> ~$ transcode -d /media/cdrom0 -x dvd -T 1,16,1 -a 0 -y ogg -m benicio.ogg
transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
[transcode] warning : unused command line parameter detected (12/13)
[transcode] warning : argc[12]=/media/cdrom0 (unused)
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source (null) (ok)
[transcode] V: import format    | unknown  (V=dvd|A=null)
[transcode] V: import frame     | disabled
[transcode] V: bits/pixel       | 0.000 (unknown)
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import           | disabled
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 0 (0.000000)
[transcode] A: adjustment       | 0@1000
[transcode] A: swap bytes       | yes
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse2 memcpy
[transcode] warning : no option -i found, reading from "/dev/zero"
[transcode] V: video buffer     | 10 @ 0x0
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_ogg.so] v0.0.5 (2003-08-31) (video) null | (audio) ogg
[transcode] warning : (encoder.c) video codec not supported by export module
[transcode] warning : failed to init export modules
[transcode] critical: plug-in initialization failed

I get nearly the same messages if I use /dev/dvd.

Any suggestions?

---

### Post by igorzwx on 2009-07-21
[http://www.google.com/search?q=%2Fdev%2Fdvd&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=%2Fdev%2Fdvd&ie=UTF-8&oe=UTF-8)

---

### Post by andrew.46 on 2009-07-21
Hi raymondvillain,

> **raymondvillain said:**
> 
```
[transcode] warning : **[COLOR="Purple"]no option -i found[/COLOR]**, reading from "/dev/zero"
```

I use a newer version of transcode so I cannot fully test this but you could try:


```
transcode **[COLOR="Purple"]-i /dev/dvd[/COLOR]** -x dvd -T 1,16,1 -a 0 -y ogg -m benicio.ogg
```

Unfortunately the syntax has changed so much recently firm advice is difficult :-).

Hope this helps?

Andrew

---

### Post by igorzwx on 2009-07-21
Hi Adrew!

Have you tried to record screen with ffmpeg,
and then tcprobe?

---

### Post by raymondvillain on 2009-07-21
Thank you andrew.46.  This time it still failed, but things look slightly better.  The last 5 lines of the output:

> [import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[export_ogg.so] v0.0.5 (2003-08-31) (video) null | (audio) ogg
[transcode] warning : (encoder.c) video codec not supported by export module
[transcode] warning : failed to init export modules
[transcode] critical: plug-in initialization failed

I'm trying now to find out what these messages mean.

Am I right, that I must download (and compile something) FFmpeg source code in order for transcode to work?

---

### Post by andrew.46 on 2009-07-22
Hi raymondvillain,

> **raymondvillain said:**
> 
```
[transcode] warning : (encoder.c) video codec not supported by export module
```


Looks like transcode wants you to specify the export formats a little more explicitly. You could try:

```
transcode -i /dev/dvd -x dvd -T 1,16,1 -a 0 **[COLOR="Purple"]-y null,ogg[/COLOR]** -m benicio.ogg
```

Transcode can use FFmpeg certainly but it is not essential. Do you know how to test the import and export modules available to you? For import modules (the 'x' option):

```

andrew@skamandros~$  **[COLOR="Purple"]ls -1 $( tcmodinfo -p )/import*.so[/COLOR]**
/usr/lib/transcode/import_ac3.so
/usr/lib/transcode/import_alsa.so
/usr/lib/transcode/import_avi.so
/usr/lib/transcode/import_bsdav.so
/usr/lib/transcode/import_dv.so
/usr/lib/transcode/import_dvd.so
**[COLOR="Red"]/usr/lib/transcode/import_ffmpeg.so[/COLOR]**
/usr/lib/transcode/import_im.so
/usr/lib/transcode/import_imlist.so
/usr/lib/transcode/import_lzo.so
/usr/lib/transcode/import_mp3.so
/usr/lib/transcode/import_mpeg2.so
/usr/lib/transcode/import_mplayer.so
/usr/lib/transcode/import_null.so
/usr/lib/transcode/import_nuv.so
/usr/lib/transcode/import_ogg.so
/usr/lib/transcode/import_pvn.so
/usr/lib/transcode/import_raw.so
/usr/lib/transcode/import_v4l.so
/usr/lib/transcode/import_v4l2.so
/usr/lib/transcode/import_vag.so
/usr/lib/transcode/import_vnc.so
/usr/lib/transcode/import_vob.so
/usr/lib/transcode/import_x11.so
/usr/lib/transcode/import_xml.so
/usr/lib/transcode/import_xvid.so
/usr/lib/transcode/import_yuv4mpeg.so

```

and for export modules (the 'y' option):

```

andrew@skamandros~$ **[COLOR="Purple"]ls -1 $( tcmodinfo -p )/export*.so[/COLOR]**
/usr/lib/transcode/export_ac3.so
/usr/lib/transcode/export_divx5.so
/usr/lib/transcode/export_dv.so
/usr/lib/transcode/export_dvraw.so
**[COLOR="Red"]/usr/lib/transcode/export_ffmpeg.so[/COLOR]**
/usr/lib/transcode/export_im.so
/usr/lib/transcode/export_jpg.so
/usr/lib/transcode/export_lame.so
/usr/lib/transcode/export_lzo.so
/usr/lib/transcode/export_mp2.so
/usr/lib/transcode/export_mp2enc.so
/usr/lib/transcode/export_mpeg2enc.so
/usr/lib/transcode/export_null.so
/usr/lib/transcode/export_ogg.so
/usr/lib/transcode/export_pcm.so
/usr/lib/transcode/export_ppm.so
/usr/lib/transcode/export_pvn.so
/usr/lib/transcode/export_raw.so
/usr/lib/transcode/export_tcaud.so
/usr/lib/transcode/export_toolame.so
/usr/lib/transcode/export_wav.so
/usr/lib/transcode/export_xvid.so
/usr/lib/transcode/export_xvid4.so
/usr/lib/transcode/export_yuv4mpeg.so

```

It is good to see some interest in this great program, it is a little under-appreciated sometimes because of its perceived complexity :-).

Andrew

---

### Post by andrew.46 on 2009-07-22
Hi igorzwx,

> **igorzwx said:**
> 
Have you tried to record screen with ffmpeg,
and then tcprobe?

Well I have used ffmpeg/x11grab but I will confess to never having used tcprobe as a 'standalone' :-). And as it turns out I have compiled my own transcode and looks like I need to recompile as I have omitted a few libraries that tcprobe needs to run effectively. Oops!

Andrew

---

### Post by raymondvillain on 2009-07-22
Thanks for the encouragement, andrew.46.  I wish greatly to become an expert at transcode ( I would like to capture movie sound tracks of interest and play them back after I turn the DVD's in to Blockbuster, etc.).

But today I'm tied up with other things, so my transcode efforts are taking a back seat to earning a living.

I will try your suggestions in the very near future.

Thanks again,
raymondvillain

---

### Post by igorzwx on 2009-07-22
Hi Andrew!

it seems to be a bug in ffmpeg/x11grab.
you get 2fps on any box.
That is why tcprobe.
It come with the package transcode (as I remember).
I would be very gratefull, if you would clarify this in some way.

Best,
Igor

---

### Post by andrew.46 on 2009-07-22
Hi Igor,

> **igorzwx said:**
> 
it seems to be a bug in ffmpeg/x11grab.
you get 2fps on any box.
That is why tcprobe.
It come with the package transcode (as I remember).
I would be very gratefull, if you would clarify this in some way.



Still having some trouble with tcprobe + libquicktime but I took a screen capture with the following:

```

ffmpeg -y -vframes 200 -r 30 -g 300 -s 1024x768 -f x11grab -i :0.0 \
-vcodec mpeg4 -qscale 2 -mbd rd -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
test.avi

```

which actually does not look too bad BTW :-). tcprobe read the result as:

```

andrew@skamandros~/Desktop$ tcprobe -i test.avi 
[tcprobe] RIFF data, AVI video
[tcprobe] summary for test.avi, (*) = not default, 0 = not detected
import frame size: -g 1024x768 [720x576] (*)
     aspect ratio: 4:3 (*)
       frame rate: -f 30.000 [25.000] frc=5 (*)
   no audio track: (use "null" import module for audio)
           length: 299 frames, frame_time=33 msec, duration=0:00:09.966

```

All the best,

Andrew

---

### Post by igorzwx on 2009-07-22
Andrew!

thank you very much!

do you have the latest version of ffmpeg compiled?

this, perhaps, make a difference.

Could you please check ffmpeg with ffv1 too?

many thanks once more!

Best,
Igor

---

### Post by andrew.46 on 2009-07-22
Hi Igor,

> **igorzwx said:**
> do you have the latest version of ffmpeg compiled?

this, perhaps, make a difference.

I will admit to updating FFmpeg from svn every few days :-).

> Could you please check ffmpeg with ffv1 too?

Finally fixed tcprobe vs libquicktime, probably about time too as tcprobe is used by transcode's import modules! Anyway I ran the following:

```
ffmpeg -r 30 -s 1024x768 -f x11grab -i :0.0 -vcodec ffv1 test.avi
```

and tcprobe reported the following:

```

andrew@skamandros~/Desktop$ tcprobe -i test.avi 
[tcprobe] RIFF data, AVI video
[tcprobe] summary for test.avi, (*) = not default, 0 = not detected
import frame size: -g 1024x768 [720x576] (*)
     aspect ratio: 4:3 (*)
      **[COLOR="Red"] frame rate: -f 30.000 [25.000] frc=5 (*)[/COLOR]**
   no audio track: (use "null" import module for audio)
           length: 209 frames, frame_time=33 msec, duration=0:00:06.966

```

FFmpeg reports the file as:

```

andrew@skamandros~/Desktop$ **[COLOR="Purple"]ffmpeg -i test.avi [/COLOR]**
FFmpeg version SVN-r19467, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libgsm 
--enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jul 20 2009 16:55:32, gcc: 4.2.4
Input #0, avi, from 'test.avi':
[B][COLOR="Red"]  Duration: 00:00:06.96, start: 0.000000, bitrate: 28626 kb/s
    Stream #0.0: Video: ffv1, bgra, 1024x768, 30 tbr, 30 tbn, 30 tbc[/COLOR][/B]
At least one output file must be specified

```

Noe the huge bitrate :-).

Andrew

---

### Post by igorzwx on 2009-07-22
Andrew!

thank you very much!!!

---

### Post by raymondvillain on 2009-07-22
Success!

> transcode -i /dev/dvd -x dvd -T 1,16,1 -a 0 -y null,wav -m benicio.wav

The code above worked perfectly.  Thanks so much, andrew.46.

I find the transcode manual (man transcode) difficult to follow.  I'm looking for other sources of instruction, since it is such a powerful tool.

For example, it says "To get a list of valid codecs, use -F list (in another place, it says use -F invalid, which doesn't make sense, to me, anyway) but the output of

transcode -F list

does not list codecs.

---

### Post by andrew.46 on 2009-07-23
Hi raymondvillain,

> **raymondvillain said:**
> 
I find the transcode manual (man transcode) difficult to follow.  I'm looking for other sources of instruction, since it is such a powerful tool.

The version I am using has split the man pages up a little and this has made things a little easier:

```

andrew@skamandros~$ transcode --version
transcode v1.1.2 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team

```

But as you already know Transcode is rather poorly documented :-).

> For example, it says "To get a list of valid codecs, use -F list (in another place, it says use -F invalid, which doesn't make sense, to me, anyway) but the output of

```
transcode -F list
```

does not list codecs.

This is an option that I have not used all that much but I can give an example. I have been using Transcode to transcode parts of The Blues Brothers to mp3 and ffmpeg and the following allows Transcode to demonstrate what codecs FFmpeg offers:

```

transcode -x dvd -i /dev/dvd -T 1,3,1 -y ffmpeg,tcaud **[COLOR="Red"]-F list[/COLOR]** \
           --lame_preset standard -E 44100,16,2 \
           -o $HOME/Desktop/james_brown.avi

```

and this shows the following:

```

[export_ffmpeg.so] List of known and supported codecs:
[export_ffmpeg.so]  Name       fourCC multipass comments
[export_ffmpeg.so]  ---------- ------ --------- -----------------------------------
[export_ffmpeg.so]  mpeg4       DIVX     yes    MPEG4 compliant video
[export_ffmpeg.so]  msmpeg4     div3     yes    old DivX3 compatible (aka MSMPEG4v3)
[export_ffmpeg.so]  msmpeg4v2   MP42     yes    old DivX3 compatible (older version)
[export_ffmpeg.so]  mjpeg       MJPG      no    Motion JPEG
[export_ffmpeg.so]  ljpeg       LJPG      no    Lossless JPEG
[export_ffmpeg.so]  mpeg1video  mpg1     yes    MPEG1 compliant video
[export_ffmpeg.so]  mpeg2video  mpg2     yes    MPEG2 compliant video
[export_ffmpeg.so]  h263        h263      no    H263
[export_ffmpeg.so]  h263p       h263     yes    H263 plus
[export_ffmpeg.so]  h264        h264     yes    H264 (avc)
[export_ffmpeg.so]  wmv1        WMV1     yes    Windows Media Video v1
[export_ffmpeg.so]  wmv2        WMV2     yes    Windows Media Video v2
[export_ffmpeg.so]  rv10        RV10     yes    old RealVideo codec
[export_ffmpeg.so]  huffyuv     HFYU     yes    Lossless HUFFYUV codec
[export_ffmpeg.so]  dvvideo     DVSD      no    Digital Video
[export_ffmpeg.so]  ffv1        FFV1      no    FF Video Codec 1 (an experimental lossless codec)
[export_ffmpeg.so]  asv1        ASV1      no    ASUS V1 codec
[export_ffmpeg.so]  asv2        ASV2      no    ASUS V2 codec

```

And I agree this is less than perfectly demonstrated in the documentation!

Andrew

---

### Post by raymondvillain on 2009-07-24
Thanks, Andrew.  How does one obtain version 1.1.2?  I have 1.0.7.

I got it with "sudo apt-get install transcode".  I'm afraid to ask, but did you compile and build your version?

raymondvillain

---

### Post by andrew.46 on 2009-07-24
Hi raymondvillain,

> **raymondvillain said:**
> How does one obtain version 1.1.2?  I have 1.0.7.
I got it with "sudo apt-get install transcode".  I'm afraid to ask, but did you compile and build your version?

My own version was compiled from source and I can tell you it was a difficult one as there are quite extensive dependencies. Some good news though is that karmic Koala will feaure this version:

[http://packages.ubuntu.com/karmic/transcode](http://packages.ubuntu.com/karmic/transcode)

Andrew

---

