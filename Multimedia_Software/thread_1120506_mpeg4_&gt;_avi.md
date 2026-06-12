---
title: "mpeg4 &gt; avi?"
date: 2009-04-09
forum: Multimedia Software
---

### Post by chris_andrew on 2009-04-09
Hi,

I have a couple of files that are in mpeg4 format, and I want to be able to play them on my Archos (portable multimedia player).  

I need to convert the files to AVI.  Can anyone recommend an app that could do this job for me?

Many thanks,

Chris.

---

### Post by aquavitae on 2009-04-09
The last time I did this was a few years ago, so there might be something better, but I'd use either transcode or mencoder (part of mplayer).  Both are fairly complicated command line apps, but I'm sure there are some good frontends for them - a google search, or even just a synaptic search should bring something up.

Hope this helps!

---

### Post by inobe on 2009-04-09
avidemux will do it, also handbrake.

---

### Post by MaraMax on 2009-04-09
I use Hyper Video Converter ([http://gtk-apps.org/content/show.php/Hyper+Video+Converter?content=88970](http://gtk-apps.org/content/show.php/Hyper+Video+Converter?content=88970)), a frontend to ffmpeg and mencoder.

Usefull

There's a qt version too.

---

### Post by cotcot on 2009-04-09
[[COLOR="Red"]Handbrake[/COLOR]]("http://filthypants.blogspot.com/2009/03/new-directions-for-building-handbrake.html") can do this. It is not in the repos. You need to compile it.

ffmpeg or mencoder in command line is also possible.

---

### Post by chris_andrew on 2009-04-09
Thanks, all.

I am happy to compile, but would rather use a package from the repo, so that updates are easily applied.

Cheers,

Chris.

---

### Post by chris_andrew on 2009-04-09
BTW, I use xfce, so would prefer not to drag-in loads of QT dependencies ;-)

Chris.

---

### Post by Cresho on 2009-04-09
winff with medibuntu can do this.  Also, try windows version of winff under wine if you are having issues with conversion.

---

### Post by andrew.46 on 2009-04-09
Hi chris,

> **chris_andrew said:**
> I am happy to compile, but would rather use a package from the repo, so that updates are easily applied.

The best tool for this job would be FFmpeg and it is not that hard to use. If you are interested have a look at the Fakeoutdoorsman's new page which describes the FFmpeg options under Ubuntu:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then run FFmpeg across one of the mp4 files as follows:

```
ffmpeg -i myfile
```

and if you post the results here I am sure that the correct syntax can be suggested to you. BTW do you have an idea of what audio and video limitations this player has?

All the best,

Andrew

---

### Post by chris_andrew on 2009-04-09
The command output on this screenshot looks encouraging.

Chris.

---

### Post by chris_andrew on 2009-04-09
I did 

```
ffmpeg -i "filename" -f avi -vcodec libxvid -qscale 4 -acodec libmp3lame "newfilename"
```

and got
```

ffmpeg -i "filename" -f avi -vcodec libxvid -qscale 4 -acodec libmp3lame "newfilename"
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
[mpeg4 @ 0x7f20b89cf900]frame skip 8
[mpeg4 @ 0x7f20b89cf900]frame skip 8
Input #0, avi, from 'filename':
  Duration: 00:38:13.8, start: 0.000000, bitrate: 892 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: liba52, 44100 Hz, stereo, 192 kb/s
Unknown encoder 'libxvid'
```

dpkg -l | grep -i libxvid

```
ii  libxvidcore4                               2:1.1.2-0.1ubuntu3                      High quality ISO MPEG4 codec library
```

indicating that libxvid is installed.

Can anyone tell me where I'm going wrong?

Thanks,

Chris.

---

### Post by chris_andrew on 2009-04-09
Can anyone help?

---

### Post by paul.gevers on 2009-04-09
> **chris_andrew said:**
> 
```

Unknown encoder 'libxvid'
```

```
ii  libxvidcore4                               2:1.1.2-0.1ubuntu3                      High quality ISO MPEG4 codec library
```

indicating that libxvid is installed.


ffmpeg does not need any extended libraries to be installed. I think you are running Intrepid, you can install libavcodec-unstripped-51. For Hardy you can see the medibuntu repositories for an unstripped version of ffmpeg. (The standard ffmpeg does not include all codecs available due to legal issues.)

---

### Post by andrew.46 on 2009-04-09
Hi chris,

> **chris_andrew said:**
> 
  Duration: 00:38:13.8, start: 0.000000, bitrate: 892 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: liba52, 44100 Hz, stereo, 192 kb/s
Unknown encoder 'libxvid'[/CODE]

As Paul has suggested you need to uncripple your copy of FFmpeg. Ubuntu has a policy of distributing FFmpeg with a few pieces missing as the Fakeoutdoorsman explains [at length]("http://ubuntuforums.org/showthread.php?t=1117283").

However I note that the original clip already has mpeg4 video so I suspect there is no need to re-encode it. Once you have an uncrippled copy of FFmpeg you could try:

```
ffmpeg -i input -vcodec copy -acodec libmp3lame -ab 128k output.avi
```

and this might very well be enough for your player. If the player balks at this you could try altering the ffourcc by adding:

```
-vtag XVID
```

into the syntax. All the best with this!

Andrew

---

### Post by Cresho on 2009-04-09
You are getting this error because you need medibuntu.  If you have wine installed with windows version of winff and not winff for linux, you will not see these errors. 

Install medibuntu to remove these errors or build an ffmpeg with all options enabled.  Most of the guys before my post have given great examples of where to get the medibuntu install.

---

### Post by FakeOutdoorsman on 2009-04-09
> **Cresho said:**
> You are getting this error because you need medibuntu.  If you have wine installed with windows version of winff and not winff for linux, you will not see these errors. 

Install medibuntu to remove these errors or build an ffmpeg with all options enabled.  Most of the guys before my post have given great examples of where to get the medibuntu install.

The original poster is using Intrepid according to the FFmpeg information.  Enabling Medibuntu will not resolve this issue because it has no relevant packages.  However, some Ubuntu releases prior to Hardy will benefit from Medibuntu as it contains a non-crippled version of FFmpeg.

---

### Post by Cresho on 2009-04-09
I guess he will be running this then

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)


Is jaunty jackelope going to have a crippled ffmpeg as well?  if so, then i wont be upgrading from hardy heron.  I have been working on alot of video editing and converting with my current os and Don't want it broken for any reason.  Building and enabling from source would be easy as long as I can find the packages necessery.

---

### Post by FakeOutdoorsman on 2009-04-09
> **Cresho said:**
> I guess he will be running this then

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)


Is jaunty jackelope going to have a crippled ffmpeg as well?
By default, yes, but you can quickly enable the restricted encoders as described in that link you mentioned.

> Building and enabling from source would be easy as long as I can find the packages necessery.

Refer to [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095) for a complete description.

---

### Post by michaelzap on 2009-04-09
There are Handbrake deb files [here]("http://handbrake.fr/?article=download") and on getdeb.net. No need to compile (it even runs fine on my 64-bit Jaunty beta system). Avidemux is also an excellent GUI convertor, as is WinFF.

---

### Post by Cresho on 2009-04-10
Thanks for that info FakeOutdoorsman.

---

