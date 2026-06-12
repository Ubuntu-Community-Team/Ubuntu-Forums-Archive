---
title: "Audacity Not Recognizing FFmpeg"
date: 2010-01-17
forum: Multimedia Software
---

### Post by DjTeriyake on 2010-01-17
I installed Audacity to convert an mp4 to an mp3. Now, I don't necessarily need Audacity to do this, but for the time being I'm more concerned with getting Audacity to work properly as opposed to getting an mp3 onto my iPod.

In Audacity, I went to _**E_dit>Pre_f_erences>Libraries**. For the **MP3 Export Library**, Audacity recognizes LAME, but under the **FFmpeg Import/Export Library** it says "**FFmpeg library not found**." I hit the **_D_ownload** button and read _[this page]("http://manual.audacityteam.org/index.php?title=FAQ:Installation_and_Plug-Ins#installffmpeg")_ on how to install FFmpeg, noticing the warning about needing FFmpeg 0.5 or later on Linux.

I fired up Synaptic and searched for "ffmpeg," chose the vanilla version and installed it along with two dependencies which I don't exactly remember but I bet they were libavformat52 and libavdevice52.

Back in the Audacity Preferences window I chose the "**_L_ocate...**" button to point to the newly installed libraries, but Audacity is not recognizing/installing them successfully. I've tried pointing to the following files:

/usr/lib/libavformat.so.52
/usr/lib/libavformat.so.52.36.0
/usr/lib/i686/cmov/libavformat.so.52
/usr/lib/i686/cmov/libavformat.so.52.36.0
/usr/share/lintian/overrides/libavformat52

Back in Synaptic, I searched for "libavformat" and got the following results:
libavformat-dev
libavformat-extra-52
**libavformat52**  *this is the one that's installed
libavformat-unstripped-52
libdlna0
libdlna-dev

Did I install the wrong version of FFmpeg or libavformat? Any pointers?

---

### Post by mc4man on 2010-01-18
> Did I install the wrong version of FFmpeg or libavformat?
Those version numbers are not from ubnutu, and audacity seems to want a specic version. ( the one provided by whatever ubuntu release you're using.

as it happens jaunty thru the current lucid all use the same version #'s ( though juanty uses an earlier ffmpeg release. (0.5 actually

libavformat.so.52.[COLOR="Red"]31.[/COLOR]0
libavcodec.so.52.[COLOR="Red"]20[/COLOR].0
libavutil.so.49.[COLOR="Red"]15[/COLOR].0

As seen [here ]("http://packages.ubuntu.com/karmic/libavformat52/filelist")

( I have non standard ffmpeg libs on this install here. will edit a screen from stock install that audacity will accept


Maybe run just this and post
```
ffmpeg
```

You're going to need to get the shared ffmpeg libs from whatever ubuntu you're using installed
Do you have a ppa or did you build ffmpeg as 'shared'?

edit
screen shows audacity from lucid ( lucid uses the same ffmpeg libs as karmic


As a comparison these are the shared ffmpeg libs on my karmic install - but I built and installed myself  in early oct. - audacity **will not accept** them


> doug@doug-desktop:~$ ffmpeg
FFmpeg version SVN-r20130, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Oct  5 2009 02:22:32 with gcc 4.4.1
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg 
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0


---

### Post by DjTeriyake on 2010-01-18
> **mc4man said:**
> Those version numbers are not from ubnutu, and audacity seems to want a specic version...You're going to need to get the shared ffmpeg libs from whatever ubuntu you're using installed
Do you have a ppa or did you build ffmpeg as 'shared'?

I installed ffmpeg from ppa. On first installing Karmic I followed an online guide that recommended adding quite a bit of extra repositories. I always figured that this would come back to bite me, but did it anyway. I guess this the scenario I was anticipating?


> Maybe run just this and post
```
ffmpeg
```

Here's the output from "ffmpeg:"
```
DjTeriyake@ubuntu:~$ ffmpeg
FFmpeg version SVN-r19468, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g '
--cc='ccache cc' --libdir='${prefix}/lib' 
--shlibdir='${prefix}/lib' --bindir='${prefix}/bin' 
--incdir='${prefix}/include/ffmpeg' --enable-shared --enable-
ibmp3lame --enable-gpl --enable-libfaad 
-mandir='${prefix}/share/man' --enable-libvorbis --enable-
pthreads --enable-libfaac --enable-libxvid --enable-postproc 
--enable-x11grab --enable-libgsm --enable-libopencore-amrnb
--enable-libopencore-amrwb --enable-libx264 --enable-libtheora
--enable-libdc1394 --enable-libspeex --enable-nonfree --disable-
stripping --enable-avfilter --enable-libdirac --disable-
decoder=libdirac --enable-libschroedinger --disable-
encoder=libschroedinger --enable-avfilter-lavf --enable-
libopenjpeg --enable-version3 --disable-altivec --disable-
armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov 16 2009 20:35:59, gcc: 4.4.1
At least one output file must be specified
```

At least I now know what type of problem I'm facing - that of specific library versions expected. Thanks.

---

### Post by mc4man on 2010-01-18
> I guess this the scenario I was anticipating?
There is always a risk when updating shared libraries from outside ubuntu repos that you may see some regressions (though can be done if looked at carefully

With the ffmpeg libs one needs to be very careful, and while there can be something to gain, it may not out weigh a loss on a local level


The other danger when enabling ppa's is if they are left enabled and you do an update thru the update manager or worse, apt-get, you may update some things you had no intention of updating 
(depending on what's available on the enabled ppa's

What you could do, though it may involve temporarily removing some apps/libs, is to disable your ppa's.

Then add the karmic medibuntu repo which has redone ffmpeg libs (same version as karmic) with aac encoding enabled.

Then remove all your ffmpeg libs (noting what else is removed) and then re- install using the now available ones from medibuntu (edit - you want the 'extra' versions

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If for any reason you have a need for a current ffmpeg itself then use this guide to build and install a **static** ffmpeg, it will not cause you any issues with apps that depend (use) the shared libs

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by DjTeriyake on 2010-01-20
Everything works now. Thanks for the guidance **mc4man**.

In going about your recommendations I realized that I was unsure as to what a PPA is besides a software source, and now I need to read up on how to manage them so I don't create problems with my installation as I had done with this Audacity/ffmpeg issue.

Here's the sequence of things that I did:

=====================================================

Opened up Synaptic's software sources and noted the repositories. Here's a screenshot of the configuration at that time:

[[IMG]http://i268.photobucket.com/albums/jj26/pauljohnb/UbuntuLinux910KarmicSynapticSoft-3.gif[/IMG]]("http://i268.photobucket.com/albums/jj26/pauljohnb/UbuntuLinux910KarmicSynapticSoft-1.gif")

Through Synaptic, removed **libavformat.so.52**. The following was also removed by Synaptic:

[B]gimp-plugin-registry
gstreamer0.10-ffmpeg
libavdevice52
libcv1
libcvaux1
libhighgui1
mencoder
mplayer-nogui
vlc
vlc-nox
vlc-plugin-pulse[/B]

Added the Medibuntu repository to Synaptic's software sources via _[the link]("https://help.ubuntu.com/community/Medibuntu")_ provided by **mc4man**.

Upon choosing to install the **libavformat-extra-52** package from the Medibuntu repository the following was removed by Synaptic...:

[B]libavcodec52
libavfilter0
libavutil49[/B]

...and the following was installed alongside:

[B]libammb3
libamrwb3
libavcodec-extra-52
libavformat-extra-52
libavutil-extra-49[/B]

Audacity was then started, and it found the correct ffmpeg libraries automatically. The original mp4 file to be edited was successfully imported and played, then exported as an mp3. However, upon testing the newly created mp3, the following was noted:

-Mp3s had no sound in multimedia software, though the sound worked correctly when opened with Audacity
-YouTube and other browser multimedia had no sound
-The original mp4 file, when opened in "Movie Player" (I think it's totem) had no sound. Movie Player said the plugin "**gstreamer0.10-ffmpeg**" was needed (which was one of the packages removed when **libavformat.so.52** was removed)

Reinstalled "**gstreamer0.10-ffmpeg**" via Synaptic, from the "*Ubuntu Developers*" maintainer. Re-tested various files:

-Mp4 played & showed picture, but still didn't have sound
-Mp3s still had no sound
-YouTube and other browser multimedia still had no sound

The remainder of the packages removed by Synaptic except VLC were then reinstalled (maintainer given in parentheses) in hopes to fix the issue of no sound:

[B]gimp-plugin-registry  (*Ubuntu Developers*)
libavdevice52         (*Ubuntu Core Developers*)
libcv1                (*Ubuntu Developers*)
libcvaux1             (*Ubuntu Developers*)
libhighgui1           (*Ubuntu Developers*)
mencoder              (*Ubuntu MOTU Developers*)
mplayer-nogui         (*Ubuntu MOTU Developers*)[/B]

Restarted and sound works on mp4, mp3, YouTube, etc. Reinstalled VLC via software center.

=====================================================

Everything is working normally now, including the importing of mp4 files by Audacity. Essentially I think this was an issue of conflicting repositories, and I've left most of the PPA repositories unchecked, as seen in the following Synaptic sources screenshot of my current configuration:

[[IMG]http://i268.photobucket.com/albums/jj26/pauljohnb/UbuntuLinux910KarmicSynapticSoft-3.gif[/IMG]]("http://i268.photobucket.com/albums/jj26/pauljohnb/UbuntuLinux910KarmicSynapticSoftwar.gif")

I don't want to ask any long follow up questions about PPAs and the proper maintenance thereof, because this central issue in this thread is solved and I don't want to go off topic, but can anyone recommend any quick rules to follow or links to read concerning PPA management?

---

