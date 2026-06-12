---
title: "Converting video to 3gp"
date: 2009-06-13
forum: Multimedia Software
---

### Post by Marlonsm on 2009-06-13
I just can't find a way to do that. I already Googled that, I tried with ffmpeg and with the WinFF (that is a GUI for ffmpeg).

this is the output I get on WinFF:
```
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

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 23.58 (283/12)
Input #0, avi, from '/media/MARLON/Ilha das Flores.avi':
  Duration: 00:13:17.19, start: 0.000000, bitrate: 2198 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x464 [PAR 1:1 DAR 40:29], 23.58 tbr, 23.58 tbn, 30k tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Unknown encoder 'libamr_nb'
Press Enter to Continue
```

How can I fix that, or are there any other converters I can try?

---

### Post by andrew.46 on 2009-06-13
Hi Marlonsm,

> **Marlonsm said:**
> 
```
Unknown encoder 'libamr_nb'Press Enter to Continue
```


Your copy of FFmpeg has not been compiled against the amr libraries unfortunately. Try running the following:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -formats | grep amr[/COLOR]**
FFmpeg version SVN-r19161, Copyright (c) 2000-2009 Fabrice Bellard, et al
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad **[COLOR="Purple"]--enable-libamr-wb --enable-libamr-nb[/COLOR]** 
--enable-libgsm --enable-libspeex --enable-zlib --enable-nonfree 
--enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.30. 2 / 52.30. 2
  libavformat   52.34. 0 / 52.34. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jun 12 2009 14:45:12, gcc: 4.2.4
 DE amr             3GPP AMR file format
[B][COLOR="Purple"] DEA    libamr_nb       libamr-nb Adaptive Multi-Rate (AMR) Narrow-Band
 DEA    libamr_wb       libamr-wb Adaptive Multi-Rate (AMR) Wide-Band[/COLOR][/B]

```

and I suspect that the lines I have outlined in purple will be missing?

Andrew

---

### Post by Marlonsm on 2009-06-13
Right, that's what I get:

```
marlon@marlon-desktop:~$ ffmpeg -formats | grep amr
FFmpeg version SVN-r19186, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.31. 2 / 52.31. 2
  libavformat   52.34. 0 / 52.34. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jun 13 2009 22:10:19, gcc: 4.3.3
 DE amr             3GPP AMR file format
```

---

### Post by sandyd on 2009-06-13
have you tried [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

---

### Post by Marlonsm on 2009-06-13
> **carlee said:**
> have you tried [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

I have, but I use the 64-bit Ubuntu, and there is only a 32-bit version on that site.

---

### Post by andrew.46 on 2009-06-13
Hi Marlonsm,

So if you were keen on using FFmpeg to do the conversion you could set our copy of FFmpeg as I have. Easiest way is to follow FakeOutdoorsman's guide on these forums:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

but add in the [Medibuntu archives]("https://help.ubuntu.com/community/Medibuntu") and compile against the amr libraries:

```

libamrnb-dev - floating-point Adaptive Multi-Rate (AMR) speech codec - Medibuntu package
libamrwb-dev - Adaptive Multi-Rate - Wideband (AMR-WB) speech codec - Medibuntu package

```

It is a bit of work if you are not used to this sort of thing but the results would be well worthwhile.

Andrew

---

### Post by Marlonsm on 2009-06-13
I've already tried that guide, but without the
```
libamrnb-dev - floating-point Adaptive Multi-Rate (AMR) speech codec - Medibuntu package
libamrwb-dev - Adaptive Multi-Rate - Wideband (AMR-WB) speech codec - Medibuntu package
```
It's getting late and I can't do it today, but I'll try that tomorrow.

Thank you, Andrew and carlee, for the help.

---

### Post by andrew.46 on 2009-06-14
Hi Marlonsm,

> **Marlonsm said:**
> I've already tried that guide, but without the
```
libamrnb-dev - floating-point Adaptive Multi-Rate (AMR) speech codec - Medibuntu package
libamrwb-dev - Adaptive Multi-Rate - Wideband (AMR-WB) speech codec - Medibuntu package
```
It's getting late and I can't do it today, but I'll try that tomorrow.

Excellent! Well if you revisit this guide don't forget to add:

```

  --enable-libamr-wb \
  --enable-libamr-nb \
  --enable-nonfree

```

to the ./configure string as well as installing the Medibuntu amr dev files. FFmpeg will then pick up and install the libraries.

Andrew

---

### Post by Marlonsm on 2009-06-14
Hi again, Andrew.

I've tried that, but it still didn't work, I can convert videos to other formats, but not to 3gp, here is what I get:
```
marlon@marlon-desktop:~/Desktop$ ffmpeg -i Ilha.avi Ilha.3gp
FFmpeg version SVN-r19191, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-libamr-wb --enable-libamr-nb
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.31. 2 / 52.31. 2
  libavformat   52.34. 0 / 52.34. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jun 14 2009 12:26:17, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 23.58 (283/12)
Input #0, avi, from 'Ilha.avi':
  Duration: 00:13:17.19, start: 0.000000, bitrate: 2198 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x464 [PAR 1:1 DAR 40:29], 23.58 tbr, 23.58 tbn, 30k tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[h263 @ 0x17c6d30]**[COLOR="Red"]The specified picture size of 640x464 is not valid for the H.263 codec.[/COLOR]**
Valid sizes are 128x96, 176x144, 352x288, 704x576, and 1408x1152. Try H.263+.
Output #0, 3gp, to 'Ilha.3gp':
    Stream #0.0: Video: h263, yuv420p, 640x464 [PAR 1:1 DAR 40:29], q=2-31, 200 kb/s, 90k tbn, 23.58 tbc
    Stream #0.1: Audio: libamr_nb, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

I've already tried setting bitrate, framerate and size, but I get the same output.
I also didn't understand that line in red, as I could convert to other formats.

I've also resized the video to 352x288 and tried again, I got the same error, but without that line:
```
marlon@marlon-desktop:~/Desktop$ ffmpeg -i Ilha2.avi Ilha.3gp
FFmpeg version SVN-r19191, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-libamr-wb --enable-libamr-nb
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.31. 2 / 52.31. 2
  libavformat   52.34. 0 / 52.34. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jun 14 2009 12:26:17, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 283.00 (283/1) -> 23.58 (283/12)
Input #0, avi, from 'Ilha2.avi':
  Duration: 00:13:17.20, start: 0.000000, bitrate: 278 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 352x288 [PAR 202:179 DAR 2222:1611], 23.58 tbr, 23.58 tbn, 283 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, 2 channels, s16, 64 kb/s
[libamr_nb @ 0x2ba3990]Only 8000Hz sample rate supported
Output #0, 3gp, to 'Ilha.3gp':
    Stream #0.0: Video: h263, yuv420p, 352x288 [PAR 202:179 DAR 2222:1611], q=2-31, 200 kb/s, 90k tbn, 23.58 tbc
    Stream #0.1: Audio: libamr_nb, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by andrew.46 on 2009-06-15
Hi Marlonsm,

> **Marlonsm said:**
> I've tried that, but it still didn't work, I can convert videos to other formats, but not to 3gp, 

Getting close though :-). Both h263 and amr have some pretty tight limitations. Try the following which has always worked for me:

```
ffmpeg -i *input.avi* -s qcif -vcodec h263 -r 25 \
-acodec libamr_nb -ac 1 -ar 8000 -ab 12200 *output.3gp*
```

with the obvious substitution for the input and output files.

All the best,

Andrew

---

### Post by Marlonsm on 2009-06-15
Thanks, it worked!

But I still can't change the output size, I wanted it 480x240 or qvga, but it only seems to work with qcif

And another question, is there a way to make it work with a GUI?

---

### Post by andrew.46 on 2009-06-16
Hi Marlonsm,

> **Marlonsm said:**
> But I still can't change the output size, I wanted it 480x240 or qvga, but it only seems to work with qcif

Your original error message suggests the answer:

```

[h263 @ 0x17c6d30]The specified picture size of 640x464 is not valid for the H.263 codec.
**[COLOR="Purple"]Valid sizes are 128x96, 176x144, 352x288, 704x576, and 1408x1152[/COLOR]**. Try H.263+.

```

You should be able to input any of these directly or use the relevant codes sqcif for 128x96 etc.

> And another question, is there a way to make it work with a GUI?

Hmmm.... my knowledge of winff is pretty minimal but I believe you can either alter the presets or add your own. Unfortunately I cannot help with this as I do not run the program but there are many here on the forums who know how to accomplish this.

All the best,

Andrew

---

### Post by paul.gevers on 2009-06-16
> **andrew.46 said:**
> Hmmm.... my knowledge of winff is pretty minimal but I believe you can either alter the presets or add your own. Unfortunately I cannot help with this as I do not run the program but there are many here on the forums who know how to accomplish this.

The documentation of WinFF describes this well IIRC. Available under the help button in WinFF (version 1.0.0 and up).

---

### Post by Marlonsm on 2009-06-16
Thankyou a alot, Andrew and Paul! :P

---

### Post by isaackrn on 2009-12-15
> **carlee said:**
> have you tried [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

  thanks!  mobilemediaconvertor is superb!

---

### Post by nbcskk on 2010-03-21
hi, i have meet the same problem as #1, then i re-installed ffmpeg follow the article "HOWTO: Install and use the latest FFmpeg and x264", and add
  --enable-libamr-wb \
  --enable-libamr-nb \
  --enable-nonfree
to ./configure, but i got this: 
[B]Unknown option "--enable-libamr-wb".
See ./configure --help for available options.[/B]
same to --enable-libamr-nb.
i thought it's because i didn't install the amrnb and amrwb package, but after i installed the two pkgs, which are "amrnb-7.0.0.2" and "amrwb-7.0.0.3", the problem exists as well.

how can i solve this??

---

