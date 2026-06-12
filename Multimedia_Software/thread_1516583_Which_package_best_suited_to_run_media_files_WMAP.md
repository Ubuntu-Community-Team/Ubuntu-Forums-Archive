---
title: "Which package best suited to run media files WMAP?"
date: 2010-06-23
forum: Multimedia Software
---

### Post by rjbgbo on 2010-06-23
I have noticed that some videos in wmv, not running, despite having installed w32codecs and the package gstreamer0.10-pitfdll - that found the tip in - [http://ubuntuforums.org/archive/index.php/t-537065.html](http://ubuntuforums.org/archive/index.php/t-537065.html)

That both in Totem, and in vlc, but in gnome-mplayer (mplayer) wheel, and funny thing is that the polls did not indicate the run in mplayer.

It seems to be an impediment to the sound appears that file type.

```
rjbgbo@rjbgbo-desktop:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x9fbc668] main libvlc: Running VLC with the default interface. Use 'cvlc' to use VLC without interface.
[0xb6f01880] main decoder error: no suitable decoder module for fourcc `wmap'.
VLC probably does not support this sound or video format.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb6f01318] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 300 ms
[0xb6f01318] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
```

---

### Post by mc4man on 2010-06-24
You should be able to play wmv with wmap thru gstreamer apps - wmap was added to gstreamer in lucid. (at least as far as wmap audio.

If vid's won't play then I'd suggest adding the gstreamer-devs ppa - I currently have it and have no problem with wmv (vc1) with wmap audio playing in totem
(ppa is also excellent to use in karmic

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

As far as vlc - it will not decode wmap unless built off of a more current ffmpeg - no ubuntu and most all ppa are not.
 
Starting in maverick (10.10) vlc will support wmap (not yet but will 

Otherwise your best option is to build yourself and statically link a current ffmpeg build

mplayer will support wmap thru w32codecs or a self built or ppa version thru libavcodec (built-in support

---

