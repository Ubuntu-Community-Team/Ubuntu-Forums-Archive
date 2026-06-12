---
title: "kdenlive: no h.264 output"
date: 2009-10-02
forum: Multimedia Software
---

### Post by barna on 2009-10-02
Hi,
I have kdenlive 0.7.5-1ubuntu1 (kubuntu-9.10), I have installed the 'unstripped' packages:

```

i   libavcodec-unstripped-52                                                   - ffmpeg utility library - transitional package
i   libavdevice-unstripped-52                                                  - ffmpeg utility library - transitional package
i   libavfilter-unstripped-0                                                   - ffmpeg utility library - transitional package
i   libavformat-unstripped-52                                                  - ffmpeg utility library - transitional package
i   libavutil-unstripped-49                                                    - ffmpeg utility library - transitional package
i   libpostproc-unstripped-51                                                  - ffmpeg utility library - transitional package
i   libswscale-unstripped-0                                                    - ffmpeg utility library - transitional package


```

and ffmpeg -formats | grep 264 gives this output

```

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
 DE h264            raw H.264 video format
  E ipod            iPod H.264 MP4 format
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 text2movsub remove_extra noise mov2textsub mp3decomp mp3comp mjpegadump imxdump h264_mp4toannexb dump_extra

```

I have rerun the kdenlive config wizard. Still, all the H.264 output options are grayed out (everything else is available). Why?

Thanks

---

### Post by bumanie on 2009-10-02
Can't help with kdenlive as I have always had it crash on gnome, however ffmpeg will code to h.264. If you want ffmpeg with a gui get [winff]("http://code.google.com/p/winff/wiki/UbuntuInstallation")

---

### Post by barna on 2009-10-03
In the meantime I figured out that bringing the pointer over these disabled rendering profiles, there is a very useful hint, why it is disabled. In my case the reason is: Unsupported audio codec libfaac. So it was not the video codec, but the audio codec, which is problematic.
Creating new rendering profiles, where I just replaced libfaac to libmp3lame allows rendering with h264. 

Probably the missing libfaac codec is due to limitations in the ubuntu-version of ffmpeg: it seems not to have been enabled:

```

Fmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static

```

Are there any suggestions, which audio codec to us when encoding to mp4 with h264 vcodec? To have a portable file, which will play on all systems?

---

### Post by FakeOutdoorsman on 2009-10-04
> **barna said:**
> Probably the missing libfaac codec is due to limitations in the ubuntu-version of ffmpeg: it seems not to have been enabled

This is correct.  Ubuntu (or may be it was Debian) developers have removed libfaac from FFmpeg due to it not actually being LGPL as it claimed.  Ubuntu has not given users any alternative, although FFmpeg can now encode to AAC natively.  I'm not sure if the repository version is too old for native AAC encoding, or if they did not enable it for some reason because I do not believe it is "non-free" as libfaac.  Right now on 9.10 you will need to compile to encode to AAC with FFmpeg.  The following guide should work, but I have yet to do any actual testing on 9.10:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by limathebest on 2009-10-17
So, summing up the moment we can not encode videos in Kdenlive using Ubuntu 9.10 format h264 !

---

### Post by barna on 2009-10-17
to overcome this problem, one can add other rendering profiles:
1) click on one of the predefined rendering profiles in the H.264 group
2) click the 'Create new profile' button
3) Give it a name, and replace acodec=libfaac to acodec=libmp3lame
This will then render with mp3+h264

---

### Post by limathebest on 2009-10-17
Very good with it my problem is over. Now it's so repeat this process to obtain the expected result. Thank you

---

### Post by cor2y on 2009-11-05
Anyone know why kdenlive will not render using ffmpeg's built in aac encoder since libfaac is now persona nongrata ?

---

### Post by FakeOutdoorsman on 2009-11-05
> **cor2y said:**
> Anyone know why kdenlive will not render using ffmpeg's built in aac encoder since libfaac is now persona nongrata ?

The native AAC encoder in more recent FFmpeg is not available in the Karmic FFmpeg.  Ubuntu chose to use a FFmpeg revision a few days before the native AAC encoder was released.

---

### Post by barna on 2009-11-06
If you do want to have AAC, you need to recompile the ffmpeg-extra packages (libraries). 
1) install libfaac-dev or whatever
2) install the dependencies of ffmpeg-extra: 
   ```
sudo apt-get build-dep ffmpeg-extra
```
3) get the source of ffmpeg-extra: 
   ```
apt-get source ffmpeg-extra
```
4) build it: 
   ```
cd ffmpeg-*; debuild -us -uc
```
   now there should be *-extra.deb files in the parent directory. 
   These are the 'extra' libraries of ffmpeg 
   (old naming scheme: -unstripped), with non-limited functionality
5) install them: 
   ```
cd ..; sudo dpkg -i *.deb 
```
   I think libavcodec-extra-52 contains the aac codec (it might be
   something else, though, check), so it is sufficient to install only
   libavcodec-extra-52. If you have the stripped libraries installed,
   install all of these -extra packages. The stripped ones will
   automatically be removed, since they conflict with the extra ones

---

### Post by cor2y on 2009-11-06
Argh, they should really have a clear tutorial on building individual libraries yourself.
Seems ffmpeg-extra will definitely replace some libraries i built/installed myself in particular libx264 with the repo version sure i can overwrite it by installing it again but you can never tell what conflict you might run into.

Thanks for the info barna.
Initially i tried just compiling svn ffmpeg again and compiling svn kdenlive (0.7.7) from source aac was listed in the H.264 profiles but i got the error that the codec was not recognized meaning even though via normal ffmpeg i could invoke the built in aac encoder with "acodec aac" and have it encode kdenlive just didnt see it.
Finally the built in encoder needs work or you need a different set of settings to make the encoded files sound nice, i did a test between that and libfaac and libfaac to my ears at least sounded better, using the same settings "-ac 2 -ab 128k" built in acc had a sort of echo quality that didnt sound good.

---

### Post by FakeOutdoorsman on 2009-11-06
> **cor2y said:**
> Argh, they should really have a clear tutorial on building individual libraries yourself.
Seems ffmpeg-extra will definitely replace some libraries i built/installed myself in particular libx264 with the repo version sure i can overwrite it by installing it again but you can never tell what conflict you might run into.

Thanks for the info barna.
Initially i tried just compiling svn ffmpeg again and compiling svn kdenlive (0.7.7) from source aac was listed in the H.264 profiles but i got the error that the codec was not recognized meaning even though via normal ffmpeg i could invoke the built in aac encoder with "acodec aac" and have it encode kdenlive just didnt see it.
Finally the built in encoder needs work or you need a different set of settings to make the encoded files sound nice, i did a test between that and libfaac and libfaac to my ears at least sounded better, using the same settings "-ac 2 -ab 128k" built in acc had a sort of echo quality that didnt sound good.

I haven't personally compared the quality of the native AAC encoder and libfaac, but some people have told me that it usually doesn't sound as good as libfaac, and then others say that libfaac doesn't sound as good as neroaacenc.  I'm not sure what is true and what is opinion.

---

### Post by barna on 2009-11-06
> **cor2y said:**
> 
Initially i tried just compiling svn ffmpeg again and compiling svn kdenlive (0.7.7) from source aac was listed in the H.264 profiles but i got the error that the codec was not recognized meaning even though via normal ffmpeg i could invoke the built in aac encoder with "acodec aac" and have it encode kdenlive just didnt see it.
Finally the built in encoder needs work or you need a different set of settings to make the encoded files sound nice, i did a test between that and libfaac and libfaac to my ears at least sounded better, using the same settings "-ac 2 -ab 128k" built in acc had a sort of echo quality that didnt sound good.

This below is just a guess, so please verify it yourself: the kdenlive h.264 rendering profile with AAC sound uses acodec=libfaac, whereas you verified that acodec=aac (built-in encoder?) is working. Either change the rendering profile (I think you can not change the predefined profile in kdenlive, but you can click on it, then click on 'Create new profile', which creates a new profile based on the selected one, and then change the option acodec=libfaac to acodec=aac), or recompile ffmpeg-extra as suggested. BTW I did this latter, and then I could render with the predefined h.264 profile, but now somehow the libfaac encoder disappeared from my ffmpeg... I need to verify, why.

---

### Post by cor2y on 2009-11-06
No go barna.
The profiles for H.264 like i said in version 0.7.7 svn now uses aac instead of libfaac however it doesnt see aac within my compiled version of ffmpeg.
Creating a new profile and using libfaac didnt work , what did work was the workaround of using "acodec=libmp3lame" but i dont want mp3 audio.

FakeOutdoorsman all i can say is aac really really doesnt hold a candle to libfaac, i havent used Nero's aac encoder myself but i have tried aacencplus and i can say at the same default setting of like what i used with libfaac my ears at least couldnt tell the difference between an aacencplus file and one encoded with libfaac. People who really dig into the settings and use different profiles probably can. I just use aac for encoding audio tracks to H.264 mp4/mkv  and not for ripping music cds so its always at that default setting of -ac 2 -ab 128k..

---

### Post by paul.gevers on 2009-11-06
> **cor2y said:**
> all i can say is aac really really doesnt hold a candle to libfaac,

I believe even upstream thinks so, see:[bug 412063 comment 6]("http://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/412063/comments/6").

---

### Post by cor2y on 2009-11-07
Well i finally got kdenlive to recognize aac encoder in ffmpeg.
I had to install ffmpeg with --enable-shared output using aac is not good.
I already knew this using ffmpeg but i was hoping there was some tweaks that could have been done within kdenlive or maybe although the codec was listed as aac it was still using libfaac.

---

### Post by uhappo on 2009-12-15
> **barna said:**
> to overcome this problem, one can add other rendering profiles:
1) click on one of the predefined rendering profiles in the H.264 group
2) click the 'Create new profile' button
3) Give it a name, and replace acodec=libfaac to acodec=libmp3lame
This will then render with mp3+h264

Thanks!!! I'm on ubuntu, but anyway, this works!

---

### Post by GrouchyGaijin on 2013-01-03
> **uhappo said:**
> Thanks!!! I'm on ubuntu, but anyway, this works!

I'm on Ubuntu as well (12.04) I have kdenlive from their (kden's) repository installed

[B]Kdenlive
Version 0.9.2
Using KDE Development Platform 4.8.5 (4.8.5)[/B]

 as well as the dev version of ffmpeg.

```
ffmpeg version git-2013-01-02-e4f14c3 Copyright (c) 2000-2013 the FFmpeg developers
  built on Jan  2 2013 18:16:31 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 13.100 / 52. 13.100
  libavcodec     54. 85.100 / 54. 85.100
  libavformat    54. 59.100 / 54. 59.100
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 30.102 /  3. 30.102
  libswscale      2.  1.103 /  2.  1.103
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100

```

libx264 is set as enabled

I might be misunderstanding this thread, but my problem is not audio; it's video.  I tried swapping out aac for acodec=libmp3lame and as I thought this didn't affect anything.  I can render a file, but when I play it I only hear the audio.  I don't see any video.

I've had this problem for a long time, even before I installed the dev version of ffmpeg.

Any ideas on how to solve this?

---

### Post by oldos2er on 2013-01-03
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

