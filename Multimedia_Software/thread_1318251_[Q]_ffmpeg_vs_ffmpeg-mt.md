---
title: "[Q] ffmpeg vs ffmpeg-mt"
date: 2009-11-07
forum: Multimedia Software
---

### Post by arisu on 2009-11-07
I have tried reading various post concerning multi-threaded video decoding, but it is very confusing.  Here are some questions:

Q1: If I follow the guide: **HOWTO: Install and use the latest FFmpeg and x264 ( [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) )**, do I get multi-threaded video decoding ?

Q2: If not, is there a similar guide for compiling/installing ffmpeg-mt ?

Q3: Does VLC support multi-threaded video decoding ?  Or do I have to compile multi-threaded version of mplayer instead ?

---

### Post by FakeOutdoorsman on 2009-11-08
> **arisu said:**
> I have tried reading various post concerning multi-threaded video decoding, but it is very confusing.  Here are some questions:

Q1: If I follow the guide: **HOWTO: Install and use the latest FFmpeg and x264 ( [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) )**, do I get multi-threaded video decoding ?

You get slice-based multi-threaded decoding with the decoders *mpeg2* and *h264*.  I don't know the answers to your other questions.

---

### Post by andrew.46 on 2009-11-09
Hi arisu,

> **arisu said:**
>  Or do I have to compile multi-threaded version of mplayer instead ?

As regards MPlayer I have always thought that a bit of patience was always a good idea and I personally will wait until FFmpeg-mt is absorbed into the mainstream source code, whenever that will happen. For real decoding benefits vdpau is available *now* as a mature product. Just my 2 cents worth :).

Andrew

---

### Post by arisu on 2009-11-10
Thanks for the replies.

Hi FakeOutdoorsman,

Thanks to your howto guide, I installed the latest ffmpeg successfully and now have slice-based multi-threaded decoding for some of my h264 videos with VLC.  :)

Hi andrew.46,

Some forum posts say FFmpeg-mt won't be absorbed into the mainstream code for a long long time.  I will follow your advice and wait though.  I use ATI HD3650 so I will have to wait for hardware accelerated video decoding too...

-arisu

---

### Post by andrew.46 on 2009-11-10
Hi arisu,

> **arisu said:**
> Some forum posts say FFmpeg-mt won't be absorbed into the mainstream code for a long long time.  I will follow your advice and wait though.  I use ATI HD3650 so I will have to wait for hardware accelerated video decoding too...

Well, don't be too hasty you can still compile a copy if you are keen to experiment :). I have written a guide for the svn MPlayer under Karmic:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

and in response to a query I have mentioned how this guide could be modified to incorporate FFmpeg-mt:

[http://ubuntuforums.org/showpost.php?p=8259986&postcount=29](http://ubuntuforums.org/showpost.php?p=8259986&postcount=29)

I would be interested to hear if this produced good results for you? I compiled and tested it briefly but I am not so hungry for such things :).

All the best,

Andrew

---

### Post by arisu on 2009-11-11
Hi Andrew,
 
 I have 64-bit ubuntu 8.10 with ATI card, so I tried your "[Howto] Install the svn Mplayer under Intrepid Ibex" ( [http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592) ) and downloaded 64-bit video codecs instead. Both regular version and mplayer-svn-mt.tar.bz2 version failed but for different reasons:
 
 1. regular version (revision 29885):
 
 ```
libavcodec/libavcodec.a(h263dec.o): In function `ff_h263_decode_frame': h263dec.c:(.text+0x1536): undefined reference to `ff_vdpau_mpeg4_decode_picture' collect2: ld returned 1 exit status make: *** [mencoder] Error 1
``` I found one post ([http://article.gmane.org/gmane.comp.video.mplayer.user/61704](http://article.gmane.org/gmane.comp.video.mplayer.user/61704)) describing the same error but no solution is given.
 
 2. mplayer-svn-mt ( from just.mooo.com ) version:
 
 ```
libmpcodecs/ve_x264.c: In function 'config': libmpcodecs/ve_x264.c:188: error: 'x264_param_t' has no member named 'b_bframe_pyramid' make: *** [libmpcodecs/ve_x264.o] Error 1
``` This post ([http://ubuntuforums.org/showthread.php?t=1295537](http://ubuntuforums.org/showthread.php?t=1295537)) seems to imply that I should wait couple days and the x264 error will get resolved.

-arisu

---

### Post by andrew.46 on 2009-11-11
Hi arisu,

The first compilation error was addressed this morning:

```
andrew@skamandros~/source/mplayer/mplayer$ svn log -l 1
------------------------------------------------------------------------
r29891 | cehoyos | 2009-11-11 11:30:54 +1100 (Wed, 11 Nov 2009) | 1 line

10l: Fix compilation without VDPAU.
```

and should no longer be a problem, I encountered the same error and this revision fixed the problem. As for the second error just have a careful look at your system and ensure you *only* have the newest version of x264 available, sometimes a repository version can make life a little complicated. If there is only a single copy just wait a day or so before attempting again. I will admit I have not come across this error.

All the best,

Andrew

---

### Post by arisu on 2009-11-11
Hi Andrew,
 
 Thanks for the pointer. :) I was able to compile and install r29891.
 
 By the way, after testing the svn mplayer with ac3, I no longer got pcm sound over S/PDIF. In case anyone else encounters the same problem, there are many threads in the forum which explain the solution that worked for me. e.g. [http://ubuntuforums.org/showthread.php?t=388191](http://ubuntuforums.org/showthread.php?t=388191) 
 
Apparently, asound.state got corrupted. I booted into live CD, configured the sound, ```
sudo alsactl store
``` to get good asound.state, and then modified the corrupted asound.state accordingly. 

 I never encountered this problem with VLC though. 

 -arisu

---

### Post by andrew.46 on 2009-11-11
Hi arisu,

> **arisu said:**
>  Thanks for the pointer. :) I was able to compile and install r29891.

I am a little curious to know if you also managed to compile the MPlayer-mt version, and if it made a big difference in playback on your system?

Andrew

---

### Post by arisu on 2009-11-11
> **andrew.46 said:**
> Hi arisu,

I am a little curious to know if you also managed to compile the MPlayer-mt version, and if it made a big difference in playback on your system?

Andrew

Hi Andrew,

I am still getting the x264 error with today's mplayer-svn-mt.

I also tried runesvend's guide ([http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)) but that gives a different error:```
fmt-conversion.c:76: error: 'PIX_FMT_VDPAU_MPEG4' undeclared here (not in a function) make: *** [fmt-conversion.o] Error 1
```-arisu

---

### Post by arisu on 2009-11-12
> **andrew.46 said:**
> Hi arisu,

I am a little curious to know if you also managed to compile the MPlayer-mt version, and if it made a big difference in playback on your system?

Andrew

Turns out that libx264-dev was removed.  After I re-installed svn libx264-dev, I could make/checkinstall mplayer-svn-mt-r29748-4.3.2.
 
 As for playback, my first impression is that it seems to use less CPU and is slightly smoother than VLC v0.9.4 with svn ffmpeg.
 
 When compared to regular mplayer (svn-r29891-1_amd64), here are some benchmarks:
 
Note: I have Core2Duo 3.0GHz CPU, and I was running 3 virtual machines while doing the benchmark.  I might try mplayer-mt again later when I can turn off the vm's

 argument: -lavdopts threads=2 -vo null -benchmark -frames 5000 -ss 120 -nosound  

 Example 1:
 
 libavformat file format detected.
 [lavf] Video stream found, -vid 0
 [lavf] Audio stream found, -aid 1
 VIDEO:  [H264]  1440x1080  24bpp  29.970 fps  3965.2 kbps (484.0 kbyte/s)
 Clip info:
  major_brand: isom
  minor_version: 1
  compatible_brands: isom
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 
 regular mplayer:
 BENCHMARKs: VC:  64.818s VO:   0.009s A:   0.000s Sys:   1.453s =   66.280s
 BENCHMARK%: VC: 97.7940% VO:  0.0140% A:  0.0000% Sys:  2.1920% = 100.0000%
 
 mplayer-ffmpeg-mt:
 BENCHMARKs: VC:  50.905s VO:   0.007s A:   0.000s Sys:   0.687s =   51.599s
 BENCHMARK%: VC: 98.6558% VO:  0.0130% A:  0.0000% Sys:  1.3312% = 100.0000%
 
 Example 2:
 
 libavformat file format detected.
 [lavf] Video stream found, -vid 0
 [lavf] Audio stream found, -aid 1
 VIDEO:  [H264]  720x480  24bpp  29.970 fps  1499.6 kbps (183.1 kbyte/s)
 Clip info:
  major_brand: isom
  minor_version: 0
  compatible_brands: isommp41
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 
 regular mplayer:
 BENCHMARKs: VC:  14.208s VO:   0.003s A:   0.000s Sys:   0.421s =   14.632s
 BENCHMARK%: VC: 97.1016% VO:  0.0202% A:  0.0000% Sys:  2.8782% = 100.0000%
 
 mplayer-ffmpeg-mt:
 BENCHMARKs: VC:  11.119s VO:   0.003s A:   0.000s Sys:   0.277s =   11.400s
 BENCHMARK%: VC: 97.5369% VO:  0.0288% A:  0.0000% Sys:  2.4343% = 100.0000%

---

### Post by hanbin973 on 2009-11-13
I have a problem also.

in x264 blah blah... using mplayer-svn-mt thing from the mooo blah hompage.

```
libx264.c: In function 'encode_nals':
libx264.c:75: warning: implicit declaration of function 'x264_nal_encode'
libx264.c: In function 'X264_init':
libx264.c:190: error: 'x264_param_t' has no member named 'b_bframe_pyramid'
make[2]: *** [libx264.o] Error 1
make[2]: Leaving directory `/home/hanbin973/mplayer-etc/mplayer-mt/libavcodec'
make[1]: *** [libavcodec/libavcodec.a] &#50724;&#47448; 2
make[1]: Leaving directory `/home/hanbin973/mplayer-etc/mplayer-mt'
make: *** [build-stamp] &#50724;&#47448; 2

```

&#50724;&#47448; is a korean word meaning ' Error ' . 

This is keep happening from... i think ... A few weeks ago.

---

### Post by andrew.46 on 2009-11-13
Hi hanbin,

> **hanbin973 said:**
> in x264 blah blah... using mplayer-svn-mt thing from the mooo blah hompage.

I do not use mplayer-mt but you could probably work your way around this by either updating to the latest x264:

```
andrew@skamandros~$ **[COLOR="Red"]x264 --version[/COLOR]**
x264 0.79.91 2a35a01
built on Nov 13 2009, gcc: 4.3.3
```

or by specifying something like:

```
./configure --disable-x264 --disable-mencoder
```

(although to tell the truth --disable-mencoder also disables x264 compilation). There is a thread dedicated to MPlayer-mt on these forums that might be well worth searching out if there is more trouble.

All the best,

Andrew

---

### Post by alxgomz on 2009-11-13
Hello I have the very same error message while trying to compile gstreamer-plugins-good:

CC    gstx264enc.o
gstx264enc.c: In function &#8216;gst_x264_enc_init_encoder&#8217;:
gstx264enc.c:585: error: &#8216;x264_param_t&#8217; has no member named &#8216;b_bframe_pyramid&#8217;
make[3]: *** [libgstx264_la-gstx264enc.lo] Erreur 1

But I had no problem while compliing regulat mplayer  with the same x264 snapshot.
I noticed that snapshot size highly decreased since 2009-11-03.
I guess It should work again snapshots prior to 2009-11-03. If you wanna test this... let us know if it works.

---

### Post by alxgomz on 2009-11-14
Apparently lix264 renamed variable "b_bframe-pyramid" to "i_bframe_pyramid".
Hack the source code in order to match the new variable name and try to recompile.

---

### Post by rosc2112 on 2009-12-31
> **alxgomz said:**
> Apparently lix264 renamed variable &quot;b_bframe-pyramid&quot; to &quot;i_bframe_pyramid&quot;.
Hack the source code in order to match the new variable name and try to recompile.

 Worked a charm for me, same prob trying to compile libquicktime-1.1.3  Thanks!!

---

### Post by boriolis on 2010-01-01
thanks :) the same trick worked  ... when I compiled gst-plugins-ugly-0.10.13  using libx264-80

---

