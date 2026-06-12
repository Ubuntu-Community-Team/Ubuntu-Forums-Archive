---
title: "hvec x265 playback, trusty 14.04"
date: 2016-03-05
forum: Multimedia Software
---

### Post by pqwoerituytrueiwoq on 2016-03-05
i am unable to get video (sound works) in smplayer and vlc just crashes
i have tested vlc in 16.04 and it works just fine, is there any way i can get it working in trusty?
i have tried some PPAs:
[http://ppa.launchpad.net/strukturag/libde265/ubuntu](http://ppa.launchpad.net/strukturag/libde265/ubuntu)
[http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu)
neither are able to play these files

i really don't feel like taking the time to upgrade yet, i would prefer procrastinate even after 16.04 is released (save it for say a 3 day weekend)

* i am by no means a expert in media codecs, i am not even good at figuring out what format they are

---

### Post by mc4man on 2016-03-06
You should be able to get hevc supporrt in 14.04. By default there is none as 14.04 uses libav9 which doesn't support.
To compare apples to apples here is a small hevc sample I encoded if you wish - 
[http://www.datafilehost.com/d/fbf63630](http://www.datafilehost.com/d/fbf63630)

For totem you need to add the strukturag ppa & install the gstreamer1.0-libde265 package (0.1.12-1ppa1~trusty1
For vlc the media ppa is ok though you'd need to install the vlc-plugin-libde265, (0.1.7-1ppa1~trusty1.1),  from the media ppa, not from the  strukturag (the media ppa plugin has been built for vlc 2.x
screens show both playing above file just fine in 14.04

Any mpv not from ubuntu repo (it's so old, worthless) will play any hevc file

The other alternative is to move 14.04 to libav11, then no plugins for either totem or vlc are needed as hevc support is supplied thru the  gstreamer1.0-libav plugin for totem & libavcodec56 for vlc.  [This ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6") does that though read page first

---

### Post by pqwoerituytrueiwoq on 2016-03-06
your sample works fine, vlc no longer crashes and acts just like smplayer on my files (they are mkv files does that matter?)
i will try that libav ppa, well i now get thumbnails for these files
well paraole works but it has a odd color overlay, no video in smplayer, and vlc locks up

i have tried playing them in a 16.04 virtualbox, works but the video and audio are not synced

---

### Post by mc4man on 2016-03-06
> **pqwoerituytrueiwoq said:**
> your sample works fine, vlc no longer crashes and acts just like smplayer on my files (they are mkv files does that matter?)
i will try that libav ppa, well i now get thumbnails for these files
well paraole works but it has a odd color overlay, no video in smplayer, and vlc locks up

i have tried playing them in a 16.04 virtualbox, works but the video and audio are not synced
Which backend is your smplayer using?

---

### Post by pqwoerituytrueiwoq on 2016-03-06
how do i check that?

---

### Post by mc4man on 2016-03-06
> **pqwoerituytrueiwoq said:**
> how do i check that?
See screen. (sort of, see below
Slightly off-topic
I (edit - will) copy the latest smplayer back to the media ppa or just use the rvm ppa
[https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)

For 14.04 there is no Ubuntu repo mplayer, so generally it sets up with mplayer2 which is dead & has been for some time
(- smplayer allows using mpv also though mpv isn't as suitable for smplayer as mplayer is though certainly can be used

mplayer2 uses the same binary name as mplayer so check in your package manager as to which is installed. If you are using mplayer2 I'd switch to mplayer which is in the trusty multimedia ppa (if using synaptic just mark mplayer for install & it will add mplayer & remove mplayer2
I just copied over a new mplayer build for trusty into the multimedia ppa, should be available in about a 1/2 hr. or so though the current package should handle hevc.

(- just curious - what Ubuntu are you using, ie. ubuntu/unity/compiz or something else? Edit: I should read better - Xubuntu I see

---

### Post by pqwoerituytrueiwoq on 2016-03-06
thanks installed mplayer and it works in smplayer :)
```
chad@Z97K1LLER:/media/chad/iso/Xenial$ apt-cache policy mplayer
mplayer:
  Installed: 2:1.1+svn37401~trusty1
  Candidate: 2:1.1+svn37401~trusty1
  Version table:
 *** 2:1.1+svn37401~trusty1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.1+dfsg1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

---

### Post by mc4man on 2016-03-06
Great, when or if you go to 16.04 you'll find the default 16.04 Ubuntu repos are in really good shape media wise
(- 16.04 uses ffmpeg & libav is gone, mplayer has been returned, ect, ect. 
Over time i'll populate [this ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media") for 16.04 but thankfully won't need as much or be as convoluted as life in 14.04 due to the return of FFmpeg & friends...

---

### Post by goofprog on 2016-03-06
try ffplay from ffmpeg

---

