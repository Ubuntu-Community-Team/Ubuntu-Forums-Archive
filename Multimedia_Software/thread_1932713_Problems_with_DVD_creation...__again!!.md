---
title: "Problems with DVD creation...  again!!"
date: 2012-02-27
forum: Multimedia Software
---

### Post by dkolars on 2012-02-27
Have .MTS files from Canon camcorder... converted them to .avi files.  Edited, appended, etc. to make 2 files.

Want to make a DVD with menu, and have used DeVeDe to create the menu...  but, now I have to burn it with some other program...  So, tried to use Brasero to create the disc, but it hangs up...  Initially it would not even recognize the .avi as a valid format, but I did some hunting and found the libraries that it was missing (!), and then it would try to write it, but hangs up about 29 Mb into the process...

So, thought I'd convert the .avi to .mp4 or .wmv using WinFF... get the following error messages:

.wmv:
> FFmpeg version 0.6.4-4:0.6.4-0ubuntu0.11.04.1, Copyright (c) 2000-2010 the Libav developers
  built on Jan  4 2012 16:09:40 with gcc 4.5.2
  configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (30000/1001)
Input #0, avi, from '/media/HD3/0Videos/Wacky Keys/Sandburg 2-25-12/Set1.avi':
  Duration: 00:47:05.12, start: 0.000000, bitrate: 1178 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 fps, 29.97 tbr, 29.97 tbn, 2997 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
[wmv2 @ 0x96706d0]multi threaded encoding not supported by codec
Output #0, asf, to '/media/HD3/0Videos/Wacky Keys/Sandburg 2-25-12/Set1.wmv':
    Stream #0.0: Video: wmv2, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: wmav2, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
FFmpeg version 0.6.4-4:0.6.4-0ubuntu0.11.04.1, Copyright (c) 2000-2010 the Libav developers
  built on Jan  4 2012 16:09:40 with gcc 4.5.2
  configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cphttp://switchboard.intelius.com/udetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mp3 @ 0x9c6f830]big_values too big

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (30000/1001)
Input #0, avi, from '/media/HD3/0Videos/Wacky Keys/Sandburg 2-25-12/Set2.avi':
  Duration: 00:39:47.68, start: 0.000000, bitrate: 1118 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 fps, 29.97 tbr, 29.97 tbn, 2997 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 32 kb/s
[wmv2 @ 0x9cc7100]multi threaded encoding not supported by codec
Output #0, asf, to '/media/HD3/0Videos/Wacky Keys/Sandburg 2-25-12/Set2.wmv':
    Stream #0.0: Video: wmv2, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: wmav2, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


Similar stuff for .mp4...  

Is there NOT a _single program_ that will encode and burn a DVD?  And why are these programs incomplete?  I spend waaay too much time hunting stuff down and not getting any work done!!  I long for a program that will do this... Windows has MANY such choices... one would think that they would also exist for Ubuntu/Linux???  I'm seriously tempted to buy a Windows disk and have it available just to be able to do tasks like this in an efficient manner...

Suggestions?

---

### Post by Paddy Landau on 2012-02-28
I have used [ManDVD]("https://sourceforge.net/projects/csgib/"). Very simple to use, although the UI is not entirely intuitive.

It used to be in the repositories (up to Maverick, I believe), but no longer is. You'll have to search for .deb -- I believe it is available but I wouldn't know where. Have a look at [2ManDVD]("http://www.ubuntuupdates.org/package/getdeb_apps/oneiric/apps/getdeb/2mandvd").

---

### Post by Dale61 on 2012-02-28
Search the Software Centre and install a program called DVDStyler.

This will convert (transcode) most formats to DVD, and it also allows you to create menus as well as adding a sound clip to said menu.

---

### Post by Randymanme on 2012-03-01
I'm having the same problem.  I'm installing DVDStyler now.  But just for the record, am I to assume that Brasero just plain doesn't work?

Brasero looks like it would be just fine for noobie-me -- if it worked.  What can I do to make it work.  Are there some dependencies I need to add?

As always, thanks for any feedback.

---

### Post by Dale61 on 2012-03-01
If, for any reason, you have a problem with DVDStyler, there is a forum available.  This is like a help section, but the answers are supplied by the developers.

---

### Post by MartyBuntu on 2012-03-01
Bite the bullet and accept the KDE libs while you install **K3B**.

Brasero is just plain horrible. The only thing it doesn't completely fall on it's face on is ISO burning.

---

### Post by dantonrenato on 2012-11-03
dvdstyler closes on Ubuntu 12.04

I'm puting together a project in dvdstyler on Ubuntu 12.04.
Ubuntu is update with n-vidia and ffmpeg.
I ride with the project videos edited in 16x9.
Use videos to m2v and ac3 audio. Dvdstyler 2.1 recognizes the files ans links them up.
Hence behest generate the ISO image. At that time appear a few lines of programming - and then the program closes. Dvdstyler crash.
The samens happens if I use mov files.
I need help! Thanks!

---

### Post by Dale61 on 2012-11-03
> **dantonrenato said:**
> dvdstyler closes on Ubuntu 12.04

I'm puting together a project in dvdstyler on Ubuntu 12.04.
Ubuntu is update with n-vidia and ffmpeg.
I ride with the project videos edited in 16x9.
Use videos to m2v and ac3 audio. Dvdstyler 2.1 recognizes the files ans links them up.
Hence behest generate the ISO image. At that time appear a few lines of programming - and then the program closes. Dvdstyler crash.
The samens happens if I use mov files.
I need help! Thanks!

Sounds like something similar that I encountered, so try this.

Open DVDStyler.
Click on Configuration > Settings.
Click on Core.
Find the Thread Count setting.  As I use a quad core CPU, I had to change my setting to 4.  Change yours to match the number of cores your CPU has.  If you don't know, start at two and work your way up from there.

However, as I now no longer require to create a DVD as we get our movies in a digital format (mkv, avi, flv, mp4, etc), any updates to the program since I last used it may have overridden any adjustments I've made.

Still, there's no harm in trying!

---

### Post by antti64 on 2012-11-04
I just yesterday met the problem with DVDstyler v2.1. If you create a DVD menu with background music the DVD disc doesn't work at DVD player. The created DVD menu is non-functional. You cannot enter to chapters. If I am correct this seems to be a bug in Ubuntu 12.04 and DVDStyler v2.1. 
 [https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1049113]("https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1049113")

I tried to compile DVDStyler source codes v2.3 but I cannot solve this in Ubuntu 12.04:

```
configure: error: Package requirements (libavformat >= 53.20.0 libavcodec >= 53.34.0 libavutil libswscale libavfilter >= 2.15.0) were not met:

No package 'libavformat' found
No package 'libavcodec' found
No package 'libavutil' found
No package 'libswscale' found
No package 'libavfilter' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBAV_CFLAGS
and LIBAV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Any help to above or workarounds?

Thanks, 

Antti

---

### Post by dantonrenato on 2012-11-06
I installed Ubuntu 12.10. Update, installed packages, all right.
But the DVDStyler is having the same problem.
Both Ubuntu 12.04 and 12.10 in the version of Dvdstyler is the same: 2.1
But now there is a new version of it.
How to install the new version from the terminal?
Tahnks.

---

