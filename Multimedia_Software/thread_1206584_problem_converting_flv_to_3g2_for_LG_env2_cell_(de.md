---
title: "problem converting flv to 3g2 for LG env2 cell (details provided)"
date: 2009-07-07
forum: Multimedia Software
---

### Post by davideps on 2009-07-07
Hi folks,

There is a lot of advice online about converting formats, but unfortunately I still cannot get this to work. I would like to convert video (in this case a .flv file) to the 3g2 format used by my LG env2 cell phone. As described below in more detail, I've already tried many permutations of mencoder and ffmpeg. I would like to use these tools or anything else that can be scripted easily. When the phone records video itself, the file has the following characteristics:





**********
davideps@system76-pc:~$ mplayer Desktop/0612091936.3g2 
MPlayer SVN-r29409-4.3.3 (C) 2000-2009 MPlayer Team

Playing Desktop/0612091936.3g2.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [mp4v]  176x144  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Requested audio codec family [qclp] (afm=qtaudio) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, floatle, 0.0 kbit/0.00% (ratio: 0->32000)
Selected audio codec: [ffqclp] afm: ffmpeg (FFmpeg QCLP audio)
==========================================================================
AO: [oss] 8000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.22:1 - prescaling to correct movie aspect.
VO: [x11] 176x144 => 176x144 Planar YV12 
[swscaler @ 0xd54340]using unscaled yuv420p -> rgb32 special converter
**********




FIRST: I do have sound, even though the system complains that it wants the "qclp" codec family. I thought I enabled this with mplayer's "configure" script before using "make". I still get the error though.  

SECOND: I simply do not know how to recreate this format using mencoder or ffmpeg. I get an error no matter what I do. Here is an example, please notice the "differing frame rate" problem and the "container" problem.




**********
davideps@system76-pc:~$ ffmpeg -i H0alnh1s3bw.flv -s 176x144 -acodec libmp3lame -ac 2 -ar 22050 -o test1.3g2
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'H0alnh1s3bw.flv':
  Duration: 00:07:55.33, start: 0.000000, bitrate: 286 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 254 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 32 kb/s
ffmpeg: unrecognized option '-o'
davideps@system76-pc:~$ ffmpeg -i H0alnh1s3bw.flv -s 176x144 -acodec libmp3lame -ac 2 -ar 22050 test1.3gp
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'H0alnh1s3bw.flv':
  Duration: 00:07:55.33, start: 0.000000, bitrate: 286 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 254 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 32 kb/s
File 'test1.3gp' already exists. Overwrite ? [y/N] y
Output #0, 3gp, to 'test1.3gp':
    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libmp3lame, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[3gp @ 0x10f97a0]track 1: could not find tag, codec not currently supported in container
Could not write header for output file #0 (incorrect codec parameters ?)
**********





Any help would be appreciated! THANK YOU!

-david

---

### Post by andrew.46 on 2009-07-07
Hi davideps,

> **davideps said:**
> 
FIRST: I do have sound, even though the system complains that it wants the "qclp" codec family. I thought I enabled this with mplayer's "configure" script before using "make". I still get the error though.

There are 2 choices with qclp, there is a native decoder and an external codec:

```

andrew@skamandros~/Desktop$ **[COLOR="Purple"]mplayer -ac help | grep qclp[/COLOR]**
**[COLOR="Purple"]ffqclp[/COLOR]**      ffmpeg    problems  FFmpeg QCLP audio  [qcelp]
**[COLOR="Purple"]qclp[/COLOR]**        qtaudio   working   QuickTime QCLP audio  [QuickTime.qts]

```

and I note that although ffqclp is marked as *problems* I have had no trouble with it. For the other you would need to load the so-called w32codecs from Medibuntu.

> SECOND: I simply do not know how to recreate this format using mencoder or ffmpeg. I get an error no matter what I do. Here is an example, please notice the "differing frame rate" problem and the "container" problem.

```

[3gp @ 0x10f97a0]track 1: could not find tag, codec not currently supported in container
Could not write header for output file #0 (incorrect codec parameters ?)

```


I believe that FFmpeg will not place mp3 audio in a 3gp container, hence the warning. Your best choice here might very well be amr audio:

```

andrew@skamandros~$ **[COLOR="Purple"]ffmpeg -formats | grep amr[/COLOR]**
FFmpeg version SVN-r19284, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
--prefix=/usr --mandir=/usr/man --disable-debug --enable-shared 
--disable-static --enable-postproc --enable-avfilter --enable-pthreads 
--enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb
 --enable-libgsm --enable-libspeex --enable-zlib --enable-nonfree
 --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jun 27 2009 21:18:28, gcc: 4.2.4
 DE amr             3GPP AMR file format
[B][COLOR="Purple"] DEA    libamr_nb       libamr-nb Adaptive Multi-Rate (AMR) Narrow-Band
 DEA    libamr_wb       libamr-wb Adaptive Multi-Rate (AMR) Wide-Band[/COLOR][/B]

```

But I do not know much about *3g2* beyond the fact that it exists so somebody with more experience will need to talk about creating these files. But certainly for ordinary *3gp* files you should be safe with h263 video and amr sound.

All the best,

Andrew

---

### Post by davideps on 2009-07-08
Andrew,

Thank you for your response. I was able to convert a file using an AMR codec, but will not be able to test it on my phone until this evening. It was a long process though to get to this point. I'll relate what I remember in the hope that others can learn from it and that SOMEONE may be able to explain it back to me.

Most of this is from memory--not actual terminal cut & paste....

>more ffmpeg -formats | grep amr
something like "DE amr" installed.

But,  I could not get this to work on the command line using "DE" or "DE amr" or "amr" or any other permutation. I finally decided to download & make the opencore_amr library and recompile ffmpeg with the opencore codec enabled. It compiled fine, but then...

>ffmpeg FILENAME
cannot find opencore library

I thought that codec libraries were required only at compile time!? Now completely confused, I just decided to reinstall the ffmpeg using the Synaptic Package Manager.  You can imagine my surprise when...

davideps@system76-pc:~$ ffmpeg -formats | grep amr
FFmpeg version SVN-r19369, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pthreads --enable-libx264 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-version3
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  7 2009 22:24:30, gcc: 4.3.3
 DE amr             3GPP AMR file format
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band

Yes, now it has opencore support. I simply don't understand how these codecs and libraries work yet. Anyway, the file I hope to test tonight was created with the following command:

davideps@system76-pc:~$ ffmpeg -i input.flv -s qcif -b 200000 -vcodec h263 -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 -ab 7950 -y outputfile.3gp

mplayer shows the video but without sound, reporting "Cannot find codec 'libamr_nb' in libavcodec." as shown below:

MPlayer SVN-r29409-4.3.3 (C) 2000-2009 MPlayer Team

Playing palin_test.3g2.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [s263]  176x144  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'libamr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.
Audio: no sound
Starting playback...
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 176x144 => 192x144 Planar YV12 
[swscaler @ 0xd54340]using unscaled yuv420p -> rgb32 special converter
V:   4.5   0/  0  9%  8%  0.0% 0 0                                    


take care,
-david

---

### Post by andrew.46 on 2009-07-08
Hi davideps,

> **davideps said:**
> 

```
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band
```

Yes, now it has opencore support.

Well, you are way ahead of me there :-). I believe that support for the free version of the amr libraries has only recently been added to FFmpeg and I am still running the older non-free libraries. Just in passing I note that an aac encoder has also just been added to the svn FFmpeg = very interesting times!

> mplayer shows the video but without sound, reporting "Cannot find codec 'libamr_nb' in libavcodec.

MPlayer does not appear to support the libopencore amr although I would imagine it will in time. Are you compiling your own MPlayer? If so simply add the 2 amr dev libraries from Medibuntu and then recompile and you will be able to play the files back. The test again will be:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -ac help | grep amr[/COLOR]**
ffamrnb     ffmpeg    working   AMR Narrowband  [libamr_nb]
ffamrwb     ffmpeg    working   AMR Wideband  [libamr_wb]

```

Just to muddy the waters a little more I should note that 3gp files can *also* support aac files but support can vary from device to device, amr is the lowest common denominator.

All the best,

Andrew

**Edit:** Looks like FFmpeg has removed support for the non-free amr lbraries, looks like I will be [building the libopencore ones]("http://ubuntuforums.org/showpost.php?p=7584660&postcount=409") sooner than I expected :)

---

### Post by davideps on 2009-07-09
Hi Andrew,


The flv video I converted to 3gp played with audio on my LG env2 cell phone. However, the audio was incredibly noisy--so much so that it was often difficult to follow the dialogue. I changed the filename to 3g2 just in case the phone was particular. I will need to try other audio settings using the libopencore_amr codec to see if I can improve the quality to something that is actually pleasant to listen to!    

Again, the settings I used for this first test were:

ffmpeg -i input.flv -s qcif -b 200000 -vcodec h263 -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 -ab 7950 -y outputfile.3gp

On a side note, when you say add the libopencore_amr libraries to mplayer and then recompile, you mean edit the configure file to have triggers for those libraries? Or something else? Either way, I'm not really up to that level yet. My mode of operating is I grep a configure file for desired options to learn how to enable them. I then type configure, make, and make install. If anything goes wrong, I see if it is a matter of missing dependencies or different directory names. Anything more complex than that and I search the forums, ask for help--or give up!

Have you seen any concise texts online that discuss "containers" and "codecs" in plain English?


take care,
-david

---

### Post by andrew.46 on 2009-07-09
> **davideps said:**
> 

Again, the settings I used for this first test were:

```
ffmpeg -i input.flv -s qcif -b 200000 -vcodec h263 -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 -ab 7950 -y outputfile.3gp
```



amr sound is not noted for its high quality I am afraid :-). I guess there are 2 choices, you could modify your commandline slightly:

```

ffmpeg -y -i input.flv -s qcif **[COLOR="Purple"]-b 200k[/COLOR]** -vcodec h263 -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 **[COLOR="Purple"]-ab 12200 [/COLOR]**outputfile.3gp

```

and this produced reasonable sound on my computer or try some aac sound:

```

ffmpeg -y -i test.flv -s qcif -b 200k -vcodec h263 **[COLOR="Purple"]-acodec libfaac -ac 1 -ab 64k[/COLOR]** outputfile.3gp

```

This also sounded ok on my computer. If you are using the repository version of FFmpeg you will have to add a few bits to get aac sound:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)


> On a side note, when you say add the libopencore_amr libraries to mplayer and then recompile, you mean edit the configure file to have triggers for those libraries? Or something else? Either way, I'm not really up to that level yet. My mode of operating is I grep a configure file for desired options to learn how to enable them. I then type configure, make, and make install. If anything goes wrong, I see if it is a matter of missing dependencies or different directory names. Anything more complex than that and I search the forums, ask for help--or give up!

Unfortunately MPlayer does not utilise the libopencore-amr libraries yet, it still uses the non-free amr libraries that you can get from Medibuntu as libamrnb-dev and libamrwb-dev. In the case of MPlayer you do not need to edit the configure file as MPlayer works by auto-detection rather than the standard adding of options. I suspect that soon MPlayer will switch over to the free libraries but I have no idea when.

> Have you seen any concise texts online that discuss "containers" and "codecs" in plain English?

It is a highly complex area and I know that I am usually accused of making it sound too complex :-). Perhaps a good start are the html pages that come with MPlayer? These can be accessed online:

[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

and should furnish a starting point at least.

Andrew

---

### Post by davideps on 2009-07-09
Hi Andrew,


Your suggestion to use a higher bitrate worked for 10.2k but failed with a segmentation fault for 12.2k. I did notice an improvement with the 10.2 and would like to try 12.2. What would cause a fault? I've got 4G of memory, though I doubt that matters. I've pasted the output below. Any ideas?


-david





davideps@system76-pc:~$ ffmpeg -y -i input.flv -s qcif -b 200k -vcodec h263 -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 -ab 12200 output-ab12200.3gp
FFmpeg version SVN-r19369, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pthreads --enable-libx264 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-version3
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  7 2009 22:24:30, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'input.flv':
  Duration: 00:07:55.33, start: 0.000000, bitrate: 254 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 254 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 2 channels, s16
Output #0, 3gp, to 'output-ab12200.3gp':
    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: libopencore_amrnb, 8000 Hz, 1 channels, s16, 12 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault8 q=3.7 size=    3275kB time=114.12 bitrate= 235.1kbits/s

---

### Post by andrew.46 on 2009-07-09
Hi davideps,

I am not sure about that one. I tried the exact commandline again on my own system:

```

andrew@skamandros~/Desktop$ [B][COLOR="Purple"]ffmpeg -y -i test.flv -s qcif -b 200k 
-vcodec h263 -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 
-ab 12200 output-ab12200.3gp[/COLOR][/B]
FFmpeg version SVN-r19390, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
--prefix=/usr --mandir=/usr/man --disable-debug --enable-shared 
--disable-static --enable-postproc --enable-avfilter --enable-pthreads 
--enable-libtheora --enable-libvorbis --enable-x11grab 
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
  built on Jul  9 2009 23:35:13, gcc: 4.2.4

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, flv, from 'test.flv':
  Duration: 00:03:38.04, start: 0.000000, bitrate: 253 kb/s
[B][COLOR="Purple"]    Stream #0.0: Video: flv, yuv420p, 320x240, 253 kb/s, 24 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 2 channels, s16[/COLOR][/B]
Output #0, 3gp, to 'output-ab12200.3gp':
[B][COLOR="Purple"]    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: libopencore_amrnb, 8000 Hz, 1 channels, s16, 12 kb/s[/COLOR][/B]
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[h263 @ 0x8075160]warning, clipping 1 dct coefficients to -127..127
    Last message repeated 2 times    87kB time=5.00 bitrate= 142.2kbits/s    
[h263 @ 0x8075160]warning, clipping 2 dct coefficients to -127..127
[h263 @ 0x8075160]warning, clipping 1 dct coefficients to -127..127
frame= 5451 fps=271 q=2.0 Lsize=    5785kB time=218.04 bitrate= 217.4kbits/s    
video:5356kB audio:341kB global headers:0kB muxing overhead 1.545208%


```

and apart from a few h263 warnings the file generated ok and played ok as well. You will note that I am using the *current* svn FFmpeg and perhaps this is the answer, it might be worth trying for an update following the Fakeoutdoorsman's guide + the extra opencore-amr information.

I have added my own 12.2 amr file (generated as above) to my website and perhaps you might like to have a look at it to see if it is really worth the effort or if aac might be a better answer :-). The file can be downloaded:

```
wget http://www.andrews-corner.org/samples/output-ab12200.3gp
```

I hope you are still having fun?

Andrew

---

### Post by davideps on 2009-07-09
Your sample file is funny and has decent sound. I may try to install the svn of ffmpeg later. First, I thought I'd try the "wide band" amr since I already tried "narrow band". Below you'll see that the format appears available...and then when I try to use it I'm told it does not exist!

-david



davideps@system76-pc:~$ ffmpeg -formats | grep amr

FFmpeg version SVN-r19369, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pthreads --enable-libx264 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-version3
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  7 2009 22:24:30, gcc: 4.3.3
 DE amr             3GPP AMR file format
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band




davideps@system76-pc:~$ ffmpeg -i H0alnh1s3bw.flv -s qcif -b 200000 -vcodec h263 -acodec libopencore_amrwb -ac 1 -ar 8000 -r 25 -ab 12200 -y outputfile.3gp
FFmpeg version SVN-r19369, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pthreads --enable-libx264 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-version3
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul  7 2009 22:24:30, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'H0alnh1s3bw.flv':
  Duration: 00:07:55.33, start: 0.000000, bitrate: 254 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 254 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 2 channels, s16
Unknown encoder 'libopencore_amrwb'



A bit frustrating.

-david

---

### Post by davideps on 2009-07-10
Hi again,


I decided to go forward with the svn ffmpeg compile. I followed the link you sent:

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Directions were excellent. Compile was smooth. I still have the SAME segmentation fault problem and the missing wide band amr library. However, the good news is that AAC works beautifully using the command line you provided:


ffmpeg -y -i test.flv -s qcif -b 200k -vcodec h263 **[COLOR=Purple]-acodec libfaac -ac 1 -ab 64k[/COLOR]** outputfile.3gp
Sound quality is excellent in comparison to AMR. I'm very pleased. In conclusion, everyone with a LG env2 cellphone should consider using these settings to transfer video. 

Andrew, thank you for your help. I hope others find this thread useful!


-david

---

### Post by andrew.46 on 2009-07-10
Hi david,

> **davideps said:**
> Your sample file is funny and has decent sound. I may try to install the svn of ffmpeg later.

I see from your next post you have succeeded with the svn FFmpeg, always the best way to go with FFmpeg encoding. You may wish to explore your phone a little further as newer phones are a lot more capable these days and will often take .mp4 files with an assortment of codecs,

> First, I thought I'd try the "wide band" amr since I already tried "narrow band". Below you'll see that the format appears available...and then when I try to use it I'm told it does not exist!


```
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band
```



I see the small misunderstanding there: 'DEA' implies that FFmpeg can _D_ecode and _E_ncode this _A_udio codec, while 'DA' implies that FFmpeg can only _D_ecode, so there is *no* encoding available with libopencore_amrwb.

Good to see you up and running though, a bit unfortunate you were working on this when FFmpeg is in the throes of changing AMR encoders :-). There are many, many other possibilities with the commandlines and probably a bunch of other possibilities with your phone that I am sure you can explore. An exciting possibility is the native aac encoder that FFmpeg has just placed in the main code, I have not experimented with this myself yet.

The continuing segfault is a bit odd and I am not sure what that is all about...

All the best,

Andrew

---

### Post by davideps on 2009-07-30
Hi again,

I was wondering why this same command does not appear to work when using the DVD drive as a source. In this example I'm trying to grab 1 minute of video starting 5 minutes into the DVD:

ffmpeg -i /dev/dvd  -b 200k -vcodec h263 -acodec libfaac -ac 1 -ab 64k -ss 00:05:00 -t 00:01:00 outputfile.3gp

FFmpeg version SVN-r19393, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 10 2009 00:05:03, gcc: 4.3.3
[mp1 @ 0x2ca7690]Header missing
    Last message repeated 40 times
Input #0, mp3, from '/dev/dvd':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: mp1, 0 channels, s16
File 'outputfile.3gp' already exists. Overwrite ? [y/N] y
[libfaac @ 0x2de23a0]libfaac doesn't support this output format!
Output #0, 3gp, to 'outputfile.3gp':
    Stream #0.0: Audio: aac, 1 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

