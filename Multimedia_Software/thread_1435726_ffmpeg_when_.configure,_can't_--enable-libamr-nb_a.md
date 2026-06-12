---
title: "ffmpeg when ./configure, can't --enable-libamr-nb and libamr-wb"
date: 2010-03-21
forum: Multimedia Software
---

### Post by nbcskk on 2010-03-21
i want to convert .flv to .3gp, when i configure ffmpeg with
```

 --enable-libamr-nb \
 --enable-libamr-wb

```
i got **Unknown option "--enable-libamr-wb" See ./configure --help for available options**. 
how to solve this?
i also have posted the question [here]("http://ubuntuforums.org/showpost.php?p=9002864&postcount=16"), but nobody replied yet.

---

### Post by andrew.46 on 2010-03-21
Hi nbcskk,

Are you compiling the current svn? If so the options are a now a little different:

```

andrew@skamandros~/source/ffmpeg/ffmpeg$ ./configure --help | grep 'amr'
  **[COLOR="Red"]--enable-libopencore-amrnb[/COLOR]** enable AMR-NB de/encoding via libopencore-amrnb [no]
  **[COLOR="Red"]--enable-libopencore-amrwb[/COLOR]** enable AMR-WB decoding via libopencore-amrwb [no]


```

and of course you will need the relevant -dev libraries for compilation to succeed...

Andrew

---

### Post by nbcskk on 2010-03-21
hi andrew.46.
yes, i checkout from current svn, now it works.
thank you very much!

---

### Post by nbcskk on 2010-03-21
oh, here comes another question
> ffmpeg -i input.flv -s 320x240 -vcodec h263 -r 25 -acodec libopencore-amrnb -ac 1 -ar 8000 -ab 12200 output.3gp
it says 
> Unknown encoder 'libopencore-amrnb'
why? i've just enabled it...
and i type 
> ffmpeg -formats | grep amr
the result are
> 
FFmpeg version SVN-r22612, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 22 2010 09:41:06 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-libopencore-amrnb --enable-libopencore-amrwb
  libavutil     50.12. 0 / 50.12. 0
  libavcodec    52.59. 0 / 52.59. 0
  libavformat   52.56. 1 / 52.56. 1
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
 DE amr             3GPP AMR file format

---

### Post by nbcskk on 2010-03-21
sorry, i solved this, it just i mistyped the "libopencore_amrnb" to "libopencore-amrnb"
everything's ok now, no question any more.

---

### Post by andrew.46 on 2010-03-21
Hi nbcskk,

> **nbcskk said:**
> sorry, i solved this, it just i mistyped the "libopencore_amrnb" to "libopencore-amrnb"
everything's ok now, no question any more.

I suspect with FFmpeg there are always more questions :). BTW with the newer FFmpeg you can see the codecs better as:


```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep amr [/COLOR]**
FFmpeg version SVN-r22610, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 21 2010 08:45:47 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libfaad 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3
 --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50.12. 0 / 50.12. 0
  libavcodec    52.59. 0 / 52.59. 0
  libavformat   52.56. 1 / 52.56. 1
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.18. 0 /  1.18. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[B][COLOR="Red"] D A    amrnb           Adaptive Multi-Rate NarrowBand
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band[/COLOR][/B]


```

All the best,

Andrew

---

### Post by nbcskk on 2010-03-21
> I suspect with FFmpeg there are always more questions .
yes, actually! hope i could get more experienced:D

---

### Post by sushant.d84 on 2011-03-22
> **nbcskk said:**
> sorry, i solved this, it just i mistyped the "libopencore_amrnb" to "libopencore-amrnb"
everything's ok now, no question any more.

Hey !! Same thing happened with me !! .. 
Now my version also run with amrnb... 


But Again !  I have another command which gives me error for AMR-WB
Please have a look here :(



root@user-desktop:~/ffmpeg_git# ffmpeg -i /opt/lampp/htdocs/smo/test.mpeg -ab 8.85k -acodec libopencore_amrwb -ac 1 -ar 16000 -vcodec h263 -s qcif /opt/lampp/htdocs/smo/output.3gp
FFmpeg version 0.6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 17 2011 13:33:15 with gcc 4.4.3
  configuration: --enable-libfaad --enable-gpl --enable-libfaac --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.11. 0 /  0.11. 0
[mpeg @ 0xa1e9420]max_analyze_duration reached
Input #0, mpeg, from '/opt/lampp/htdocs/smo/test.mpeg':
  Duration: 00:00:17.28, start: 1.000000, bitrate: 514 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x238 [PAR 1:1 DAR 160:119], 104857 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 29.97 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, 2 channels, s16, 64 kb/s
Unknown encoder 'libopencore_amrwb'


Please tell me how can I solve this.. 

Regards
Sushant Danekar

---

### Post by andrew.46 on 2011-03-22
> **sushant.d84 said:**
> 
```
Unknown encoder 'libopencore_amrwb'
```


FFmpeg does not have an *encoder* for amrwb, only amrnb :).

Andrew

---

### Post by sushant.d84 on 2011-03-23
Oh I see that !! 
I am new for this field 

Thanks for that 

now I am facing new problem 

============================================
root@user-desktop:/opt/lampp/htdocs/ffmpeg-0.6.0-old# ./configure  --enable-libfaad --enable-gpl --enable-libfaac --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-libmp3lame  --enable-cross-compile
Must specify target arch and OS when cross-compiling

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

==================================

Can you please help me out

---

### Post by FakeOutdoorsman on 2011-03-23
> **sushant.d84 said:**
> Can you please help me out

Remove *--enable-cross-compile* and it will work.

---

### Post by andrew.46 on 2011-03-23
I guess this is the problem option:

```
--enable-cross-compile
```

You have not mentioned why you are using this?

Andrew

---

### Post by sushant.d84 on 2011-03-24
Hey :P
Thanks for your reply .. 

I remove the options and now I got a new message.. 



root@user-desktop:/opt/lampp/htdocs/ffmpeg-0.6.0-old# ./configure   --enable-gpl --enable-libfaac --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-libmp3lame 
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --enable-cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

---

### Post by andrew.46 on 2011-03-24
> **sushant.d84 said:**
> I remove the options and now I got a new message...

I suspect that rather than continuing your attempts to build FFmpeg in this way you might be better to follow this guide:

HOWTO: Install and use the latest FFmpeg and x264 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This might make life a little easier for you :).

Andrew

---

### Post by andrew.46 on 2011-04-13
> **andrew.46 said:**
> FFmpeg does not have an *encoder* for amrwb, only amrnb :).

How quickly my words turn to dust in my mouth :(. This link shows some details of the new amr-wb *encoder* now possible with FFmpeg:

[http://ubuntuforums.org/showpost.php?p=10671718&postcount=1606](http://ubuntuforums.org/showpost.php?p=10671718&postcount=1606)

---

