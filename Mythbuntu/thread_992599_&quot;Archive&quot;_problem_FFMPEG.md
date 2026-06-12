---
title: "&quot;Archive&quot; problem FFMPEG"
date: 2008-11-24
forum: Mythbuntu
---

### Post by jellono on 2008-11-24
I am trying out "Archive" to make a DVD and it is giving me a ffmpeg error..

The original TV program was recorded with a Haupagg 150 mpeg2 Not compressed..

log...

Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 4:3
Re-encoding audio and video
Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_pal.xml
Encoding profile (SP) found
ffmpeg -v 1 -i "/myth/tv/1050_20081124043000.mpg" -r pal -target dvd -b 4771k -s 720x576 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/myth/tmp/work/1/newfile2.mpg" -map 0:0 -map 0:1 
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from '/myth/tv/1050_20081124043000.mpg':
  Duration: 00:29:57.1, start: 0.189267, bitrate: 5186 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Assuming PAL for target.
Unknown encoder 'mpeg2video'
************************************************************
ERROR: Failed while running ffmpeg to re-encode video.
Command was ffmpeg -v 1 -i "/myth/tv/1050_20081124043000.mpg" -r pal -target dvd -b 4771k -s 720x576 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/myth/tmp/work/1/newfile2.mpg" -map 0:0 -map 0:1

---

### Post by dmfrey on 2008-11-25
I ran into this same error.  Here are a few tips that I have on dealing with MythArchive.

To fix your error do the following:
```

sudo apt-get install libavcodec-unstripped-51
libavdevice-unstripped-52 libavutil-unstripped-49
libpostproc-unstripped-51 libswscale-unstripped-0

```
This is documented on LaunchPad in [https://bugs.launchpad.net/medibuntu/+bug/269997](https://bugs.launchpad.net/medibuntu/+bug/269997)


To fix issue with ICE errors when burning to DVD:
```

rm ~/.ICEAuthority

```
I have done some looking but could not find what is actually creating this file.  It comes back every time your reboot so you have to delete it before every MythArchive session after a reboot.

I hope this helps you out.

---

### Post by jellono on 2008-11-30
That was fantastic. The fix worked, I spent 2 days searching for this answer and never found this article.

Dave

---

### Post by johnnysako on 2009-05-09
I had a similar issue on mythbuntu 9.04.  Installing the "unstripped" libraries did not help.

---

### Post by klc5555 on 2009-06-21
Just ran into this "Unknown encoder 'mpeg2video'" error in 9.04, archiving a DVB recording in Mytharchive. The first time I've tried to use mytharchive in 9.04.

"apt-get install"  reports that libavcodec-unstripped-51 can't be found, but installing the remaining four packages (libavdevice-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0) seems to be sufficient to get the job done.

---

### Post by faginbagin on 2009-06-22
That's because the package name in Jaunty is libavcodec-unstripped-52, not 51.

---

### Post by klc5555 on 2009-06-22
> **faginbagin said:**
> That's because the package name in Jaunty is libavcodec-unstripped-52, not 51.

Thanks!

But the main point was that separately installing libavcodec-unstripped-52 (or libavcodec-unstripped-anything) in 9.04 seems to be unnecessary for eliminating the "Unknown encoder 'mpeg2video'" error. It's apparently one, some, or all of the other four 'unstripped' packages that does the trick in 9.04.

Unless the needs of transcoding and archiving output from an analog mpeg2 encoder like a pvr-150 turn out to be different. I've so far only used 9.04's mytharchive on some short dvb recordings. 

Cheers! :)

---

### Post by faginbagin on 2009-06-22
As long as your default recording profile for the PVR-150 is DVD compatible, specifically width & height conform to DVD standards, you should not need to transcode PVR-150 recordings. When mytharchive asks for an encoding profile, choose "Don't re-encode".

HD recordings, on the other hand, do need transcoding to a DVD compatible format.

Have fun!

---

### Post by DrCrispPacket on 2009-08-29
Jauny Mythbuntu: 

installing ***-unstripped-** as described above solved FFMPEG problem, which I had encountered while trying to archive non-myth videos. 

I was trying to produce a DVD containing a mix of recordings consisting of a couple of TV reordings obtained with a DVB card in Myth and a couple of video files downloaded from BBC iPlayer, and it worked a treat after I had performed the fix.

Thanks for the hints.

---

