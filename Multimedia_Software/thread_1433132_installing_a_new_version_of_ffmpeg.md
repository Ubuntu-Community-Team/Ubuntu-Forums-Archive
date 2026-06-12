---
title: "installing a new version of ffmpeg"
date: 2010-03-18
forum: Multimedia Software
---

### Post by Mia1990 on 2010-03-18
Hi,
I am wanting to install a new build of svn ffmpeg here is what i am having some problems with when i go to uninstall ffmpeg libx264 and x264 it is wanting to uninstall some more stuff that i do not want un installed.So is there a way to just uninstall those 3 things and leave eeverything else alone?
Thank you

---

### Post by Yellow Pasque on 2010-03-18
The dirty way to do it would be to overwrite the installed version of ffmpeg by using --prefix=/usr in the configure script of ffmpeg.
Safer/cleaner way would be to use checkinstall to create a .deb and replace it.

---

### Post by hazelnut on 2010-03-18
WARNING

Just posted somthing about this in another thread.

If you compile the latest x264 and ffmpeg you may very well break mplayer and vlc because ffmpeg will try to install some shared libraries like libavcodec and libavformat and some others.

I'm guessing you want an ffmpeg build that can encode with libx264.

Best way, IMO:

Install build dependencies and sources from repositories. Compile from those sources.

I could try to post step-by-step, but I'd be going by memory.  If you have trouble, let me know, I can probably help.  

I think build-dep for ffmpeg is going to complain about wrong versions--it's lying. you have to force the versions for some of the libs.

---

### Post by Mia1990 on 2010-03-19
I have svn ffmpeg working now at first it works great but when i update there is a ffmpeg update that breaks tovid and winff.I used check install to install it.Maybe i should hav just installed it with make install or is there a easier way to stop the update from showing up or installing?

---

### Post by sam.reader on 2010-03-19
I suggest you get CCCP software with regular updates.
It has everything that you need to play different kinds of videos.
X264 and mpeg or mp4 videos play even in Media Player classic without any hiccups.
If you have tried it let me know the result.

---

### Post by Mia1990 on 2010-03-20
New version of svn ffmpeg is working great but i have a question vhooks are disabled and a few other things are as well why and is there a way to get around this?After i install a update to ffmpeg and do a ffmpeg -version this is what i get.

> FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib [COLOR=Red]--disable-stripping --disable-vhook[/COLOR] --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared [COLOR=Red]--disable-static[/COLOR]
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
and this is my configuration when i compile

> ./configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-nonfree --enable-x11grab  --enable-version3 --enable-libopencore-amrnb  --enable-encoder=libx264 --enable-encoder=h264 --enable-swscaleif i put --enable-vhook in there then it will not compile.So do i need any of the things that are disabled?I think there website said they are replacing vhooking with something else.

---

### Post by Yellow Pasque on 2010-03-20
> if i put --enable-vhook in there then it will not compile.
vhook has been replaced by libavfilter. Just make sure you have libavfilter-dev installed.

---

### Post by Yellow Pasque on 2010-03-20
> **Mia1990 said:**
> I have svn ffmpeg working now at first it works great but when i update there is a ffmpeg update that breaks tovid and winff

Instead of updating, use Synaptic to pin/hold the ffmpeg repo updates (under the package menu, there's a 'Lock Version' option).

Or, the old-school way:
```
sudo dpkg hold ffmpeg
```

---

### Post by Mia1990 on 2010-03-20
Ok libavfilter-dev was not installed.Do i need to recompile ffmpeg?I have both tovid and winff working with the update now.

---

### Post by Yellow Pasque on 2010-03-20
> **Mia1990 said:**
> Ok libavfilter-dev was not installed.Do i need to recompile ffmpeg?

Yes.

---

### Post by Mia1990 on 2010-03-20
thank you

---

### Post by Yellow Pasque on 2010-03-20
Aye.

---

