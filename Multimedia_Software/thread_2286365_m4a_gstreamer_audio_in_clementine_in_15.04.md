---
title: "m4a gstreamer audio in clementine in 15.04"
date: 2015-07-11
forum: Multimedia Software
---

### Post by neltnerb on 2015-07-11
I recently installed Ubuntu 15.04 on a new computer with Clementine. It plays mp3 and flac fine, but complains that gstreamer is missing for some m4a audio files. In previous versions I could fix this by installing gstreamer0.10-plugins-bad or similar, but these are installed and it is still not working. Does anyone know how to get gstreamer to properly work with .m4a audio files?

---

### Post by blm-ubunet on 2015-07-11
14.04 can have both gstreamer-0.1 & 1.0 installed at same time.
FWIU Clementine from devs nightly ppa requires gstreamer-1.0.
This has problems with wma & m4a again.. 
Clementine crashes when gstreamer1.0 chokes on certain wma files.
(Even the windows build has similar problems)

You can test & compare with old gstreamer (from cmd line) with :
```
gst-launch-0.10 playbin uri=file:///home/johndoe/my-random-media-file.m4a
gst-launch-1.0 playbin uri=file:///home/johndoe/my-random-media-file.m4a
```
and so at least find some debugging clues in the std-out..

I doubt it is possible to force clementine to use the old gstreamer.
Options are:
- transcode with ffmpeg etc
- play with ffplay or gst-launch-0.10
- find something else..

---

### Post by neltnerb on 2015-07-11
Curious. With gst-launch-0.10, it fails to play.

```

Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
** Message: don't know how to handle audio/x-alac, codec_data=(buffer)00000024616c616300000000000010000010280a0e0200ff000028ae0007ee4e0000ac44, samplesize=(int)16, rate=(int)44100, channels=(int)2
Missing element: Apple Lossless Audio (ALAC) decoder
ERROR: from element /GstPlayBin:playbin0: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
Additional debug info:
gstplaybasebin.c(2323): prepare_output (): /GstPlayBin:playbin0
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

```

With gst-launch-1.0 it works fine. So I guess that means that gstreamer-1.0 works fine, but gstreamer-0.10 doesn't work and Clementine is using the 0.10 version.

---

### Post by neltnerb on 2015-07-11
Okay, I've confirmed that the issue is that Clementine 1.2.3 uses gstreamer0.10, and that Ubuntu removed the gstreamer0.10-ffmpeg package from the distribution in the last few releases (which is the one used to decode apple lossless audio).

I was able to use this PPA to reinstall the ffmpeg plugin and now it works fine.

```
sudo add-apt-repository ppa:mc3man/gstffmpeg-keep
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

(Source: [http://askubuntu.com/questions/575869/how-do-i-install-gstreamer0-10-ffmpeg-on-ubuntu-14-10]("http://askubuntu.com/questions/575869/how-do-i-install-gstreamer0-10-ffmpeg-on-ubuntu-14-10"))

---

### Post by mc4man on 2015-07-11
Your other choice would be to use the dev ppa for clementine which finally has moved clementine to gsteamer1.0, then you'd get support for .m4a, wma thru the gstreamer1.0-libav plugin. Clementine has taken a long time to move to gst 1.0 & apparently only thru the ppa as it's still on 0.10 in 15.10 & Debian sid though it's next release will be on gst-1.0

[https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine-dev](https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine-dev)

next release change log - [https://raw.githubusercontent.com/clementine-player/Clementine/master/Changelog](https://raw.githubusercontent.com/clementine-player/Clementine/master/Changelog)

---

### Post by neltnerb on 2015-07-11
Glad to hear, I didn't see any indication of gstreamer 1.0 support in clementine. I think for now it's working well enough, but glad to know I won't have to find yet another amarok clone for 15.10!

---

### Post by blm-ubunet on 2015-07-11
@neltnerb
I think your soln is best. None of my old wma files have ever played in latest clementine/gststreamer-1.0 & that's with mc4man's ppa build of gstreamer1.0-libav.

I didn't know about "gstffmpeg-keep" package & did not realize the std packaged release version of clementine was so old. This turns out to be a good thing.

---

### Post by mc4man on 2015-07-11
15.10 may still use the clem w/ 0.10 gst., if that's the case i'll add 15.10 to the gstffmpeg-keep ppa. As of now it does use 0.10

---

### Post by dave231 on 2016-04-06
mc4man, pretty new to ubuntu so pardon my ignorance.
Running 15.10 on an intel nuc, the follow fails to fetch on sudo apt-get update:

/dist/wily/main/binary-amd64/Packages
/dist/wily/main/binary-i386/Packages

It is then unable to locate package gstreamer0.10-ffmpeg

Any thoughts?

---

### Post by mc4man on 2016-04-06
> **dave231 said:**
> mc4man, pretty new to ubuntu so pardon my ignorance.
Running 15.10 on an intel nuc, the follow fails to fetch on sudo apt-get update:

/dist/wily/main/binary-amd64/Packages
/dist/wily/main/binary-i386/Packages

It is then unable to locate package gstreamer0.10-ffmpeg

Any thoughts?I never did put up a package for 15.10 & 16.04 will not need it as clementine has moved to gstreamer1.0
Check here in several hours & there should be a package for 15.10 though you move to 16.04 next month or so.
[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)

---

### Post by manuel41 on 2016-05-30
> **mc4man said:**
> I never did put up a package for 15.10 & 16.04 will not need it as clementine has moved to gstreamer1.0 Check here in several hours & there should be a package for 15.10 though you move to 16.04 next month or so. [https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)    I'm facing the same issue, I'm on 16.04, installed Clementine 1.3.1 and playing m4a files results in   ```
Your GStreamer installation is missing a plug-in
``` could you ELI5 how to fix it?

---

### Post by mc4man on 2016-05-30
> **manuel41 said:**
> I'm facing the same issue, I'm on 16.04, installed Clementine 1.3.1 and playing m4a files results in   ```
Your GStreamer installation is missing a plug-in
``` could you ELI5 how to fix it?
clementine in 16.04 (1.2.3+git...) & likely your one now use gst-1.0 so install
gstreamer1.0-libav

---

### Post by Fawad_Raza on 2016-06-05
> **mc4man said:**
> clementine in 16.04 (1.2.3+git...) & likely your one now use gst-1.0 so install
gstreamer1.0-libav

Hi I did just that, already installed. 

In **Ubuntu 16.04** it still has same problem of:

```
[COLOR=#000000][FONT=&quot]Your GStreamer installation is missing a plug-in[/FONT][/COLOR]
```

Same problem with .pls URLs in 16.04. Audacious plays both fine, so it looks to me more of a Clementine issue than Ubuntu 16.04. 

So I'd rather not back-port/use old packages, lets see if Clementine catches up with Ubuntu 16.04. Example I have for URL:

[http://stereoscenic.com/pls/pill-hi-aac.pls](http://stereoscenic.com/pls/pill-hi-aac.pls)

Plays fine in Audacious, but not in Clementine. 

Anyway rant over, any help which would make Clementine behave in this regard is highly appreciated.

Regards

---

### Post by mc4man on 2016-06-05
> **Fawad_Raza said:**
> Hi I did just that, already installed. 

In **Ubuntu 16.04** it still has same problem of:

```
[COLOR=#000000][FONT=&quot]Your GStreamer installation is missing a plug-in[/FONT][/COLOR]
```

Same problem with .pls URLs in 16.04. Audacious plays both fine, so it looks to me more of a Clementine issue than Ubuntu 16.04. 

So I'd rather not back-port/use old packages, lets see if Clementine catches up with Ubuntu 16.04. Example I have for URL:

[http://stereoscenic.com/pls/pill-hi-aac.pls](http://stereoscenic.com/pls/pill-hi-aac.pls)

Plays fine in Audacious, but not in Clementine. 

Anyway rant over, any help which would make Clementine behave in this regard is highly appreciated.

Regards
Your .pls works fine here in clementine, for that type you need this package
gstreamer1.0-plugins-bad-faad

---

