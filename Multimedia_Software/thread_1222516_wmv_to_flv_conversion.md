---
title: "wmv to flv conversion ?"
date: 2009-07-25
forum: Multimedia Software
---

### Post by garyed on 2009-07-25
I'm trying to convert some wmv movies to flv but they lose the sound after conversion. I posted in the beginners forum but I never got it resolved.
the code I'm using is:
```

ffmpeg -i first.wmv -vcodec flv first.flv

```

I get an error during the encoding about the audio codec not recognized.
I'm running Hardy. Anyone have any ideas?

---

### Post by andrew.46 on 2009-07-25
Hi garyed,

> **garyed said:**
> 
```
ffmpeg -i first.wmv -vcodec flv first.flv
```

I get an error during the encoding about the audio codec not recognized.
I'm running Hardy.

A couple of ideas:

[LIST=1]
[*]Since you are running Hardy have a look at the [Fakeoutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=1117283") to getting the most out of your ?repository FFmpeg.
[*]Post the full command and full terminal output here, this will make it much easier to diagnose the problem.
[/LIST]

wmv files can be a little tricky depending on exactly what codecs have been used to make them.

Andrew

---

### Post by garyed on 2009-07-25
Thanks for the reply,I got called away from the computer & then fell asleep.

Here's my command & output:
> gary@gary-desktop:~/downloads$ ffmpeg -i first.wmv -vcodec flv first.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, asf, from 'first.wmv':
  Duration: 00:02:49.7, start: 5.000000, bitrate: 318 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 352x240, 29.92 fps(r)
Output #0, flv, to 'first.flv':
  Stream #0.0: Video: flv, yuv420p, 352x240, q=2-31, 200 kb/s, 29.92 fps(c)
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
frame= 5064 q=5.4 Lsize=    4421kB time=169.3 bitrate= 214.0kbits/s    
video:4330kB audio:0kB global headers:0kB muxing overhead 2.108244%
gary@gary-desktop:~/downloads$ 

I assume the audio:0kb means it couldn't convert the audio.

---

### Post by andrew.46 on 2009-07-25
Hi garyed,

> **garyed said:**
> 
```

Duration: 00:02:49.7, start: 5.000000, bitrate: 318 kb/s
Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
Stream #0.1: Video: wmv3, yuv420p, 352x240, 29.92 fps(r)
Output #0, flv, to 'first.flv':
Stream #0.0: Video: flv, yuv420p, 352x240, q=2-31, 200 kb/s, 29.92 fps(c)
Stream mapping:
Stream #0.1 -> #0.0

```


Looks like the audio is not actually encoded at all. For flv files you can choose either aac or mp3 sound and I guess mp3 sound would be the safest. So try the following:

```
ffmpeg -i first.wmv -vcodec flv -acodec mp3 first.flv
```

Hardy's FFmpeg uses slightly older syntax than the modern version where you would see *-acodec libmp3lame*. 

Andrew

---

### Post by garyed on 2009-07-25
> **andrew.46 said:**
> Hi garyed,



Looks like the audio is not actually encoded at all. For flv files you can choose either aac or mp3 sound and I guess mp3 sound would be the safest. So try the following:

```
ffmpeg -i first.wmv -vcodec flv -acodec mp3 first.flv
```

Hardy's FFmpeg uses slightly older syntax than the modern version where you would see *-acodec libmp3lame*. 

Andrew

I still get unsupported audio codec:
I tried -acodec mp3 exactly as you posted & then libmp3lame & also mp3lame & they all gave the same result.
What's strange is I also tried mencoder & it converted the audio fine but the video was blank.

---

### Post by andrew.46 on 2009-07-25
Hi garyed,

> **garyed said:**
> I still get unsupported audio codec:
I tried -acodec mp3 exactly as you posted & then libmp3lame & also mp3lame & they all gave the same result.

Very odd. Can I ask where your copy of FFmpeg came from? It looks like an older version compiled on a new system which is also a little odd. And perhaps you can post this problem file somewhere online? I would be keen to have a look at it.

Andrew

---

### Post by garyed on 2009-07-25
I had ffmpeg from my original install of Hardy that did the same thing.
A few days ago I uninstalled ffmpeg & reinstalled from the Medibuntu repos
on someone else's advice. 
Still have the same problem with audio.

---

### Post by andrew.46 on 2009-07-25
Hi garyed,

> **garyed said:**
> I had ffmpeg from my original install of Hardy that did the same thing.A few days ago I uninstalled ffmpeg & reinstalled from the Medibuntu repos on someone else's advice. 

OIC, I read that thread and I will admit that I am as stumped as the FakeOutdoorsman. Hopefully you can post this file?nAnother thought would be to try a similar conversion but this time with aac sound. On the svn FFmpeg this would be:

```
ffmpeg -i first.wmv -vcodec flv **[COLOR="Red"]-acodec libfaac[/COLOR]** first.flv
```

but your copy of FFmpeg may very well use a different name for the aac encoder. Run the following to see how it is named:

```

andrew@skamandros~$**[COLOR="Red"] ffmpeg -formats | grep aac[/COLOR]**
FFmpeg version SVN-r19507, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
--prefix=/usr --mandir=/usr/man --disable-debug --enable-shared
 --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis 
--enable-x11grab --enable-libmp3lame --enable-libx264 
--enable-libschroedinger --enable-libfaac --enable-libfaad 
--enable-libopencore-amrnb --enable-libopencore-amrwb 
--enable-version3 --enable-libgsm --enable-libspeex --enable-zlib
 --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jul 25 2009 09:03:14, gcc: 4.2.4
 D  aac             raw ADTS AAC
 DEA    aac             Advanced Audio Coding
  **[COLOR="Red"]EA    libfaac         libfaac AAC (Advanced Audio Codec)[/COLOR]**
 text2movsub remove_extra noise mov2textsub mp3decomp 
mp3comp mjpegadump imxdump h264_mp4toannexb dump_extra aac_adtstoasc

```

And perhaps this one will work :-).

Andrew

---

### Post by garyed on 2009-07-25
I tried aac & it said unknown codec again.
[code]
gary@gary-desktop:~/downloads$ ffmpeg -formats|grep aac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 D  aac             ADTS AAC
[/codec]

---

### Post by SuperSonic4 on 2009-07-25
It seems like you don't have faac on your computer which is needed to encoded to aac

You can always try ```
-acodec libvorbis
``` - since ogg vorbis is free it should be on there.

```
ffmpeg -i first.wmv -vcodec flv -acodec libvorbis first.flv
```

---

### Post by garyed on 2009-07-25
> **SuperSonic4 said:**
> It seems like you don't have faac on your computer which is needed to encoded to aac

You can always try ```
-acodec libvorbis
``` - since ogg vorbis is free it should be on there.

```
ffmpeg -i first.wmv -vcodec flv -acodec libvorbis first.flv
```

I still get unknown codec.
It seems that for some reason its not finding any audio codecs.
Could I completely uninstall ffmpeg & reinstall a newer version?
I'm not sure how to do it but I've been working on this for a few days now.

---

### Post by andrew.46 on 2009-07-25
Hi garyed,

> **garyed said:**
> I tried aac & it said unknown codec again.

```

gary@gary-desktop:~/downloads$ ffmpeg -formats|grep aac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug **[COLOR="Red"]--enable-libmp3lame[/COLOR]** --enable-libfaadbin --enable-libfaad **[COLOR="Red"]--enable-libfaac[/COLOR]** --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 D  aac             ADTS AAC

```

I suspect your copy of FFmpeg is damaged somehow. Your configuration string declares '--enable-libfaac' but does not allow aac encoding also declares '--enable-libmp3lame' and does not allow mp3 encoding. Either that or you have several copies of FFmpeg on your system?

Andrew

---

### Post by mc4man on 2009-07-25
This may have resolved itself either intentionally or inadvertently (thru an update

While I'm in no position on hardy at this point to see, this could be possible - 
if you have the hardy ffmpeg libs installed with or without ffmeg installed, then add medibuntu as a source and install or update ffmpeg it seems possible that that is all that will get updated. 

The ffmpeg libs installed **may** stay the same (hardy repo) but the update manager will show libavcodec1d, ect. with available updates

Looking at the control file in the medibuntu ffmpeg the lib deps are set to the ubuntu repo versions, not medibuntu's

> Package: ffmpeg
Version: 3:0.cvs20070307-5ubuntu7.3+medibuntu1
Architecture: i386
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Installed-Size: 648
Depends: libavcodec1d (>= 0.cvs20070307), libavformat1d (>= 0.cvs20070307), libavutil1d (>= 0.cvs20070307), libc6 (>= 2.7), libfreetype6 (>= 2.3.5), libimlib2, libsdl1.2debian (>= 1.2.10-1), libswscale1d (>= 0.cvs20070307)
Section: graphics


where as medibuntu's libavcodec ver. is 
```
Package: libavcodec1d
Source: ffmpeg
Version: 3:0.cvs20070307-5ubuntu7.3+medibuntu1

```

---

